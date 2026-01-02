# 📤 上傳到 GitHub 指南

## 方法 1: 使用 GitHub 網頁介面（最簡單）

### 步驟 1: 創建新 Repository

1. 登入 [GitHub](https://github.com)
2. 點擊右上角的 `+` → `New repository`
3. 填寫資訊：
   - Repository name: `shadowing-practice-tool`（或你喜歡的名字）
   - Description: `A language learning tool for shadowing practice with auto-transcription`
   - 選擇 `Public`（公開）或 `Private`（私密）
   - ✅ 勾選 `Add a README file`
   - 選擇 License: `MIT License`
4. 點擊 `Create repository`

### 步驟 2: 上傳檔案

1. 在新建的 repository 頁面，點擊 `Add file` → `Upload files`
2. 將以下檔案拖曳到網頁：
   - `index.html`
   - `README.md`（如果之前沒勾選自動生成）
   - `.gitignore`
   - `examples/API-SETUP.md`
3. 在下方填寫 Commit message：`Initial commit: Add shadowing practice tool`
4. 點擊 `Commit changes`

### 步驟 3: 啟用 GitHub Pages（可選）

1. 前往 `Settings` → `Pages`
2. 在 `Source` 選擇 `main` 分支
3. 點擊 `Save`
4. 等待幾分鐘後，你的網站會發布到：
   `https://你的使用者名稱.github.io/shadowing-practice-tool/`

---

## 方法 2: 使用 Git 命令列

### 前置準備

確保已安裝 Git：
```bash
git --version
```

如果沒有，請從 [git-scm.com](https://git-scm.com/) 下載安裝。

### 步驟 1: 在 GitHub 創建新 Repository

（同方法 1 的步驟 1，但不要上傳任何檔案）

### 步驟 2: 初始化本地 Git Repository

在專案資料夾中開啟終端機/命令提示字元：

```bash
# 進入專案目錄
cd shadowing-practice-app

# 初始化 Git
git init

# 新增所有檔案
git add .

# 建立第一個 commit
git commit -m "Initial commit: Add shadowing practice tool"

# 設定主分支名稱
git branch -M main

# 連接到 GitHub（替換成你的 repository URL）
git remote add origin https://github.com/你的使用者名稱/shadowing-practice-tool.git

# 推送到 GitHub
git push -u origin main
```

### 步驟 3: 啟用 GitHub Pages

（同方法 1 的步驟 3）

---

## 方法 3: 使用 GitHub Desktop（推薦新手）

### 步驟 1: 安裝 GitHub Desktop

從 [desktop.github.com](https://desktop.github.com/) 下載並安裝

### 步驟 2: 創建 Repository

1. 開啟 GitHub Desktop
2. 點擊 `File` → `New repository`
3. 填寫：
   - Name: `shadowing-practice-tool`
   - Local path: 選擇專案資料夾的上層目錄
   - ✅ Initialize with README
   - Git ignore: `None`
   - License: `MIT`
4. 點擊 `Create repository`

### 步驟 3: 複製檔案並推送

1. 將所有專案檔案複製到新建的 repository 資料夾
2. 在 GitHub Desktop 中會看到所有變更
3. 在下方填寫 Commit message：`Initial commit`
4. 點擊 `Commit to main`
5. 點擊 `Publish repository`
6. 選擇是否保持私密，然後點擊 `Publish repository`

---

## ⚠️ 上傳前檢查清單

在上傳到 GitHub 前，請確認：

- [ ] 已移除所有 API Keys（檢查 index.html 中沒有硬編碼的 key）
- [ ] `.gitignore` 檔案已正確設定
- [ ] README.md 內容完整且正確
- [ ] 檔案結構清晰易懂
- [ ] 所有範例程式碼可以正常運作

---

## 📝 後續維護

### 更新檔案

**使用網頁介面**：
1. 找到要修改的檔案
2. 點擊 `編輯` 圖示（鉛筆）
3. 修改後點擊 `Commit changes`

**使用 Git 命令列**：
```bash
# 修改檔案後
git add .
git commit -m "描述你的更改"
git push
```

**使用 GitHub Desktop**：
1. 修改檔案
2. 在 GitHub Desktop 中查看變更
3. 填寫 Commit message
4. 點擊 `Commit` 然後 `Push origin`

---

## 🌟 推薦的 Repository 設定

### 添加主題標籤（Topics）

在 repository 頁面點擊設定圖示，添加：
- `language-learning`
- `shadowing`
- `transcription`
- `education`
- `javascript`

### 添加描述

在 repository 頁面添加簡短描述：
```
🎧 A web-based shadowing practice tool with automatic transcription for language learners
```

### 設定 About

填寫：
- Website: GitHub Pages URL（如果有啟用）
- Topics: 上述標籤

---

## 🎉 完成！

你的專案現在已經在 GitHub 上了！

- 分享你的 repository URL 給朋友
- 如果啟用了 GitHub Pages，也可以分享網站 URL
- 鼓勵其他人 Star ⭐ 你的專案

---

需要幫助？查看 [GitHub 官方文件](https://docs.github.com/) 或在專案中開 Issue！
