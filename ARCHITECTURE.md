# YDigest — Sistem Mimarisi & İş Akışı

Bu belge, YDigest sisteminin veri akışını, temel modüllerini ve bileşenler arası ilişkilerini tanımlar.

---

## 1. Veri Akış Şeması (Pipeline)

```
[ RSS / Atom Kaynakları ]
           │
           ▼
   [ Ingestion Layer ]   <-- Asenkron HTTP Fetcher (HTTPX + Feedparser)
           │
           ▼
  [ Processing Layer ]   <-- Boilerplate & HTML Temizliği, Tekilleştirme
           │
           ▼
    [ AI / LLM Engine ]  <-- Yapılandırılmış Prompt & Model Çıkarımı
           │
           ▼
     [ Storage (DB) ]    <-- SQLite (WAL Modu)
           │
     ┌─────┴───────────────┐
     ▼                     ▼
[ Web UI (Dashboard) ]   [ Webhook / Delivery ]
```

---

## 2. Modül Sorumlulukları

### A. Ingestion (Veri Toplama)
- Tanımlanan kaynak listelerini periyodik olarak tarar.
- HTTP `ETag` ve `Last-Modified` başlıklarını kullanarak gereksiz bant genişliği tüketimini önler.
- Zaten işlenmiş URL ve içeriklerin hash kayıtlarını kontrol eder.

### B. Processing (İşleme & Temizleme)
- Sayfadaki reklam, navigasyon ve menü fazlalıklarını temizleyerek ham metni izole eder.
- Metin benzerlik algoritmalarıyla aynı haberi aktaran farklı kaynakları tek bir kayıt altında gruplar.

### C. AI / LLM Engine (Özetleme & Analiz)
- Yapılandırılmış şablonlar (Structured JSON Output) ile LLM API çağrısı yapar.
- Çıktı formatı:
  - Günün ana manşeti
  - Kategori bazlı özet maddeleri
  - Genel duygu ve önem skoru

### D. Delivery & Presentation (Dağıtım & Arayüz)
- **REST API:** Harici sistemlerin bültenleri sorgulayabilmesi ve manuel tetikleme yapabilmesi için uç noktalar.
- **Webhook Dispatcher:** Tamamlanan bültenleri harici servislere veya bot altyapılarına otomatik iletme.
- **Web UI:** Ekstra build adımı gerektirmeyen, doğrudan sunulan hafif HTML/CSS/JS arayüzü.
