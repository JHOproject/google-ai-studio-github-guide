# Google AI Studio × GitHub Pages 自動部署指南

這個 Repository 提供一份繁體中文教學，說明如何把適合靜態部署的 Google AI Studio App 連接至 GitHub，透過 GitHub Actions 建立 CI/CD，並發布到 GitHub Pages。

## 完整教學

請前往：[Google AI Studio × GitHub Pages 上線指南](https://jhoproject.github.io/google-ai-studio-github-guide/)

網頁版包含可直接貼入 Google AI Studio 的 Prompt、GitHub Pages 設定步驟、常見問題與完整注意事項。

## 流程摘要

首次設定只需要完成一次：

1. 在 Google AI Studio 將 App 連接至 GitHub Repository。
2. 透過 AI Studio Prompt 檢查 App 是否適合 GitHub Pages，並建立 `.github/workflows/deploy-pages.yml`。
3. 將 workflow 與 App 程式碼 Push 到 GitHub 的 `main` branch。
4. 在 GitHub Repository 進入 **Settings → Pages**，將 Source 設為 **GitHub Actions**。
5. 等待首次 GitHub Actions workflow 完成，取得 GitHub Pages 網址。

完成初始設定後，每次更新只需要：

1. 在 Google AI Studio 使用 Prompt 修改 App。
2. 確認預覽與主要功能正常。
3. 使用 **Push changes** 或 **Publish to GitHub** 將新 commit 推送到 `main`。
4. GitHub Actions 會自動建置並更新 GitHub Pages。

## 重要限制

- GitHub Pages 只能託管靜態網站，不能執行 Node.js 後端或其他伺服器端程式。
- 不要把 API Key、密碼、Token 或其他機密寫入 Repository 或前端程式碼。
- AI Studio Secrets 不會自動提供給 GitHub Pages。
- 如果 App 需要後端、資料庫、登入或伺服器端 Gemini API，應使用 Cloud Run、Firebase 或其他安全的後端服務。
- 真正觸發這套 CI/CD 的是新 commit 進入 GitHub 的 `main`；AI Studio 的 **Publish App** 是 Cloud Run 部署流程，兩者不同。

## Repository 內容

- `index.html`：完整網頁版教學。
- `media/`：教學使用的示意圖片。
- `.github/workflows/pages.yml`：本 Repository 本身的 GitHub Pages CI/CD workflow。
- `.nojekyll`：停用 GitHub Pages 的預設 Jekyll 處理。

## 官方參考

- [Google AI Studio — Build apps](https://ai.google.dev/gemini-api/docs/aistudio-build-mode)
- [GitHub Pages — Configuring a publishing source](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)
- [GitHub Pages — Using custom workflows](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages)
