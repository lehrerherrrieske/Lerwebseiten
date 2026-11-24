# Krisenstab Kryptologie – wachsende Lernwebseite (GK 11, LB4)

Datei: `K11GK - LB4 - Krisenstab_Kryptologie.html` (lernhtml, Krisenstab-Look dunkel/amber)
Kennnummer: MR-20261123-0E536D · Lehrerpasswort: `VeniVidiVici`
Neue Wochen immer in DIESE Datei einbauen (gleiche Kennnummer → Schülerfortschritt bleibt erhalten).

## Story-Stand (Funkspruch 1 = Skytale + Cäsar)
- Lagebericht: Cyberangriff DI 07:13, 24 h ohne Verschlüsselung, Krisenstab-Teams, Kryptogebäude abgebrannt → zurück zu den Anfängen.
- Brieftauben/Skytale: Taube 1 bringt Stab (Dicke 4), Taube 2 Streifen; Antwort mit Stab 5 („WIR BRAUCHEN UNTERSTUETZUNG IN BAYERN“); Falke schlägt Stab-Taube → Durchprobieren (Dicke 6) → Frequenz 88,3 MHz.
- Funkgerät (Popup unten rechts) mit Funkerin Berger (HQ), Cäsar-Scheibe (Popup, drehbar):
  2.2 Gruß k=3 entschlüsseln · 2.3 Anweisung (k=3) → neuer Schlüssel 11, Lagebericht verschlüsselt funken · 2.4 Feindspruch „DER FEIND HOERT MIT“ k=19 (Brute Force) · 2.6 langer Feindspruch k=8 per Häufigkeitsanalyse (Zählwerk, M↔E) · 2.7 Treffpunkt FERNSEHTURM.
- Pointe/Cliffhanger: Feind hat alle Cäsar-Funksprüche mitgelesen → „Ein einziger fester Schlüssel reicht nicht“ → nächster Funkcode.
- Geplante Fortsetzung laut Folien: Vigenère (Blaufieber Saarland, Schlüssel KRYPTO), Kasiski-Test (General-Nachricht, Schlüssel PRAKTIKANT, Länge 10!), danach Asymmetrisch/RSA, Steganographie.

## Funkcode-Mechanik (Wochen unsichtbar bis Code)
- Im Script-Block `/* >>> FUNKCODE */`: `var WOCHEN=[ {h:'…',d:'…'}, … ];`
- Jede Woche = verschlüsseltes JSON `{id:'ph4', titel:'Funkspruch 2 · …', nav:'<button class="pnav" id="pn4" onclick="showPhase(4)">…</button>', html:'<section class="phase" id="ph4">…</section>', js:'…'}`.
- Code normalisieren: Großbuchstaben, Ä→AE…, nur A–Z0–9. Prüf-Hash: FNV-1a 32 Bit von `'pruef:'+code` (hex). Schlüsselstrom: mulberry32(FNV-1a(`'schluessel:'+code`)), Byte = floor(r()*256), XOR über UTF-8-JSON, dann Base64.
- Nach korrektem Code: Code in localStorage (`LH_NS+'funkcodes'`), Seite lädt neu, Woche wird vor dem Funkcode-Reiter eingefügt; payload-js läuft bei DOMContentLoaded (quizFeedback etc. dort ergänzen).
- Funk-Chat-Zustand: `funk_on`, `funk_step`, `funk_log` (mit LH_NS); FSTEPS-Array im KRISENSTAB-Script – für neue Wochen eigene Schritte/Chatfiguren ergänzen.
