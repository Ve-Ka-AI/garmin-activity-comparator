# Garmin Activity Comparator 🚴🏃📊

Pokročilý klientský nástroj pro porovnávání a analytickou vizualizací více Garmin `.fit` aktivit najednou (až 5 aktivit vedle sebe) přímo v prohlížeči bez nahrávání dat na server.

🔗 **Živé demo na GitHub Pages:** `https://ve-ka-ai.github.io/garmin-activity-comparator`

---

## 🌟 Hlavní Funkce & Vlastnosti

- **100% Klientské zpracování (Browser-Only)**: Zero-server privacy guarantee. Žádná data se neukládají ani neodosílají na server.
- **Duální Parsovací Engine**: CDN ES Module `fit-parser.js` s vysoce výkonným záložním binárním FIT parserem.
  - Přepočet Garmin semicircles na stupně (`semicircles * 180 / 2^31`).
  - Přepočet Garmin epoch časových razítek (`+ 631065600`).
- **Nahrávání složek & Automatické párování**:
  - Podpora nahrávání celých složek (`webkitdirectory`) i drag-and-drop. Podadresáře (např. `/Vasek/`, `/Manzelka/`) automaticky určují jména uživatelů.
  - **Scénář A (Společná aktivita)**: Automaticky detekuje a seskupí aktivity různých uživatelů se startem ve stejný den a čas (tolerance ±15 min) s podobnou délkou trvání.
  - **Scénář B (Opakovaná trasa)**: Detekuje opakované jízdy/běhy jednoho uživatele/zařízení na stejné trase (start/cíl v okruhu 100 m a geometrický překryv trasy).
- **Detekce Zdroje Dat & Připojených Čidel**:
  - Automaticky rozliší externí senzor teploty **Garmin Tempe** vs. optické merání ze zápěstí.
  - Detekuje spárovaný **Garmin Snímač Rychlosti Kola (Bike Speed Sensor)**.
- **Analýza Frekvence Záznamu**:
  - Vyhodnotí průměrný rozestup trasových bodů a detekuje **1s Záznam** vs. **Chytrý záznam (Smart Recording)** včetně hustoty bodů na km.
- **Interaktivní Mapa & Synchronizované Grafy**:
  - Překryv tras 2 až 5 aktivit odlišnými barvami na Leaflet.js mapě.
  - **Synchronizovaný Crosshair**: Pohyb kurzoru po grafech automaticky posouvá svítící ukazatel na mapě u všech srovnávaných aktivit současně.
  - Přepínání osy X (**Čas** vs **Vzdálenost**), jednotek (**Rychlost km/h** vs **Tempo min/km**) a tepu (**BPM** vs **% max HR**).
- **Export do Excelu (.xlsx)**:
  - Kompletní srovnávací matice metrik ke stažení jedním kliknutím.

---

## 🚀 Jak nasadit na GitHub Pages

1. **Vytvoření nového repozitáře na GitHubu**:
   - Přejděte na [GitHub New Repository](https://github.com/new) pod účtem `Ve-Ka-AI`.
   - Pojmenujte repozitář: `garmin-activity-comparator`.
   - Nastavte jako **Public**.

2. **Odeslání kódu z lokální složky**:
   ```bash
   git init
   git add index.html README.md
   git commit -m "Initial release of Garmin Activity Comparator"
   git branch -M main
   git remote add origin https://github.com/Ve-Ka-AI/garmin-activity-comparator.git
   git push -u origin main
   ```

3. **Aktivace GitHub Pages**:
   - V nastavení repozitáře (`Settings` -> `Pages`).
   - Pod **Build and deployment** vyberte **Source**: `Deploy from a branch`.
   - Vyberte větev **`main`** / složku **`/(root)`** a klikněte na **Save**.
   - Aplikace bude během 1–2 minut dostupná na `https://ve-ka-ai.github.io/garmin-activity-comparator`.

---

## 🛠️ Použité Technologie

- **HTML5 & CSS3**: Glassmorphism Dark Mode Design System (`Outfit` & `Inter` Google Fonts).
- **Leaflet.js**: Interaktivní mapový podklad & vykreslování GPS tras.
- **Chart.js**: Synchronizované výkonnostní grafy s crosshair ukazatelem.
- **SheetJS (xlsx)**: Klientský export srovnávacích tabulek do Microsoft Excel `.xlsx`.
