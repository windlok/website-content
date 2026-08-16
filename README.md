# Website Content (GitHub = SQL)

Bu klasordeki JSON dosyalari sitenin "veritabani" gibi davranir.
Sitedeki Timeline, Achievements, Certificates, Metrics ve Settings bolumleri
bu dosyalardan okunur.

## Skills (Yetenek Matrisi)

- **Languages** grubu: GitHub repolarindan **otomatik** hesaplanir
  (her dilin kac projede kullanildigi + seviye).
- `skills.json`: GitHub'da gorunmeyen diller icin eklenir (ornegin
  LabVIEW). `group_name` degeri "Languages" olursa otomatik listeye
  karisir, `count` alani "X proje" olarak gosterilir.

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

Oncelik sirasi: **repo topics > dil > varsayilan (Muhendislik)**.
Yani bir repoya `web` topic'i eklersen, dili Python bile olsa Web kategorisine duser.

| Kategori | Topic (oncelikli) | Dil (topic yoksa) |
| --- | --- | --- |
| Oyun | `game`, `game` isimli repo | - |
| AI / Veri Bilimi | `ai`, `ml`, `llm`, `machine-learning`, `data-science`, `model` | `Jupyter Notebook` |
| Elektronik/IoT | `iot`, `arduino`, `esp32`, `esp8266`, `embedded`, `hardware`, `sensor` | `Arduino`, `Embedded C` |
| Web | `web`, `frontend`, `backend`, `react`, `nextjs`, `django`, `flask`, `api` | `JavaScript`, `TypeScript`, `HTML`, `CSS`, `PHP`, `Vue`, `Svelte`, `Astro` |
| Muhendislik | `labview`, `automation`, `engineering` | `C`, `C++`, `LabVIEW`, `Python` (varsayilan) |

**Not:** Python tek basina AI degildir! Python reposu Muhendislik'e duser;
AI olmasi icin `ai` / `ml` / `llm` gibi topic eklemen gerekir.

## Ozel baslik (title)

Repo adi otomatik temizlenir (alt cizgi/tek tire -> bosluk, dil eki
cikarilir: `Muta-File-Transfer-Server-c` -> "Muta File Transfer Server").
Yine de basligi kendin belirlemek istersen repoya `title-` ile baslayan bir
topic ekle (topic kurallari: kucuk harf + tire):

| Repo topic'i | Sitedeki baslik |
| --- | --- |
| `title-instagram-botu` | Instagram Botu |
| `title-3d-printer-web` | 3D Printer Web |
| `title-cakma-mario` | Cakma Mario |

`title-` ile baslayan topic'ler kategori eslemesine ve stack cihplerine
karistirilmaz.

## Iletisim

Contact form mesajlari `GITHUB_CONTENT_REPO` (veya `GITHUB_USERNAME/website-content`)
repoda **GitHub Issue** olarak acilir. Token'da `public_repo` scope'u olmali.