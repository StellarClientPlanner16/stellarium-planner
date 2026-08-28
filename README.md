# 🚀 High-Performance Async Telegram Media Downloader Bot

An enterprise-grade, asynchronous Telegram Media Downloader Bot built with **Python 3.11+**, **`python-telegram-bot` (v20+)**, **`yt-dlp`**, and **`FFmpeg`**. Fully containerized via **Docker** and pre-configured for seamless zero-downtime deployment on **Railway.app**.

---

## 🛠 Features & Architecture Highlights

- **Asynchronous & Non-Blocking Architecture:** Engine built on Python's `asyncio` loop to handle high-concurrency requests smoothly.
- **Robust Media Extraction:** Leverages `yt-dlp` to extract media from hundreds of platforms (YouTube, Twitter/X, Instagram, TikTok, etc.) with automatic format fallback.
- **On-the-Fly Audio & Video Processing:** Seamless integration with `FFmpeg` for remuxing, encoding, audio extraction, and dynamic thumbnail generation.
- **Resource Protection & Throttling:** Built-in `asyncio.Semaphore` limiters to protect CPU/RAM from spike usage during heavy media tasks.
- **Automated Lifecycle & Storage Management:** Strict cleanup hooks automatically purge temporary downloaded segments and converted media files post-transmission to prevent disk exhaustion.
- **Lightweight Database Layer:** Uses optimized `sqlite3` for user tracking, execution logs, and configuration state storage.
- **Production Ready Containerization:** Optimized Multi-stage `Dockerfile` with minimal footprint, caching layers, and environment readiness.

---

## 🏗 System Architecture

```
[ Telegram Client ] ──> ( Telegram Bot API )
                              │
                              ▼
                [ Async Telegram Bot (ptb) ]
                              │
                  ├── User & State Layer (sqlite3)
                  ├── Task Queue & Semaphore Throttling
                  │
                  ▼
                [ Media Engine Handler ]
               /                        \
       ( yt-dlp Extractor )      ( FFmpeg Engine )
              │                         │
              └──────► [ Temp Storage ] ◄┘
                              │
                      ( Auto Cleanup )
```

---

## 📦 Directory Structure

```
.
├── bot/
│   ├── __init__.py
│   ├── main.py              # Application entrypoint & bot initialization
│   ├── handlers/            # Telegram command & message route handlers
│   ├── services/            # yt-dlp & FFmpeg execution abstractions
│   └── database/            # SQLite connection, schema, & query helpers
├── temp/                    # Dynamic scratch directory for active downloads
├── Dockerfile               # Production multi-stage Docker configuration
├── docker-compose.yml       # Local development & container orchestration
├── requirements.txt         # Core dependencies with pinned versions
├── .env.example             # Environment variable blueprint
└── README.md                # Technical documentation
```

---

## ⚙️ Environment Variables

Create a `.env` file in the root directory based on `.env.example`:

| Variable | Description | Required | Default |
| :--- | :--- | :---: | :---: |
| `BOT_TOKEN` | Telegram Bot API Token from [@BotFather](https://t.me/BotFather) | **Yes** | - |
| `MAX_CONCURRENT_DOWNLOADS` | Max simultaneous download tasks before queueing | No | `5` |
| `MAX_FILE_SIZE_MB` | Upper limit for file downloads (Telegram limit ~2000MB) | No | `2000` |
| `TEMP_DOWNLOAD_DIR` | Directory for temporary media caching | No | `./temp` |
| `DATABASE_PATH` | Path to SQLite database file | No | `./data/bot.db` |

---

## 🚀 Quick Start (Local Development)

### Prerequisites

- **Python 3.11+**
- **FFmpeg** installed and added to PATH (`ffmpeg -version`)
- **Git**

### 1. Clone & Setup Virtual Environment

```bash
git clone https://github.com/your-username/telegram-downloader-bot.git
cd telegram-downloader-bot

python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 2. Install Dependencies

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### 3. Run the Bot

```bash
cp .env.example .env
# Edit .env and supply your BOT_TOKEN

python -m bot.main
```

---

## 🐳 Docker Deployment

### Local Docker Build & Run

```bash
# Build Docker image
docker build -t telegram-downloader-bot .

# Run container
docker run -d \
  --name tg_downloader \
  --env-file .env \
  -v $(pwd)/data:/app/data \
  telegram-downloader-bot
```

### Using Docker Compose

```bash
docker-compose up -d --build
```

---

## 🚂 Railway.app Deployment Guide

This project is tailored for **Railway.app** zero-config deployment via Dockerfile.

1. **Fork/Push** this repository to your GitHub account.
2. Log in to [Railway.app](https://railway.app) and create a **New Project**.
3. Select **Deploy from GitHub repo** and connect your repository.
4. Go to the **Variables** tab in your Railway deployment dashboard and define:
   - `BOT_TOKEN`: `<your_telegram_bot_token>`
   - `MAX_CONCURRENT_DOWNLOADS`: `5`
5. Railway will automatically detect the `Dockerfile`, build the container, and start your bot instance.
6. (Optional) Attach a Railway Persistent Volume mounted to `/app/data` to retain SQLite state across deployments.

---

## ⚡ Performance Optimization & Safety

- **Memory Safety:** Processing large files is isolated to async worker queues to avoid RAM saturation.
- **Storage Sweeper:** Post-transmission cleanup runs inside a `finally` block to guarantee temp file removal even if user cancels or execution fails.
- **FFmpeg Hardware Acceleration:** If deployed on environments with GPU passthrough, update the FFmpeg flags in `services/ffmpeg.py` to enable hardware-accelerated transcoding (`h264_nvenc` / `vaapi`).

---

## 📜 License

Distributed under the **MIT License**. See `LICENSE` for details.
