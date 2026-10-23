# Ödev Takip

Öğretmenler için sınıf, öğrenci ve ödev takibini tek bir HTML sayfasında toplayan, kurulum gerektirmeyen bir uygulama. Ödevi yapmayan veya getirmeyen öğrencilerin listesi tek tıkla WhatsApp'a yapıştırılacak bir mesaja dönüşür.

## Özellikler

### 1. Sınıflar ve Öğrenciler
- Sınıf ekleme ve silme
- Seçilen sınıfa öğrenci ekleme ve silme
- Toplu öğrenci ekleme (her satıra bir isim)
- Sınıf başına öğrenci sayısı gösterimi

### 2. Ödev Ekle
- Sınıf seçerek ödev ekleme (başlık, veriliş tarihi, isteğe bağlı açıklama)
- Seçilen sınıfa verilmiş ödevlerin tarihe göre listelenmesi
- Ödev silme

### 3. Ödev Kontrol Et
- Sınıf seçildiğinde o sınıfa verilen ödevlerin listelenmesi
- Her ödevin yanında **Kontrol Et** butonu ve işaretlenen öğrenci sayısı (ör. `12/25`)
- Öğrenci listesi ve **Yaptı / Yapmadı / Gelmedi** sütunları (her öğrenci için tek seçim)
- **Kaydet** butonu ile seçimlerin saklanması
- **Gönder** butonu ile WhatsApp mesajının oluşturulması ve kopyalanması

## WhatsApp Mesaj Formatı

Gönder butonuna basınca aşağıdaki gibi bir mesaj oluşur:

```
📚 8-A - 23.10.2026

Ali Yılmaz, Veli Kaya öğrencileri Sayfa 45 ödevini yapmadı.
Ayşe Demir öğrencileri Sayfa 45 ödevini getirmedi.
```

- **Yapmadı** işaretlenenler → "ödevini yapmadı"
- **Gelmedi** işaretlenenler → "ödevini getirmedi"
- Kimse işaretlenmediyse: "Tüm öğrenciler ... ödevini yaptı."

Mesaj penceresindeki **Kopyala** butonuyla metni alıp WhatsApp'a yapıştırabilirsin.

## Kullanım

1. `odev-takip.html` dosyasını tarayıcıda aç (çift tıklaman yeterli).
2. **Sınıflar & Öğrenciler** sekmesinde sınıfı ve öğrencileri ekle.
3. **Ödev Ekle** sekmesinde sınıfa ödev ver.
4. **Ödev Kontrol Et** sekmesinde sınıfı seç, ödevin yanındaki **Kontrol Et** butonuna tıkla, işaretlemeleri yap ve **Kaydet** veya **Gönder**'e bas.

## Veri Saklama

- Tüm veriler tarayıcının `localStorage` alanında, `odevTakip.v1` anahtarı altında tutulur.
- Sunucu, hesap veya internet bağlantısı gerekmez.
- Veriler yalnızca o cihazdaki o tarayıcıda görünür. Tarayıcı verileri temizlenirse silinir.
- Sınıf silindiğinde o sınıfın öğrencileri, ödevleri ve kontrol kayıtları da silinir.

## Veri Yapısı

```json
{
  "classes":   [{ "id": "...", "name": "8-A", "students": [{ "id": "...", "name": "Ali Yılmaz" }] }],
  "homeworks": [{ "id": "...", "classId": "...", "title": "Sayfa 45", "date": "2026-10-23", "note": "" }],
  "checks":    { "<ödevId>": { "<öğrenciId>": "yapti | yapmadi | gelmedi" } }
}
```

## Teknik Bilgiler

- Tek dosya: HTML + CSS + vanilla JavaScript
- Harici kütüphane veya CDN bağlantısı yok
- Mobil ve masaüstü uyumlu (responsive) arayüz
- Kullanıcı girdileri HTML'e yazılırken kaçışlanır (XSS'e karşı)

## Dosyalar

| Dosya | Açıklama |
|---|---|
| `odev-takip.html` | Uygulamanın tamamı |
| `README.md` | Bu açıklama dosyası |
