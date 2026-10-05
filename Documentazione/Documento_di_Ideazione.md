# Documento di Ideazione - Progetto Switcha

**Corso di Tecnologie Web (TWeb) - A.A. 2024/2025**
**Nome Progetto**: Switcha (Piattaforma di Scambio Favori e Risorse di Quartiere)
**Tipologia Documento**: Analisi degli Scenari, Attori e Casi d'Uso (2-3 Pagine)

---

## 1. Introduzione e Descrizione dell'Applicazione

**Switcha** è un'applicazione web pensata per promuovere la solidarietà locale e il riuso sostenibile. Permette agli utenti di una medesima comunità urbana o di quartiere di pubblicare ed esplorare annunci di baratto/scambio basati su "Cosa offro" e "Cosa cerco".

L'applicazione elimina qualsiasi transazione economica, concentrandosi sull'impatto **benefit** della tessitura di comunità e della sostenibilità ambientale. L'interfaccia è progettata per essere totalmente responsive, consentendone un utilizzo fluido sia da dispositivi mobili (smartphone e tablet durante gli spostamenti) sia da computer desktop.

---

## 2. Scenari Tipici d'Uso

* **Scenario 1 (Utilizzo Mobile - Smartphone)***Marco*, uno studente fuorisede appena trasferitosi in città, deve montare alcuni mobili nella nuova stanza ma non possiede un avvitatore elettrico. Mentre torna dalle lezioni in autobus, accede a Switcha dallo smartphone per cercare se un vicino di quartiere presti un attrezzo in cambio di lezioni di inglese o ripetizioni di matematica.
* **Scenario 2 (Utilizzo Desktop / Laptop)***Elena*, appassionata di giardinaggio, ha prodotto diverse piantine di pomodoro in esubero nel suo orto urbano. Desidera cederle a qualcuno del quartiere chiedendo in cambio un piccolo aiuto per la manutenzione della sua bicicletta. Accede a Switcha da casa tramite il proprio laptop per inserire un annuncio dettagliato con foto, descrizione e categoria.
* **Scenario 3 (Utilizzo Desktop - Moderazione)**
  *Laura*, membro dello staff di amministrazione della piattaforma, accede al sistema da PC durante le ore d'ufficio per verificare il corretto utilizzo della bacheca, controllare le segnalazioni ed eliminare eventuali annunci fuori tema o inappropriati.

---

## 3. Tipologie di Utilizzatori (Attori Principali)

1. **Utente Standard (`ROLE_USER`)**:
   Rappresenta il cittadino/utente finale. Può esplorare la bacheca, filtrare gli annunci per categoria, pubblicare i propri annunci di scambio, inviare proposte di baratto agli altri utenti, acccettare/rifiutare le proposte ricevute e rilasciare recensioni.
2. **Amministratore (`ROLE_ADMIN`)**:
   Rappresenta il gestore di piattaforma. Ha accesso ad un pannello di controllo riservato per monitorare tutti gli annunci presenti nel sistema ed eventualmente rimuovere quelli non conformi alle regole della community.

---

## 4. Matrice Terzetti "Scenario / Utilizzatore / Obiettivo" e Casi d'Uso

### Terzetto 1: Scenario 1 | Utente Standard (`ROLE_USER`) | Ricerca e Richiesta di Scambio

* **Obiettivo**: Trovare una risorsa/servizio necessario nelle vicinanze e proporre uno scambio.
* **Caso d'Uso 1.1 (UC1 - Consultazione Bacheca e Filtri)**:L'utente entra nell'applicazione, seleziona la categoria desiderata (es. *Fai da te / Attrezzi*) ed esplora gli annunci disponibili visualizzando i dettagli di ciascuna offerta.
* **Caso d'Uso 1.2 (UC2 - Invio Proposta di Scambio)**:
  Dalla scheda dettagliata di un annuncio, l'utente compila un form indicando la propria proposta specifica (cosa offre in cambio) ed invia la richiesta al proprietario dell'annuncio.

### Terzetto 2: Scenario 2 | Utente Standard (`ROLE_USER`) | Offerta e Gestione Scambi

* **Obiettivo**: Pubblicare le proprie disponibilità e gestire i baratti in entrata.
* **Caso d'Uso 2.1 (UC3 - Creazione Nuovo Annuncio)**:L'utente compila il form di inserimento specificando titolo, descrizione, cosa offre, cosa richiede in cambio e la categoria di appartenenza. L'annuncio viene salvato nel server e pubblicato in bacheca.
* **Caso d'Uso 2.2 (UC4 - Gestione Proposte Ricevute e Accettazione)**:
  L'utente accede al proprio profilo per consultare le proposte arrivate per i propri annunci. Può valutarle e decidere di accettarne una, cambiando lo stato dello scambio in "Accettato".

### Terzetto 3: Scenario 3 | Amministratore (`ROLE_ADMIN`) | Moderazione Piattaforma

* **Obiettivo**: Rimuovere annunci inappropriati e mantenere la bacheca sicura.
* **Caso d'Uso 3.1 (UC5 - Moderazione ed Eliminazione Annuncio)**:
  L'amministratore entra nella dashboard riservata, individua un annuncio non conforme o segnalato e lo elimina definitivamente dal database.

---

## 5. Selezione dei Casi d'Uso per l'Implementazione (Proof-of-Concept)

Per la realizzazione del **Proof-of-Concept (PoC)** richiesto dal corso, sono stati selezionati **2 Casi d'Uso principali** che coprono l'intero ciclo operativo dell'applicazione e soddisfano rigorosamente i requisiti tecnici client-side e server-side:

### 1. Caso d'Uso Selezionato #1: *Pubblicazione di un Nuovo Annuncio di Scambio* (UC3)

* **Descrizione del Flusso**:Un utente autenticato compila il form dedicato (**Form POST 1**) fornendo Titolo, Descrizione, Servizio Offerto, Servizio Richiesto e Categoria.
* **Meccanica Tecnico-Implementativa**:
  - **Server-Side**: Invio della richiesta HTTP `POST /api/announcements` verso l'`AnnouncementController`. Validazione e salvataggio nel database H2 tramite `AnnouncementRepository`.
  - **Client-Side**: Gestione dello stato tramite il pattern **Lifting State Up**: il componente `CreateAnnouncementForm` comunica la nuova risorsa al componente genitore `App.tsx`, il quale aggiorna immediatamente lo stato globale della lista annunci. Di conseguenza, il componente fratello `AnnouncementFeed` renderizza subito la nuova scheda senza richiedere il ricaricamento della pagina.

### 2. Caso d'Uso Selezionato #2: *Invio e Accettazione Proposta di Scambio* (UC2 + UC4)

* **Descrizione del Flusso**:Un utente invia una proposta per un annuncio visibile in bacheca (**Form POST 2**). Successivamente, il creatore dell'annuncio consulta le proposte ricevute nel proprio pannello utente e clicca su "Accetta".
* **Meccanica Tecnico-Implementativa**:
  - **Server-Side**: Chiamata `POST /api/proposals` gestita da `ProposalController` per la creazione della proposta. Successiva chiamata `PUT /api/proposals/{id}/status?status=ACCEPTED` per l'aggiornamento dello stato.
  - **Client-Side (Reattività Server-Client)**: L'azione di accettazione di una proposta genera una sincronizzazione simultanea lato client: la proposta cambia stato in `ACCEPTED` nel pannello `UserProfileView`, e contemporaneamente l'annuncio associato visibile nella bacheca globale (`AnnouncementFeed`) aggiorna la propria etichetta di stato da `ACTIVE` a `IN_TRATTATIVA`.
