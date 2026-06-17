# Progetto Sicurezza delle Architetture Orientate ai Servizi

**DESCRIZIONE DEL PROGETTO:**
Questo progetto implementa un sistema di monitoraggio degli accessi basato su OAuth2 e Keycloak in grado di rilevare automaticamente possibili comportamenti sospetti. 
In particolare, il sistema simula diversi scenari di autenticazione (legittimi e malevoli), e genera notifiche quando vengono rilevati comportamenti sospetti riconducibili ad attacchi di tipo brute force o tentativi di accesso ripetuti non autorizzati.

**PASSI PER L'INSTALLAZIONE:**

**1-** Prima di eseguire il progetto è necessario aver installato Python e Docker Desktop.

**2-** All'interno della cartella del progetto è presente il file: "docker-compose.yml".
Per avviare Keycloak eseguire nel terminale il comando: "docker compose up -d" e successivamente, cercare su un browser qualsiasi l'indirizzo "http://localhost:8080". 

***3-** In questo momento bisogna configurare Keycloak, pertanto bisogna accedere alla Administration Console con le credenziali configurate nel Docker, ovvero: 
Username: admin / Password: admin .
Dopodiché bisogna creare il Realm denominato "security-demo". Successivamente occore configurare un Client OAuth2 chiamato "python-client", abilitando le opzioni "Client Authentication" e "Direct Access Grants", le quali risultano essere necessarie per consentire all'app di Python di effettuare richieste di autenticazione verso il server. 
Una volta terminata la configurazione del client, bisogna creare un utente di test (testuser) ed assegnarli una password permanente, che verrà utilizzata durante le simulazioni delle autenticazioni (nel mio caso username: testuser, password: password123).
Importante sottolinare che il valore presente nella voce "Client Secret" (generato da Keycloak) deve essere copiato all'interno del file "main.py", sostituendo il valore della costante "CLIENT_SECRET". 

**4-** Una volta completate tutte le operazioni indicate precedentemente, è possibile eseguire il progetto direttamente su un editor di codice sorgente (Visual Studio Code nel mio caso).

**TECNOLOGIE UTILIZZATE:**
- Python
- OAuth2
- Keycloak
- JWT
- Docker
  
**DIPENDENZE:**
- In questo progetto sono state utilizzate le librerie standard Python, pertanto le uniche dipendenze presenti sono:
- Python (una versione uguale o superiore alla 3.10); 
- Docker Desktop;
- Keycloak 23. 
