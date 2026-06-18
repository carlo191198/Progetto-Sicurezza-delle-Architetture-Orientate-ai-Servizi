# Progetto Sicurezza delle Architetture Orientate ai Servizi

**1- DESCRIZIONE DEL PROGETTO:**

Questo progetto implementa un sistema di monitoraggio degli accessi basato su OAuth2 e Keycloak in grado di rilevare automaticamente possibili comportamenti sospetti. 
In particolare, il sistema simula diversi scenari di autenticazione (legittimi e malevoli), e genera notifiche quando vengono rilevati comportamenti sospetti riconducibili ad attacchi di tipo brute force o tentativi di accesso ripetuti non autorizzati.

**2- PASSI PER L'INSTALLAZIONE:**

- Prima di eseguire il progetto è necessario aver installato Python e Docker Desktop.

- All'interno della cartella del progetto è presente il file: "docker-compose.yml".
Per avviare Keycloak eseguire nel terminale il comando: "docker compose up -d" e successivamente, cercare su un browser qualsiasi l'indirizzo
"http://localhost:8080". 

- In questo momento bisogna configurare Keycloak, pertanto bisogna accedere alla Administration Console con le credenziali configurate nel Docker, ovvero: 
Username: admin / Password: admin .
Dopodiché bisogna creare il Realm denominato "security-demo". Successivamente occore configurare un Client OAuth2 chiamato "python-client", abilitando le opzioni "Client Authentication" e "Direct Access Grants", le quali risultano essere necessarie per consentire all'app di Python di effettuare richieste di autenticazione verso il server. 
Una volta terminata la configurazione del client, bisogna creare un utente di test (testuser) ed assegnarli una password permanente, che verrà utilizzata durante le simulazioni delle autenticazioni (nel mio caso username: testuser, password: password123).
Il valore presente nella voce "Client Secret" (generato da Keycloak) deve essere copiato all'interno del file "main.py", sostituendo il valore della costante "CLIENT_SECRET". 

**4-** Una volta completate tutte le operazioni indicate precedentemente, è possibile eseguire il progetto direttamente su un editor di codice sorgente (Visual Studio Code nel mio caso).
  
**3- DIPENDENZE:**
In questo progetto sono state utilizzate le seguenti tecnologie:
- Python (una versione uguale o superiore alla 3, nel mio caso 3.10); 
- Docker Desktop;
- Keycloak;
- OAuth2;
- JWT (JSON Web Token).

Inoltre, sono state utilizzate esclusivamente librerie Python standard, quindi non è necessario installare ulteriori pacchetti aggiuntivi tramite pip. 

**4- ARCHITETTURA:**
L'architettura del mio progetto è composta essenzialmente da due componenti principali:

**- Keycloak:** Keycloak svolge il ruolo di Authorization Server ed Identity Provider, pertanto le sue funzioni principali sono: 
- Gestione degli utenti;
- Verifica delle credenziali;
- Generazione dei token JWT.

**- Python:** Tramite un editor di codice sorgente (Visual Studio Code), con Python è stato possibile: 
- Inviare richieste di autenticazione a Keycloak tramite OAuth2;
- Registrare tutti i tentativi di accesso;
- Distinguere le autenticazioni effettuate con successo da quelle fallite;
- Generare alert in presenza di attività sospette.

**5- TEST DI SICUREZZA:** 
Per verificare il corretto svolgimento e funzionamento del sistema, sono stati simulati ed eseguiti tre scenari differenti: 

**-Test 1 - Autenticazione Valida:** È stato effettuato un login utilizzando le credenziali corrette. 
- Risultato atteso: Autenticazione riuscita e ricezione di un token JWT.
- Esito del test: Superato.

**-Test 2 - Attacco Brute Force:** Sono stati simulati diversi tentativi di autenticazione falliti provenienti dallo stesso indirizzo IP.
- Risultato atteso: Rilevamento automatico dell'attacco e generazione di un alert di sicurezza.
- Esito del test: Superato.

**-Test 3 - Attacco ad un Account:** Sono stati simulati più tentativi di autenticazione falliti verso lo stesso utente utilizzando password differenti.
- Risultato atteso: Identificazione del comportamento anomalo e generazione di un alert.
- Esito del test: Superato.
