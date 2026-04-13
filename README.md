# 🚗 Private Bridge

**Private Bridge**, fiziksel dünyadaki etkileşimlerde kişisel veri gizliliğini korumak amacıyla geliştirilmiş, karekod (QR) tabanlı güvenli bir iletişim yönlendirme sistemidir.

## 🌟 Öne Çıkan Özellikler
- **Gizlilik Odaklı:** Araç sahipleri ve ziyaretçiler telefon numaralarını paylaşmadan iletişim kurabilir.
- **Akıllı Yönlendirme:** Gelen mesajlar veritabanındaki aktif oturumlar üzerinden otomatik olarak doğru tarafa iletilir.
- **Hibrit Altyapı:** Meta WhatsApp Business API ve Green API entegrasyonu ile kesintisiz veri akışı sağlar.
- **Oturum Yönetimi:** 15 dakikalık "Açık Kapı" (Stateful Session) mantığı ile doğal bir chat deneyimi sunar.

## 🛠️ Teknik Mimari
Sistem, Python (FastAPI) altyapısı üzerinde çalışır ve verileri SQLite üzerinde yönetir.

### Mesaj Akış Diyagramı
1. **Ziyaretçi:** Aracın üzerindeki QR kodu taratır.
2. **Sistem:** QR ID ile eşleşen araç sahibini bulur ve ziyaretçinin numarasını (`wa_id`) veritabanına "aktif oturum" olarak kaydeder.
3. **Araç Sahibi:** Bildirimi alır. 15 dakika içinde bota yazdığı herhangi bir cevap, sistem tarafından otomatik olarak ziyaretçiye iletilir.

### Veritabanı Şeması
- `qr_codes`: QR ID, Araç Sahibi Telefonu, Plaka Bilgisi.
- `chat_sessions`: QR ID, Son Ziyaretçi Telefonu, Son Etkileşim Zamanı (`updated_at`).

## 🚀 Kurulum ve Çalıştırma
```bash
# Gereksinimleri yükle
pip install fastapi uvicorn sqlite3 requests

# Sistemi başlat
uvicorn main:app --host 0.0.0.0 --port 8000

🔒 Güvenlik ve Gizlilik
Bu proje, Meta İşletme İlkeleri (Meta Business Policies) ile tam uyumludur. Kullanıcı verileri üçüncü taraflarla paylaşılmaz ve sadece iletişim oturumu süresince işlenir.

📧 İletişim
Destek ve bilgi için: support@privatebridge.com
