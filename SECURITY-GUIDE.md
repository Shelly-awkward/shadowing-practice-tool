# 🔒 API Key 安全指南

## ❌ 危險做法

### 1. 直接寫在程式碼中（即使是 Private Repository）

```javascript
// ❌ 危險！不要這樣做
const API_KEY = "sk-1234567890abcdef";  // 永遠留在 Git 歷史中
```

**風險**：
- Git 歷史永久保存
- 未來可能變成公開
- 協作者都能看到
- 如果分享程式碼就外洩

---

## ✅ 安全做法

### 方案 1: 使用 localStorage（已實作在 index-secure.html）

**優點**：
- ✅ API Key 只存在用戶瀏覽器
- ✅ 程式碼可以公開在 GitHub
- ✅ 每個用戶使用自己的 Key
- ✅ 不會被 commit 到 Git

**如何使用**：
```javascript
// 儲存（只在用戶瀏覽器）
localStorage.setItem('api_key', userInputKey);

// 讀取
const apiKey = localStorage.getItem('api_key');

// 使用
fetch('https://api.openai.com/...', {
    headers: { 'Authorization': `Bearer ${apiKey}` }
});
```

---

### 方案 2: 環境變數（需要後端）

如果你要部署到伺服器（非純前端）：

#### 2.1 使用 `.env` 檔案

```bash
# .env 檔案（加入 .gitignore）
OPENAI_API_KEY=sk-your-key-here
ASSEMBLYAI_API_KEY=your-key-here
```

```javascript
// 後端程式碼
require('dotenv').config();
const apiKey = process.env.OPENAI_API_KEY;
```

#### 2.2 在 Vercel/Netlify 設定環境變數

1. 前往專案設定
2. 找到 "Environment Variables"
3. 新增變數：
   - Name: `OPENAI_API_KEY`
   - Value: `sk-...`

---

### 方案 3: Serverless Functions

創建一個 API 端點來隱藏真實的 API Key：

```javascript
// api/transcribe.js (Vercel Serverless Function)
export default async function handler(req, res) {
    const apiKey = process.env.OPENAI_API_KEY;  // 從環境變數讀取
    
    // 轉發請求到 OpenAI
    const response = await fetch('https://api.openai.com/...', {
        headers: {
            'Authorization': `Bearer ${apiKey}`
        },
        body: req.body
    });
    
    const data = await response.json();
    res.json(data);
}
```

前端改為呼叫你的 API：
```javascript
// 前端不需要 API Key
fetch('/api/transcribe', {
    method: 'POST',
    body: audioFile
});
```

---

## 🚨 如果 API Key 已經 commit 到 Git

### 緊急處理步驟：

#### 1. 立即撤銷 API Key
- OpenAI: https://platform.openai.com/api-keys → 刪除舊 Key
- AssemblyAI: Dashboard → 重新生成 Key

#### 2. 從 Git 歷史中移除（困難）

```bash
# 警告：這會改寫 Git 歷史！
git filter-branch --force --index-filter \
  "git rm --cached --ignore-unmatch index.html" \
  --prune-empty --tag-name-filter cat -- --all

# 強制推送
git push origin --force --all
```

**注意**：
- 這只適用於你是唯一開發者的情況
- 如果有協作者，他們本地仍有舊歷史
- 最好的方法還是撤銷 Key 並創建新的

#### 3. 使用 BFG Repo-Cleaner（更簡單）

```bash
# 下載 BFG
# https://rtyley.github.io/bfg-repo-cleaner/

# 移除包含 API Key 的檔案
bfg --delete-files index.html

# 清理
git reflog expire --expire=now --all
git gc --prune=now --aggressive
```

---

## 📋 檢查清單

上傳到 GitHub 前：

- [ ] 確認沒有 API Key 在程式碼中
- [ ] `.gitignore` 包含 `.env`, `config.js`, `secrets.js`
- [ ] 使用 localStorage 或環境變數
- [ ] 測試程式碼可以在沒有 Key 的情況下運行
- [ ] 檢查 Git 歷史：`git log -p | grep -i "api"`

---

## 🎯 推薦方案總結

| 方案 | 適用情境 | 安全性 | 難度 |
|------|---------|--------|------|
| **localStorage** | 純前端應用 | ⭐⭐⭐ | ⭐ |
| **環境變數** | 有後端的應用 | ⭐⭐⭐⭐ | ⭐⭐ |
| **Serverless** | 需要隱藏 Key | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ |

**對於你的 Shadowing 工具**：
- ✅ 使用 `index-secure.html`（已實作 localStorage）
- ✅ 可以放心上傳到 GitHub（即使是 Public）
- ✅ 每個用戶輸入自己的 API Key
- ✅ Key 只存在用戶的瀏覽器，不會外洩

---

## 🔍 驗證安全性

```bash
# 檢查程式碼中是否有 API Key
grep -r "sk-" .
grep -r "api.key" .

# 檢查 Git 歷史
git log -p | grep -i "api"
git log -p | grep "sk-"
```

如果找到任何結果 → 立即撤銷該 Key！

---

## 💡 最佳實踐

1. **永遠不要** commit API Key
2. **使用** `.gitignore` 保護敏感檔案
3. **定期更換** API Key
4. **監控** API 用量（防止被盜用）
5. **設定** 用量限制和警報

---

**記住**：一旦 commit 到 Git，就很難完全刪除。預防勝於治療！🛡️
