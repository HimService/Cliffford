# Cliffford Discord Bot

[繁體中文](README.md) | [English](README_EN.md)

# Cliffford Discord Bot

## 簡介
Cliffford Discord Bot 是一個基於 Python 3.11 開發的 Discord 機器人，利用 Google Gemini API 提供AI回應功能，包括文字聊天和圖片分析。機器人支援斜線指令（`/reset`、`/set`、`/unset`）來管理其行為，並通過 `console_rules.json` 檔案實現實時規則檢查，確保回應符合規範。

機器人功能包括：
- 通過文字和圖片與用戶互動（使用 Gemini API）。
- 設定特定的回應頻道（`/set` 和 `/unset`）。
- 重置機器人聊天狀態（`/reset`）。
- 實時檢查規則，避免違反 `console_rules.json` 中的規定。
- 將所有控制台輸出記錄到 `bot.log` 檔案。

## 需求
- Python 3.11 或 3.12（建議使用 3.11）
- Discord Bot Token x1
- Google Gemini API Key x1
Discord Bot Token與Gemini API Key這兩個是最基礎且最需要的。

## 安裝

### 1. 下載專案

### 2. 前往專案資料夾
```bash
cd Cliffford
```

### 3. 安裝依賴
安裝必要的套件：
```bash
pip install -r requirements.txt
```

### 4. 配置設定
- 配置 `setting.py` 檔案，填入內容：
  ```python
  BOT_TOKEN = "你的_Discord_Bot_Token"
  GEMINI_API_KEY = "你的_Gemini_API_Key"
  BOT_NAME = "Cliffford"  # ai自稱
  BOT_VERSION = "Beta.v0.a1"  # 版本(看你要不要動)
  developer = "你的名字"  # 機器人擁有者的名字
  developer_id = "你的Discord ID" # 開發者/擁有者Discord ID
  DEFAULT_CHANNEL = "頻道 ID"  # 可填可不填，不填在哪個頻道說話他都會回你,除非你有使用/set
  ```

- 配置 `main.py` 檔案，填入內容：
  ```
  genai.configure(api_key=GEMINI_API_KEY)
  text_model = genai.GenerativeModel('填入你所使用的Gemini模型名稱')
  vision_model = genai.GenerativeModel('填入你所使用的Gemini模型名稱')
  ```

### 5. 編輯規則檔案
- 編輯 `bot_rules.json`（用於 AI跟人交談時的基礎規則）：
  ```json
  [
    {
      "role": "user",
      "parts": "[規則]請使用中文回應所有訊息"
    },
    {
      "role": "model",
      "parts": "[回應規則]我會使用中文回應所有訊息"
    }
  ]
  ```
- 編輯 `console_rules.json`（用於實時規則）：
  ```json
  [
    {
      "rule": "避免使用粗魯或冒犯性語言",
      "action": "請使用友善的語言，否則我無法回應"
    }
  ]
  ```

## 使用方法

## 啟動機器人
在專案資料夾中運行：
```bash
python main.py
```

## 機器人於Discord 互動
- **文字聊天**：在 Discord 中直接發送文字訊息，機器人會以回覆形式回應。
- **圖片分析**：上傳圖片並（可選）添加文字描述，機器人會分析圖片並回應。
- **斜線指令**：
  - `/reset`：重置記憶。
  - `/set #channel`：設定機器人只在指定頻道回應。
  - `/unset`：取消頻道設定，讓機器人在所有頻道進行回應。

## 控制台互動
- 啟動後，控制台會提示「在控制台輸入問題（輸入 'exit' 退出）」，你可以在控制台輸入問題讓機器人回應。

## 日誌記錄
- 所有控制台輸出會同時記錄到 `bot.log` 檔案，格式為：
  ```
  日期 時間 - INFO - 用戶輸入：用戶問的問題
  日期 時間 - INFO - 機器人正在對照實時規則
  日期 時間 - INFO - 機器人回應：機器人的回應
  ```

## 詳細配置說明

### `setting.py`
- `BOT_TOKEN`：請從 Discord Developer Portal 獲取的 Bot Token。
- `GEMINI_API_KEY`：從 Google Cloud Console 獲取對應的 Gemini API Key。
- `bot_name`：機器人的名稱(ai的自稱)。
- `bot_version`：機器人的版本號(可以不用動)。
- `developer`：機器人的擁有者。
- `DEFAULT_CHANNEL`：可選的預設回應頻道 ID（留空為沒有設定）。

### `console_rules.json`
- 定義實時規則，格式為：
  ```json
  [
    {
      "rule": "規則描述",
      "action": "違反時的回應"
    }
  ]
  ```
- 規則會在每次處理訊息時實時檢查。

## 常見問題

### 1. Gemini API 錯誤
- 確認 `GEMINI_API_KEY` 有效，並檢查模型名稱（例如 `gemini-2.0-flash`）是否有填寫正確。
- 確保 API Key 有權限使用指定的 Gemini 模型,且還有請求額度。


## 貢獻
如果您有新的功能建議或發現 Bug，請聯繫。
## 許可
請閱讀 `LICENSE` 文件。
