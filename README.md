# nightcafe-site — The Night Café csatornaoldal

A **The Night Café** rövidvideós animációs sorozat (Kapi, a kapibara barista és Bruno, a szorongó
galamb egy éjjel nyitva tartó neonos kávés standnál) statikus bemutató oldala, a hozzá tartozó
**adatvédelmi tájékoztatóval** és **felhasználási feltételekkel**.

Élő oldal: **https://bkiscsatari.github.io/nightcafe-site/** (GitHub Pages, `main` ág, gyökér, HTTPS kényszerítve).

## Miért létezik

A tartalmat a **Viral Content Engine** (`bkiscsatari/Viralsocial`) gyártja és tölti fel automatikusan.
A platform-integrációkhoz nyilvános adatvédelmi és ÁSZF-URL kell:

- a **YouTube Data API** OAuth-appja (a `youtube.upload` hatókör) — az app „Production” státuszban
  van, nem lejáró refresh tokennel (2026-08-26);
- esetleg a Meta (Instagram / Facebook) és a TikTok fejlesztői appok beállításai is, ha azok
  ugyanezekre az URL-ekre hivatkoznak (ezt az appok konzolján kell ellenőrizni).

Ezek az URL-ek ide mutatnak, ezért **az oldalak címét és elérhetőségét nem szabad megváltoztatni**
anélkül, hogy a platform-appok beállításait is frissítenénk.

## Felépítés

| Fájl | Útvonal | Tartalom |
|---|---|---|
| `index.html` | `/` | A sorozat egy bekezdéses bemutatása, AI-jelölés („minden epizód AI-generált animáció, eredeti szereplőkkel”), link a YouTube-csatornára, az adatvédelmi és az ÁSZF-oldalra |
| `privacy.html` | `/privacy.html` | Adatvédelmi tájékoztató: a Viral Content Engine magáncélú, egyfelhasználós alkalmazás; harmadik fél személyes adatát nem gyűjti, nem tárolja, nem osztja meg; a Google-hozzáférést (`youtube.upload`) csak a saját csatornára feltöltéshez használja, a hitelesítő adatok a tulajdonos saját infrastruktúráján vannak; csak nyilvános platformadatot olvas hivatalos API-n; az oldal nem használ sütit, analitikát vagy követést; kapcsolat |
| `terms.html` | `/terms.html` | Felhasználási feltételek: magáncélú alkalmazás, nem szolgáltatás mások számára, nincs felhasználói fiók és nincs felhasználói tartalom; minden videó AI-generált, így jelölve, szórakoztatási céllal, „ahogy van”; kapcsolat |

Technika: három önálló, kézzel írt HTML-fájl, beágyazott CSS-sel (sötét téma, `max-width: 40rem`),
JavaScript, külső betűtípus, süti és követés nélkül. Build-lépés nincs; a GitHub Pages a `main` ág
gyökeréből szolgálja ki.

## Módosítás

Szerkeszd a HTML-fájlt, frissítsd a „Last updated” dátumot, és pushold a `main`-re; a Pages
néhány percen belül kiteszi. Ha az alkalmazás adatkezelése változik (új platform, új hatókör, új
adattípus), a `privacy.html`-t ugyanabban a lépésben kell frissíteni.

## Nyitott pont

A `privacy.html` jelenleg csak a Google / YouTube hozzáférést írja le. A Viral Content Engine
Instagramra és Facebookra is posztol (a `tekpiks` Meta appon át), ezért ha a Meta app ezt az URL-t
használja adatvédelmi tájékoztatóként, a szöveget ki kell egészíteni a Meta-jogosultságokkal.
