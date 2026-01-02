# API 設定範例

## OpenAI Whisper API

### 取得 API Key

1. 前往 [OpenAI Platform](https://platform.openai.com/)
2. 註冊或登入帳號
3. 點擊右上角的個人頭像 → "View API keys"
4. 點擊 "Create new secret key"
5. 複製並安全儲存你的 API Key

### 使用方式

在應用程式的「自動產生」分頁中：
1. 貼上你的 API Key
2. 上傳音訊檔案
3. 點擊「使用 Whisper 產生逐字稿」

### 費用

- Whisper API: $0.006 / 分鐘
- 例如：30 分鐘的 podcast = $0.18 美元

### 注意事項

⚠️ **重要**：
- 請勿將 API Key 公開或提交到 Git
- 使用後建議從瀏覽器中清除
- API Key 只儲存在你的瀏覽器本地

---

## AssemblyAI（推薦）

### 取得 API Key

1. 前往 [AssemblyAI](https://www.assemblyai.com/)
2. 註冊免費帳號
3. 在 Dashboard 中找到你的 API Key

### 優點

- 免費額度充足
- 轉錄品質優秀
- 支援多語言
- 可直接整合 Claude AI 做後續處理

### Python 使用範例

```python
import assemblyai as aai

# 設定 API Key
aai.settings.api_key = "YOUR_API_KEY"

# 轉錄音訊
transcriber = aai.Transcriber()
transcript = transcriber.transcribe("podcast.mp3")

# 取得逐字稿
print(transcript.text)

# 儲存到檔案
with open("transcript.txt", "w") as f:
    f.write(transcript.text)
```

---

## 從 YouTube 提取字幕

### 方法 1: YouTube 內建功能

1. 開啟 YouTube 影片
2. 點擊影片下方的「...」(更多)
3. 選擇「顯示完整記錄」
4. 複製字幕文字
5. 貼到 Shadowing 工具的「手動輸入」分頁

### 方法 2: 使用線上工具

推薦工具：
- [DownSub](https://downsub.com/) - 免費下載字幕
- [YouTube Transcript](https://youtubetranscript.com/) - 直接取得文字稿

---

## 安全建議

### 本地開發

如果你想在本地開發並使用環境變數：

1. 創建 `.env` 檔案（已在 .gitignore 中）
```
OPENAI_API_KEY=sk-...
ASSEMBLYAI_API_KEY=...
```

2. 使用環境變數讀取（需要後端支援）

### 生產環境

對於公開部署：
- 考慮使用後端 API 來隱藏金鑰
- 或使用 Serverless Functions（如 Vercel, Netlify Functions）
- 實作 API 金鑰管理和用量限制

---

## 常見問題

### Q: API Key 會被儲存在哪裡？
A: 目前的實作中，API Key 僅在使用時暫時儲存在瀏覽器記憶體中，不會永久儲存。

### Q: 如何保護我的 API Key？
A: 
1. 不要將 API Key 提交到 GitHub
2. 使用完畢後清除瀏覽器快取
3. 定期更換 API Key
4. 設定 API 用量限制

### Q: 轉錄需要多久時間？
A: 通常音訊長度的 10-30% 時間。例如 10 分鐘音訊約需 1-3 分鐘處理。

### Q: 支援哪些語言？
A: 
- Whisper: 支援 99 種語言
- AssemblyAI: 主要支援英文，部分支援其他語言

---

**需要協助？歡迎在 GitHub 開 Issue！**
