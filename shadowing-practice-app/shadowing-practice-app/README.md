# 🎧 Shadowing Practice Tool

一個專為語言學習者設計的跟讀練習工具，支援自動產生逐字稿、速度調整和循環播放功能。

## ✨ 功能特色

- 📝 **多種逐字稿來源**
  - 手動輸入逐字稿
  - 使用 OpenAI Whisper API 自動產生
  - 使用 AssemblyAI 自動轉錄
  - 從 YouTube 提取字幕

- 🎵 **靈活的播放控制**
  - 播放速度調整（0.5x - 2.0x）
  - 循環播放特定段落（5秒、10秒、15秒、30秒或自訂）
  - 鍵盤快捷鍵控制

- 🎯 **專為 Shadowing 設計**
  - 清晰的逐字稿顯示
  - 段落分行方便跟讀
  - 響應式設計，支援手機和電腦

## 🚀 快速開始

### 線上使用

1. 下載 `index.html` 檔案
2. 在瀏覽器中開啟
3. 開始使用！

### 使用 API 自動產生逐字稿

#### 選項 1: OpenAI Whisper API

1. 前往 [OpenAI Platform](https://platform.openai.com/) 註冊帳號
2. 取得 API Key
3. 在工具中輸入 API Key
4. 上傳音訊檔案即可自動產生逐字稿

**費用**: 約 $0.006/分鐘

#### 選項 2: AssemblyAI（推薦）

1. 前往 [AssemblyAI](https://www.assemblyai.com/) 註冊免費帳號
2. 取得 API Key
3. 使用提供的 Python 腳本或直接在網頁中使用

**優點**: 
- 免費額度充足
- 可直接整合 Claude AI
- 轉錄準確度高

## 📖 使用說明

### 基本流程

1. **載入音訊**
   - 貼上音訊 URL（如 podcast 的 MP3 連結）
   - 或上傳本地音訊檔案

2. **準備逐字稿**
   - **手動輸入**：直接貼上已有的逐字稿
   - **自動產生**：使用 Whisper 或 AssemblyAI API
   - **YouTube**：從 YouTube 影片提取字幕

3. **開始練習**
   - 點擊「開始練習」
   - 調整播放速度（建議初學者從 0.7x 開始）
   - 設定循環播放區間來反覆練習困難段落

### 鍵盤快捷鍵

- **空白鍵**: 播放/暫停
- **← 左箭頭**: 後退 5 秒
- **→ 右箭頭**: 前進 5 秒

## 🔒 API 金鑰安全

**重要提醒**：
- ⚠️ 請勿將 API 金鑰提交到 GitHub
- ⚠️ 使用完畢後可在瀏覽器中清除
- ⚠️ API 金鑰僅儲存在瀏覽器的本地記憶體中
- ⚠️ 建議使用環境變數或配置檔案管理 API 金鑰

## 🛠️ 技術架構

- 純前端應用（HTML + CSS + JavaScript）
- 無需伺服器部署
- 支援的音訊格式：MP3, M4A, WAV, OGG 等
- API 整合：OpenAI Whisper、AssemblyAI

## 📦 檔案結構

```
shadowing-practice-app/
├── index.html              # 主要應用程式
├── README.md              # 說明文件
├── .gitignore            # Git 忽略檔案
└── examples/             # 範例檔案
    └── sample-config.md  # API 設定範例
```

## 🌐 部署到 GitHub Pages

1. Fork 或 Clone 此專案
2. 前往 GitHub 專案設定
3. 在 Pages 設定中選擇 `main` 分支
4. 網站會自動部署到 `https://你的使用者名稱.github.io/專案名稱/`

## 💡 使用範例

### 適合的學習材料

- 📻 Podcast（如：Brains On, NPR, BBC）
- 🎬 YouTube 影片（教學、演講、訪談）
- 🎓 線上課程音訊
- 📚 有聲書

### 建議的練習方法

1. **第一遍**：正常速度聆聽，理解內容
2. **第二遍**：降速到 0.7x，跟著逐字稿跟讀
3. **第三遍**：提升到 0.9x，不看逐字稿練習
4. **最後**：正常速度，完全跟讀

## 🤝 貢獻

歡迎提交 Issue 和 Pull Request！

## 📄 授權

MIT License

## 🙏 致謝

- OpenAI Whisper API
- AssemblyAI
- Anthropic Claude（用於開發協助）

## 📧 聯絡方式

如有問題或建議，歡迎開 Issue 討論！

---

**祝你學習愉快！🎉**
