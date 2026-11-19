# Stato delle prove - 1.0.0-rc2

Aggiornato al 19 novembre 2026. **Candidata al rilascio, non versione stabile già collaudata sul dispositivo.**

Il firmware e il kit ZIP non sono stati modificati durante queste prove. La documentazione inclusa nell’archivio è datata 18 novembre; questo file raccoglie anche i risultati successivi.

## Completato

- Quattro fotografie reali del guscio v24 integrate in assets e nella documentazione, con dati privati rimossi e pixel invariati. Guida illustrata PDF inclusa. Le fotografie non attestano la versione firmware.

- Prove fisiche confermate dal costruttore: ora/data e meteo sul display, navigazione con il pulsante; timer avvio/pausa con doppio clic e reset fermo alla durata salvata; reazione alla presa/inclinazione e ritorno al riposo dopo l’appoggio senza animazione continua nei 15 secondi osservati.
- Scadenza di un timer di un minuto verificata via USB: avvio a 60000 ms, termine a 0, fermo e completato, senza panic o riavvii. Durata abituale salvata invariata. Il costruttore conferma la scritta **Fatto.** e il ritorno alla faccina con un clic breve; USB conferma timer fermo e schermata del volto.
- Portale aperto dal telefono e salvataggio rete/città confermati, con Agenda OFF. Wi-Fi/meteo verificati anche dopo un riavvio: città conservata, riconnessione e nuova ricezione meteo automatiche (HTTP200/TLS0). Ora disponibile e resa visiva confermata; nessuna prova separata della sincronizzazione NTP. Nessuna password o chiave letta dal dispositivo.
- Agenda Google end-to-end con il codice pubblico, un progetto Apps Script separato e il calendario principale: distribuzione con accesso in sola lettura, richieste senza chiave respinte, lettura riuscita sul PIP. Confermati sia lo stato vuoto sia l'arrivo automatico di un appuntamento di prova con titolo e orario corretti sul display. Nessun calendario, indirizzo, chiave o titolo privato incluso nel download.
- Durante l'osservazione USB rilevate e recuperate automaticamente due brevi disconnessioni Wi-Fi, di circa due secondi osservati ciascuna. L'Agenda si è aggiornata dopo il recupero, senza riavvio del dispositivo. La prova con router spento per 30 secondi resta da eseguire.
- Prima installazione della candidata Public rc2 sulla scheda V2 del costruttore: quattro regioni scritte con hash verificati, impostazioni personali escluse dalle scritture. Avvio iniziale senza impostazioni pubbliche di rete/città/Agenda, seguito dalla configurazione dal telefono. Queste verifiche non costituiscono una prova di durata.

- Base verificata: gli effettivi sorgenti Studio 1.5, precedenti alla Corsa. Nove file sono identici alla v1.5; gli altri tre contengono gli adattamenti pubblici e la sola correzione movimento riportata. Nessun codice della funzione Corsa incluso.

- Copia per hash dei sette file originali del case v24: 3MF, tre STL, tre STEP. Geometria e impostazioni invariate.
- Case v24: riscontro generale fisico del costruttore “stampato e tutto ok”, 13 novembre 2026. Nessuna nuova stampa dichiarata durante la preparazione del kit pubblico.
- Compilazione completa per Waveshare ESP32-S3-LCD-1.69, ESP32 3.0.5, GFX 1.4.9 e SensorLib 0.2.1. Applicazione circa 1,26 MB, entro la partizione da 1.310.720 byte; RAM globale 48.644 byte nella build di riferimento.
- Test pulsante, timer, intervalli e rollover.
- Test esperienza: riposo, agenda contestuale, ritorno dalle pagine manuali, priorità del timer e reset fermo.
- Test parser agenda: dati validi/non validi, scadenze, UTF-8, eventi e URL.
- Regressione del movimento: traccia da fermo, nuovo orientamento di appoggio, vibrazioni, deriva e riarmo dopo la posa.
- Test aggiuntivo delle etichette calendario dell'edizione pubblica: nomi dell'utente ammessi; etichette troppo lunghe, caratteri di controllo e UTF-8 malformato rifiutati.
- Test locale del servizio Google: calendario principale come default, nessun ID di account preimpostato, unione dei duplicati e confronto della chiave. Test con API simulate, non accesso reale a Google.
- Controllo del pacchetto contro i riferimenti privati noti, includendo i contenuti interni del 3MF. Esclusi log personali, dump, chiavi, calendari e servizio Corsa del costruttore.

## Da completare prima di chiamarla stabile

- Utilizzo prolungato con durata dichiarata e recupero dopo un’interruzione prolungata della rete. Una registrazione di 30 minuti è stata avviata; il suo esito completo non è ancora incluso in questo aggiornamento.
- Aggiungere foto dell’interno aperto e delle parti separate alla guida. Le quattro foto esterne reali sono già integrate e prive di metadati privati.

I test del firmware personale precedente non vengono attribuiti automaticamente alla nuova candidata. Public rc2 è ora caricata sul dispositivo per la prova, con impostazioni in uno spazio separato e ripristino personale conservato privatamente. L'ora valida letta al primo avvio può provenire dal RTC e non dimostra la sincronizzazione internet. Nessuna credenziale del costruttore è nel download.

## Limiti noti della candidata

- **Ora dopo una configurazione lunga.** Il modulo acquisisce l'ora del telefono quando si apre la pagina. Se si salva molto dopo, può impostare un'ora arretrata e l'Agenda può rifiutare i dati recenti. Se succede, ricaricare il modulo e premere subito **Salva impostazioni**; lasciare vuoti password Wi-Fi e chiave Agenda per conservare i valori già salvati. Questa procedura ha risolto il collaudo sul prototipo. Il limite non è stato corretto nel firmware rc2.
- **Durata della pressione.** Per il clic breve premere e rilasciare entro circa mezzo secondo. Il comportamento ereditato dalla base Studio 1.5 ignora le pressioni intermedie di circa 0,8–1,8 secondi; una pressione lunga viene riconosciuta dopo circa 1,8 secondi. Questa gestione non è stata modificata durante il collaudo.
