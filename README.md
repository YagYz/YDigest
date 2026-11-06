# YDigest — AI-Powered News & Content Digest Engine

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python 3.10+](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)](https://www.python.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.115+-009688?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?logo=docker&logoColor=white)](docker-compose.yml)

**YDigest**, modern haber kaynakları, RSS/Atom beslemeleri ve web içerikleri için geliştirilmiş; asenkron veri toplama, içerik tekilleştirme, yapay zeka destekli özetleme ve çok kanallı bildirim/dağıtım altyapısı sunan açık kaynaklı bir bülten motorudur.

---

## 🚀 Temel Özellikler

- **Çoklu Kaynak Desteği:** RSS, Atom ve özel haber akışlarından asenkron içerik toplama.
- **Akıllı Metin Çıkarma & Tekilleştirme:** Reklam ve boilerplate temizliği, benzer haberleri otomatik kümeleme.
- **Yapay Zeka Destekli Analiz:** LLM (Google Gemini Flash / yerel modeller) ile yapılandırılmış kategorik özet ve manşet çıkarımı.
- **Hafif & Hızlı Mimari:** Düşük donanımlı sistemlerde bile minimal bellek ayak iziyle çalışma.
- **Modern Web Arayüzü:** Ekstra derleme adımı gerektirmeyen hafif, modern ve responsive dashboard.
- **Entegrasyon & Webhook:** REST API, webhook ve harici bot sistemlerine anlık veri aktarımı.

---

## 🛠 Mimari & Teknoloji Yığını

- **Backend:** Python (FastAPI, Asyncio, Pydantic)
- **Veri Toplama & İşleme:** HTTPX, Feedparser, Trafilatura
- **Veritabanı:** SQLite (WAL modu)
- **Frontend:** Vanilla HTML5, CSS3, Modern JavaScript
- **Dağıtım:** Docker, Docker Compose

---

## 📦 Kurulum & Çalıştırma

### Gereksinimler
- Python 3.10+
- Git

### Yerel Kurulum

```bash
git clone https://github.com/YagYz/YDigest.git
cd YDigest

# Sanal ortam oluşturma
python3 -m venv .venv
source .venv/bin/activate

# Bağımlılıkları yükleme
pip install -r requirements.txt

# Ortam değişkenlerini ayarlama
cp .env.example .env

# Uygulamayı başlatma
uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload
```

---

## 📄 Lisans

Bu proje [MIT](LICENSE) lisansı altında sunulmaktadır.
