**Spiegazione degli screenshot**

**1. Terminale:** 
In questa schermata viene mostrato il terminale di Windows PowerShell utilizzato per avviare il progetto. Mediante il comando "dir" è stato possibile verificare la presenza del file "docker-compose.yml" all'interno della cartella e successivamente è stato eseguito il comando "docker compose up -d", il quale ha permesso di scaricare l'immagine di Keycloak, creare il container Docker ed avviare il servizio di autenticazione. 

**2. Configurazione del Client OAuth2:** 
La schermata mostra la sezione "Clients" di Keycloak. Durante questa fase ho configurato il client OAuth2 denominato "python-client", il quale viene utilizzato da Python per inviare le richieste di autenticazione al server Keycloak.

**3. Creazione del Realm:**
In questa schermata è visibile il Realm "security-demo" creato all'interno di Keycloak. Il Realm è stato essenziale poiché rappresenta il dominio di sicurezza all'interno del quale vengono gestiti gli utenti, le credenziali, i ruoli e le varie configurazioni di autenticazione. 

**4. Creazione dell'utente test:**
La schermata mostra l'esistenza dell'utente test denominato "testuser" all'interno della sezione "Users" di Keycloak, il quale viene utilizzato durante i test per verificare il corretto funzionamento del processo di autenticazione tramite OAuth2.

**5. Esecuzione e Risultati del progetto:**
Questa schermata mostra l'output generato dal progetto. Nel primo scenario viene simulato un accesso legittimo con le credenziali corrette. Come si può vedere dalla schermata, l'autenticazione viene eseguita con successo e Keycloak restituisce un token JWT valido. 

Nel secondo scenario vengono simulati sei tentativi di autenticazione falliti provenienti tutti dallo stesso indirizzo IP. Come si può vedere dalla schermata, dopo il superamento della soglia configurata, il sistema rileva automaticamente un possibile attacco di tipo "Brute Force" e genera immediatamente un alert di sicurezza. 

Nel terzo scenario vengono simulati diversi tentativi di accesso fallito verso lo stesso account. Come si può vedere dalla schermata, anche in questo caso il sistema è stato in grado di identificare il comportamento sospetto e genera un alert di sicurezza relativo ad un possibile attacco mirato all'account. 

Infine, viene mostrato un riepilogo dei tentativi di login effettuati, col numero dei login andati a buon fine e quelli falliti. 
