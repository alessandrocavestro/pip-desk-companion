# Dipendenze e attribuzioni

Questo file distingue i contributi PIP dai componenti esistenti. Non applicare la licenza del case a librerie, font, toolchain o certificati.

| Componente | Versione di riferimento | Origine / condizioni |
|---|---|---|
| Arduino core ESP32 | 3.0.5 | https://github.com/espressif/arduino-esp32/tree/3.0.5 - core LGPL-2.1-or-later, con componenti sotto licenze proprie |
| GFX Library for Arduino | 1.4.9 | https://github.com/moononournation/Arduino_GFX/tree/v1.4.9 - avviso BSD del progetto, `licenses/BSD-Arduino-GFX.txt` |
| SensorLib | 0.2.1 | https://github.com/lewisxhe/SensorsLib - MIT, `licenses/MIT-SensorLib.txt` |
| cJSON | Dal core ESP-IDF del pacchetto ESP32 | https://github.com/DaveGamble/cJSON - MIT, `licenses/MIT-cJSON.txt` |
| Glifi raster da Liberation Sans | Font di riferimento dello sviluppo | SIL OFL 1.1, `licenses/OFL-Liberation.txt`; i dati dei glifi in `PipFonts.h` restano sotto OFL |
| Open-Meteo | API meteo e geocoding | https://open-meteo.com/ - dati CC BY 4.0; condizioni API separate, https://open-meteo.com/en/terms |
| Certificati CA pubblici in PipTrust.h | Copia incorporata | Materiale pubblico delle autorità emittenti, usato per verificare HTTPS; nessuna chiave privata inclusa |

Le librerie si installano dai rispettivi gestori e non sono rivendicate come opere originali di PIP. Questa consegna per il download distribuisce i sorgenti originali e le istruzioni di compilazione; **non distribuisce un'immagine binaria che incorpori il core/SDK**. I binari di prova per il titolare sono separati dal pacchetto pubblico. Un futuro installer binario richiederà anche il pacchetto di redistribuzione delle dipendenze, con sorgenti e possibilità di ricollegamento dove richiesti dalle rispettive licenze.

Non sono inclusi firmware proprietari di ripristino Waveshare, dump di memoria, credenziali Wi-Fi, ID di calendario, chiavi o servizi privati del costruttore.
