# Dijital davetiye: ChatGPT ile yapım kılavuzu

Bu kılavuz, hazır davetiye şablonunu bir çifte göre düzenleyip yayına almayı anlatıyor.
Kod bilmen gerekmiyor. Kod gerektiren yerde işi ChatGPT yapıyor, sen dosyayı kaydedip yüklüyorsun.

Örnek sonuç: https://meyigun34.github.io/davetiye/

---

## 0. Gerekenler

- Bir bilgisayar (telefondan yapılmaz, dosya yüklemek zor).
- ChatGPT hesabı. Dosya yükleyebildiğin bir sürüm işini kolaylaştırır.
- Ücretsiz bir GitHub hesabı: https://github.com/signup
- Bir metin düzenleyici. Mac'te TextEdit yerine **VS Code** öner (ücretsiz, https://code.visualstudio.com).
  TextEdit tırnak işaretlerini bozabiliyor.

## 1. Şablonu indir

1. https://github.com/meyigun34/davetiye adresine git.
2. Yeşil **Code** düğmesi → **Download ZIP**.
3. ZIP'i aç. Klasörün içi şöyle olmalı:

```
index.html     sayfanın kendisi (tasarım, animasyon)
veri.json      çiftin bilgileri
doku/          dantel, inci ve kağıt görselleri
```

Bu üçü hep birlikte durur. `doku` klasörü eksik kalırsa dantel görünmez.

## 2. Yeni çiftin bilgilerini gir (her müşteride bu adım)

Yalnız `veri.json` değişir. İki yolu var.

**Elle:** `veri.json`'u VS Code ile aç, tırnak içindeki yazıları değiştir, kaydet.

**ChatGPT ile:** `veri.json`'un içeriğini kopyala ve şunu yaz:

```
Aşağıdaki JSON bir düğün davetiyesinin bilgileri. Yapıyı, alan adlarını ve
tırnakları değiştirmeden yalnız değerleri şu bilgilere göre doldur.
Cevap olarak sadece JSON'u ver, açıklama yazma.

Gelin: Ayşe
Damat: Mert
Tarih ve saat: 5 Eylül 2027, 19.00
Mekân: Göl Evi, Sapanca
Akış: 18.30 karşılama, 19.00 nikâh, 20.00 yemek, 22.00 ilk dans
Kıyafet notu: ...
LCV son tarihi: 1 Ağustos 2027

<veri.json içeriğini buraya yapıştır>
```

Gelen cevabı `veri.json`'un içine yapıştırıp kaydet.

Alanların anlamı:

| Alan | Ne yazılır | Dikkat |
|---|---|---|
| `gelin`, `damat` | İsimler | |
| `monogram` | Mühürdeki harfler, örn. `A&M` | En çok 3-4 karakter, sığmaz |
| `tarih` | Geri sayım için: `2027-09-05T19:00:00+03:00` | Bu biçim bozulursa geri sayım çalışmaz |
| `tarih_yazi` | Ekranda görünen tarih, örn. `5 Eylül 2027 · Pazar` | |
| `ust_satir` | İsimlerin üstündeki küçük yazı | |
| `mekan.ad`, `mekan.adres` | Mekân adı ve adresi | |
| `mekan.harita` | Google Haritalar'da mekânı aç → Paylaş → bağlantıyı kopyala | |
| `akis` | Saat, ad ve ikon | İkon yalnız `kadeh`, `yuzuk`, `tabak`, `nota` olabilir |
| `kiyafet` | Kıyafet notu | |
| `lcv_son` | Katılım için son tarih | |

## 3. Tasarımı değiştirmek (isteğe bağlı)

Renk, yazı tipi, bölüm ekleme ya da çıkarma `index.html`'de yapılır. ChatGPT'ye
`index.html` dosyasını yükle (yükleyemiyorsan içeriğini yapıştır) ve şu kalıbı kullan:

```
Ekteki index.html mobil bir düğün davetiyesi. Şu değişikliği yap:
<istediğin değişiklik>

Kurallar:
- Başka hiçbir şeyi değiştirme. Zarf animasyonu, veri.json okuma ve doku/ görselleri aynı kalsın.
- Dosyanın TAMAMINI tek parça halinde ver, "..." ile kısaltma.
```

Örnek istekler:
- "Mürdüm rengini (#4B2236) zümrüt yeşili yap." Renkler dosyanın en üstünde, `:root` bölümünde duruyor.
- "Kıyafet bölümünü kaldır."
- "Mekân bölümünün altına 'Konaklama' diye bir bölüm ekle, bilgisini veri.json'dan oku."

ChatGPT'nin verdiği dosyayı `index.html`'in yerine kaydet. Önce eskisinin bir kopyasını al:
bir şey bozulursa geri dönersin.

**Bu kılavuzun dışında kalan:** dantel deseninin kendisini (çiçek şekli, dantel rengi)
değiştirmek. `doku/` klasöründeki görseller ayrı bir programla üretiliyor; ChatGPT bunu
sohbette yapamaz.

## 4. Denemek

Bilgisayarda `index.html`'e çift tıklarsan sayfa çoğu tarayıcıda **boş açılır**. Bu bir
hata değil: tarayıcı güvenlik yüzünden `veri.json`'u diskten okutmuyor.

Denemenin iki yolu var:
- **En kolayı:** 5. adımdaki gibi GitHub'a yükle, linkten telefonda aç.
- **Bilgisayarda:** VS Code'a **Live Server** eklentisini kur, `index.html`'e sağ tıkla →
  *Open with Live Server*. Tarayıcıda telefon görünümüne geçmek için F12 → telefon simgesi.

Kontrol listesi:
- [ ] Zarfa dokununca açılıyor mu?
- [ ] İsimler, tarih, mühürdeki harfler doğru mu?
- [ ] Geri sayım işliyor mu?
- [ ] "Yol tarifi" doğru yeri açıyor mu?
- [ ] Sayfa sonuna kadar kayıyor mu?

## 5. Yayına almak (GitHub Pages, ücretsiz)

Her çift için ayrı bir depo aç, böylece her çiftin ayrı bir linki olur.

1. GitHub'da sağ üstte **+** → **New repository**.
2. Ad olarak çiftin adını yaz, örn. `ayse-mert`. **Public** seçili olsun. **Create repository**.
3. Açılan sayfada **uploading an existing file** bağlantısına tıkla.
4. `index.html`, `veri.json` ve `doku` klasörünü birlikte sürükle-bırak. Klasörü sürüklemek
   önemli, içindeki görseller `doku/` altında kalmalı. **Commit changes**.
5. Depoda **Settings** → soldan **Pages** → *Branch* altında `main` ve `/ (root)` seç → **Save**.
6. 1-2 dakika bekle. Link: `https://<kullanıcı-adın>.github.io/ayse-mert/`

Sonradan bir düzeltme yaparsan aynı depoda dosyanın üstüne yeniden yükle, link aynı kalır.
Değişikliğin görünmesi bir iki dakika sürebilir.

**Not:** Depo herkese açık. Çiftin telefonu, ev adresi gibi bilgileri `veri.json`'a koyma.

## 6. Katılım formu (LCV)

Şablondaki form şu an cevapları **hiçbir yere kaydetmiyor**, yalnız teşekkür yazısı gösteriyor.
Cevapların çifte ulaşması için formun bir form servisine bağlanması gerekiyor.
Formspree gibi bir servise üye olup sana verdiği adresle ChatGPT'ye şunu yaz:

```
Ekteki index.html'deki id="lcv" formunun cevaplarını şu Formspree adresine
göndersin: <adres>. Gönderim başarılıysa mevcut teşekkür yazısı görünsün,
hata olursa "Gönderilemedi, tekrar deneyin" yazsın. Başka hiçbir şeyi değiştirme.
Dosyanın tamamını ver.
```

Bunu ilk kez yaptıktan sonra kendi telefonundan bir deneme cevabı gönder, servise ulaştığını gör.

## 7. Sık karşılaşılan sorunlar

| Belirti | Sebep | Çözüm |
|---|---|---|
| Sayfa bembeyaz ya da zarf hiç çıkmıyor | `veri.json`'da virgül ya da tırnak hatası | İçeriği ChatGPT'ye yapıştır: "Bu JSON geçerli mi, hatayı düzelt" |
| Zarf var ama dantel yok, düz renk | `doku` klasörü yüklenmemiş ya da adı değişmiş | Klasörü adını değiştirmeden yeniden yükle |
| Geri sayım 0 gösteriyor | `tarih` biçimi bozuk ya da tarih geçmiş | `2027-09-05T19:00:00+03:00` biçimine bak |
| ChatGPT'nin verdiği dosya yarım | Uzun dosyada kısaltma yapmış | "Dosyanın tamamını, kısaltmadan ver" diye tekrar iste |
| Link açılınca 404 | Pages henüz hazır değil ya da `index.html` kök dizinde değil | 2 dakika bekle; dosyalar klasör içinde değil, deponun kökünde olmalı |
| Yaptığın değişiklik görünmüyor | Telefon eski sürümü hatırlıyor | Sayfayı yenile ya da gizli sekmede aç |
