# Hasan Hoca Randevu Sistemi

Ogrencilerin ve velilerin online randevu alabilecegi, Google Form tarzi bir randevu sistemi.

**Ozellikler:**
- Google Form gorunumunde randevu formu
- Admin paneli ile musait saatleri dinamik guncelleme
- Randevu geldiginde otomatik e-posta bildirimi
- Tum randevulari admin panelden goruntuleme
- Ucretsiz (Google Sheets + GitHub Pages)

---

## Kurulum Rehberi (Adim Adim)

### ADIM 1: Google Sheets Olusturun

1. **Google Drive**'a gidin: https://drive.google.com
2. Sol ustte **"+ Yeni"** > **"Google E-Tablolar"** > **"Bos e-tablo"** tiklayin
3. Tabloya isim verin: **"Randevu Sistemi Veritabani"**

> Bu tablo hem musait saatlerinizi hem de gelen randevulari saklayacak.

---

### ADIM 2: Google Apps Script Olusturun

1. Olusturdugunuz tabloda ust menuden **Uzantilar** > **Apps Script** tiklayin
2. Yeni bir sekme acilacak (Apps Script editoru)
3. Sol tarafta `Kod.gs` dosyasini goreceksiniz
4. Icindeki tum kodu **silin**
5. Bu repodaki **`google-apps-script.gs`** dosyasinin icerigini **kopyalayip yapistin**
6. **Ctrl+S** ile kaydedin

> **ONEMLI:** Kod icindeki `ADMIN_SIFRE` degerini kendi istediginiz bir sifreyle degistirin!

---

### ADIM 3: Ilk Kurulumu Calistirin

1. Apps Script editorunde ust tarafta fonksiyon secici var (varsayilan "myFunction" yazar)
2. Acilir menuden **`ilkKurulum`** fonksiyonunu secin
3. **"Calistir"** (ucgen ikon) butonuna basin
4. **Yetkilendirme** isteyecek:
   - "Izinleri incele" tiklayin
   - Google hesabinizi secin
   - "Gelismis" > "... (guvenli degil) sayfasina git" tiklayin
   - "Izin ver" tiklayin
5. Calistiktan sonra "Kurulum tamamlandi!" mesajini goreceksiniz

> Simdi Google Sheets'e donup bakin: "Slotlar" ve "Randevular" adinda iki sayfa olusmus olmali.

---

### ADIM 4: Web Uygulamasi Olarak Yayinlayin

1. Apps Script editorunde sag ustteki **"Dagit"** > **"Yeni dagitim"** tiklayin
2. Sol tarafta disli ikonu > **"Web uygulamasi"** secin
3. Ayarlar:
   - **Aciklama:** "Randevu Sistemi API"
   - **Olarak calistir:** "Ben" (kendi hesabiniz)
   - **Erisim yetkisi olan:** **"Herkes"** (onemli!)
4. **"Dagit"** butonuna basin
5. **Web uygulamasi URL'si** gorunecek. Bu URL'yi kopyalayin!

> URL su sekilde gorunur:
> `https://script.google.com/macros/s/AKfycbx.../exec`
>
> **BU URL'yi NOT EDIN** - bir sonraki adimda lazim olacak!

---

### ADIM 5: HTML Dosyalarini Guncelleyin

Bu repoda 2 HTML dosyasi var:

#### `index.html` (Randevu formu)
1. Dosyayi bir metin editoruyle acin (Not Defteri veya VS Code)
2. Icinde su satiri bulun:
   ```
   const API_URL = 'BURAYA_APPS_SCRIPT_URL_YAPISTIRILACAK';
   ```
3. `BURAYA_APPS_SCRIPT_URL_YAPISTIRILACAK` kismini 4. adimda kopyaladiginiz URL ile degistirin:
   ```
   const API_URL = 'https://script.google.com/macros/s/AKfycbx.../exec';
   ```
4. Kaydedin

#### `admin.html` (Admin paneli)
1. Ayni sekilde acin
2. Ayni `API_URL` satirini bulup ayni URL'yi yapistin
3. Kaydedin

---

### ADIM 6: GitHub'a Yukleyin ve Yayinlayin

#### 6a. GitHub Hesabi Olusturun (yoksa)
1. https://github.com adresine gidin
2. **"Sign up"** tiklayin
3. E-posta, sifre ve kullanici adi girin
4. Hesabi dogrulayin

#### 6b. Yeni Repo Olusturun
1. GitHub'da sag ustte **"+"** > **"New repository"** tiklayin
2. Ayarlar:
   - **Repository name:** `randevu` (veya istediginiz bir isim)
   - **Description:** "Randevu alma sistemi"
   - **Public** secili olmali (GitHub Pages icin gerekli)
   - **Add a README file** tiklamayin (biz zaten haziladik)
3. **"Create repository"** tiklayin

#### 6c. Dosyalari Yukleyin
1. Repo sayfasinda **"uploading an existing file"** linkini tiklayin
   (veya **"Add file"** > **"Upload files"**)
2. Su 3 dosyayi surekleyip birakin:
   - `index.html`
   - `admin.html`
   - `README.md`
3. Alttaki **"Commit changes"** butonuna basin

#### 6d. GitHub Pages'i Aktif Edin
1. Repo sayfasinda **"Settings"** sekmesine tiklayin (ustteki menu)
2. Sol menuden **"Pages"** tiklayin
3. **"Source"** altinda:
   - **Branch:** `main` secin
   - **Folder:** `/ (root)` secin
4. **"Save"** tiklayin
5. BirkaC dakika bekleyin. Sayfa yenilendiginde ustte yesil bir kutu goreceksiniz:
   > "Your site is live at https://KULLANICIADI.github.io/randevu/"

---

### ADIM 7: Test Edin

1. **Randevu formu:** `https://KULLANICIADI.github.io/randevu/`
2. **Admin paneli:** `https://KULLANICIADI.github.io/randevu/admin.html`

- Formdan bir test randevusu gonderin
- E-posta geldigini kontrol edin
- Admin panele giris yapin (Apps Script'te belirlediginiz sifre ile)
- Saatleri degistirmeyi deneyin

---

## Kullanim

### Ogrencilere/Velilere Link Gonderme

Formu paylasmak icin bu linki gonderin:
```
https://KULLANICIADI.github.io/randevu/
```

WhatsApp, Instagram, e-posta — istediginiz yerden paylasabilirsiniz.

### Saatleri Guncelleme

1. `https://KULLANICIADI.github.io/randevu/admin.html` adresine gidin
2. Sifrenizle giris yapin
3. **"Musait Saatler"** sekmesinde:
   - Yesil/mor olan saatler = AKTIF (ogrenciler gorebilir)
   - Bir saate tiklayarak acip kapatabilirsiniz
4. **"Degisiklikleri Kaydet"** butonuna basin

### Randevulari Goruntuleme

Admin panelde **"Randevular"** sekmesine tiklayin. Tum gelen randevulari burada gorebilirsiniz.

---

## Dosya Yapisi

```
randevu/
  index.html              <- Randevu formu (ogrenciler bunu gorur)
  admin.html              <- Admin paneli (sadece siz)
  google-apps-script.gs   <- Google Apps Script kodu (Sheets'e yapistirirsiniz)
  README.md               <- Bu dosya
```

---

## Sik Sorulan Sorular

**S: Apps Script'i guncelledim ama calismadi?**
Her kod degisikliginden sonra Apps Script'te **"Dagit" > "Dagitimlari Yonet"** > sag ustte **kalem ikonu** > **"Yeni surum"** > **"Dagit"** yapmaniz gerekir.

**S: E-posta gelmiyor?**
Gmail gonderim limiti gunluk 100'dur. Apps Script'teki `EMAIL` degerinin dogru oldugundan emin olun.

**S: Admin sifremi nasil degistiririm?**
Apps Script'te `ADMIN_SIFRE` degerini degistirin ve yeni surum olarak dagitin.

**S: Formu Turkce karakterlerle gosteremiyorum?**
Dosyalari UTF-8 kodlamasiyla kaydettiginizden emin olun.
