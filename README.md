# Website Content (GitHub = SQL)

Bu klasordeki JSON dosyalari sitenin "veritabani" gibi davranir.
Sitedeki Skills, Timeline, Achievements, Certificates, Services, Testimonials,
Media, Metrics ve Settings bolumleri bu dosyalardan okunur.

## Nasil calisir

1. `.env.local` icinde `GITHUB_CONTENT_REPO=senin-kullanici-adin/website-content` tanimla.
2. Bu klasordeki tum dosyalari o repoya (repo kokune, `main` branch) push et.
3. Site her saat icerikleri o repodan ceker. Repo yoksa buradaki fallback dosyalari kullanilir.

## Projeler otomatik

Projeler **Supabase veya admin paneli olmadan** dogrudan GitHub repolarindan gelir:

- Yeni bir projeye baslayinca sadece **public repo ac** -> sitede gorunur.
- Repoya son 10 gun icinde push atildiysa durum **"aktif calisiyor"**.
- 10 gunluk surede push yoksa durum **"bitti"**.
- Sureyi `GITHUB_ACTIVE_DAYS` env degiskeni ile degistirebilirsin.

## Repo -> Kategori eslemesi

Kategori repo topic'leri ve dili kullanilarak otomatik atanir:

| Kategori | Topic / Dil |
| --- | --- |
| Oyun | `game`, `unity`, `unreal`, `godot` |
| AI / Veri Bilimi | `ai`, `ml`, `llm`, `python`, `jupyter notebook` |
| Elektronik/IoT | `iot`, `arduino`, `esp32`, `esp8266`, `embedded`, `C`, `C++` |
| Web | `web`, `frontend`, `backend`, `react`, `nextjs`, `javascript`, `typescript` |
| Muhendislik | `labview` (varsayilan) |

Kategoriyi degistirmek istersen reponun **topics** alanina yukaridaki anahtar
kelimelerden birini ekle (orn. `ai` topic'i ekleyince proje AI bolumune duser).

## Iletisim

Contact form mesajlari `GITHUB_CONTENT_REPO` (veya `GITHUB_USERNAME/website-content`)
repoda **GitHub Issue** olarak acilir. Token'da `public_repo` scope'u olmali.