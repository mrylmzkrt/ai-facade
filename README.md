# Facade AI DXF

FacadeTool benzeri bir online MVP: cephe fotoğrafını yapay zekâ ile analiz eder, pencere/kapı/kat çizgisi/kolon/ana kontur verisini layerlı DXF çizimine dönüştürür.

Bu sürüm tek başına klasik edge-detection yapmaz. Kaliteli sonuç için server tarafında OpenAI vision modeli kullanır. `OPENAI_API_KEY` tanımlı değilse sadece fallback/test geometrisi üretir.

## Özellikler

- Cephe fotoğrafı yükleme
- 4 cephe köşesi seçme
- Cephe genişliği/yüksekliği girme
- AI ile mimari eleman algılama
- SVG önizleme
- DXF indirme
- Layer yapısı:
  - `A-FACADE-OUTLINE`
  - `A-OPENING-WINDOW`
  - `A-OPENING-DOOR`
  - `A-FLOOR-LINE`
  - `A-AXIS`
  - `A-COLUMN`
  - `A-BALCONY-RAILING`
  - `A-ORNAMENT-SIMPLIFIED`
  - `A-NOTE`
  - `A-REFERENCE`

## Online yayınlama: Vercel

Yerelde terminal kullanmadan yayınlamak için:

1. Bu klasörü GitHub'da yeni bir repository'ye yükle.
2. Vercel'e gir: https://vercel.com/new
3. GitHub repository'ni seç.
4. Environment Variables bölümüne şunu ekle:

```txt
OPENAI_API_KEY=senin_openai_api_keyin
OPENAI_MODEL=gpt-5.4-mini
```

5. Deploy butonuna bas.

## Kullanım

1. Siteyi aç.
2. Cephe görselini yükle.
3. Cephe köşelerini sırayla seç:
   - sol üst
   - sağ üst
   - sağ alt
   - sol alt
4. Cephe genişliği ve yüksekliğini metre olarak gir.
5. Algılama modunu seç.
6. `Cepheyi algıla ve DXF üret` butonuna bas.
7. DXF'i indir ve AutoCAD/Rhino içinde aç.

## Önemli not

Bu araç röleve veya uygulama projesi yerine geçmez. AI çıktısı mimari çizime hızlı başlangıç için base drawing üretir. Ölçüler ve cephe elemanları mutlaka kontrol edilmelidir.

## Yerel çalıştırmak gerekirse

```bash
npm install
npm run dev
```

Sonra `.env.local` dosyasına OpenAI API anahtarını ekle:

```txt
OPENAI_API_KEY=sk-...
OPENAI_MODEL=gpt-5.4-mini
```
