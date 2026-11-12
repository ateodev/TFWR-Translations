# Kopie přes Zkratky
Aplikace Zkratky může při každém odchodu ze hry zkopírovat tvoje uložené hry na místo, které si vybereš, třeba na iCloud Drive. Dělá to sama, bez ptaní. Patří to k plné verzi.

## Nastavení
1. V aplikaci **Zkratky** klepni na + pro novou zkratku, vpravo nahoře klepni na **Upravit** a přidej akci hry **Získat poslední save**.
2. Přidej **Uložit soubor** a klepni na jeho šipku. Vypni **Zeptat se na místo uložení**, vyber složku a zapni **Přepsat soubor, pokud existuje**.
3. Dole klepni na **Hledat**, pak na **Automatizace** a pod nadpisem **Aplikace** zvol **Aplikace**.
4. V řádku, který se objeví, klepni na **Aplikace** a vyber hru, pak klepni na **otevře** a zvol **zavře**.

Před iOS 27 vytvoř automatizaci místo toho na kartě **Automatizace**: zvol **Aplikace**, hru, jen **je zavřená** a **Spustit okamžitě** a přidej do ní akce z kroků 1 a 2. V iOS 16 místo toho vypni **Zeptat se před spuštěním**.

Každá kopie je zip pojmenovaný podle své uložené hry, takže od každé uložené hry máš jednu aktuální kopii.

## Starší kopie
Vlož do cesty ke složce v akci **Uložit soubor** proměnnou **Dnešní datum**. Kopie z jiného dne pak půjdou do vlastní složky a ty starší zůstanou.

## Další akce
**Získat save** získá jednu uloženou hru podle jejího názvu. **Získat savy** získá všechny uložené hry, nebo jen ty změněné od nějakého data.

## Vrácení kopie
Tyto akce uložené hry jen kopírují ven. Kopii vrátíš tak, že na obrazovce „Nahrát“ stiskneš „Import“ a vybereš její zip.

Cloudové ukládání drží tvoje zařízení na stejném postupu. Kopie ze Zkratek je tvůj vlastní soubor, uložený tam, kde si vybereš, pro historii nebo pro hru na PC.
