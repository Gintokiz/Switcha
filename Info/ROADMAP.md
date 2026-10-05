# 📌 Roadmap e Lista Attività - Switcha (Piattaforma di Baratto Prestazioni)

> **Versione Estesa** - Guida passo-passo per lo sviluppo di un'applicazione web semplice, compatta e funzionale per lo scambio occasionale di servizi senza l'uso di denaro.

---

## 🚀 Fase 1: Configurazione Iniziale e Struttura Progetto

- [ ] **1.1 Definizione Architettura**
  - [ ] Strutturazione della cartella di progetto (`frontend/` e `backend/`)
  - [ ] Inizializzazione repository Git e configurazione file `.gitignore`
- [ ] **1.2 Setup Ambiente di Sviluppo**
  - [ ] Inizializzazione `package.json` ed installazione dipendenze base
  - [ ] Configurazione server di sviluppo locale
- [ ] **1.3 Modellazione e Schema del Database**
  - [ ] Tabella `Utenti` (ID, Nome, Email, Password Hash, Bio, Avatar, Rating Medio, Data Creazione)
  - [ ] Tabella `Annunci` (ID, UtenteID, Titolo, Descrizione, Servizio Offerto, Servizio Cercato, Categoria, Stato [Attivo/In Trattativa/Concluso], Data)
  - [ ] Tabella `Proposte / Interessi` (ID, AnnuncioID, UtenteRichiedenteID, Stato [In Attesa/Accettata/Rifiutata])
  - [ ] Tabella `Messaggi / Chat` (ID, PropostaID, MittenteID, Testo, DataInvio, Letto)
  - [ ] Tabella `Recensioni` (ID, ScambioID, DaUtenteID, AUtenteID, Voto [1-5], Commento, Data)

---

## 👤 Fase 2: Autenticazione e Gestione Profilo Utente

- [ ] **2.1 Sistema di Autenticazione**
  - [ ] Form di Registrazione utente (con validazione campi)
  - [ ] Form di Login con generazione Token/Sessione
  - [ ] Logout e gestione stato utente autenticato
- [ ] **2.2 Profilo Utente**
  - [ ] Visualizzazione del proprio profilo (Informazioni personali, foto, competenze offerte/cercate)
  - [ ] Modifica profilo (aggiornamento bio, avatar, contatti)
  - [ ] Visualizzazione profilo pubblico di altri utenti (con lista recensioni ricevute)

---

## 📋 Fase 3: Bacheca Annunci (Feed Principale)

- [ ] **3.1 Creazione e Pubblicazione Annuncio**
  - [ ] Form per pubblicare un annuncio: _Cosa offro_ vs _Cosa cerco in cambio_ (es. "Sessione Fotografica 📸 in cambio di Logo/Favicon 🎨")
  - [ ] Assegnazione categoria e tag (es. Fotografia, Grafica, Riparazioni, Ripetizioni, Web Design)
- [ ] **3.2 Visualizzazione e Ricerca Bacheca**
  - [ ] Grid/Lista degli annunci attivi con card sintetiche
  - [ ] Filtro per categoria e barra di ricerca per parola chiave
  - [ ] Pagina o modale di dettaglio dell'annuncio singolo
- [ ] **3.3 Interazione "Sono Interessato"**
  - [ ] Pulsante **"Sono Interessato"** sulla scheda annuncio
  - [ ] Notifica o invio proposta al proprietario dell'annuncio
  - [ ] Cambio di stato dell'annuncio o apertura trattativa

---

## 💬 Fase 4: Chat e Trattativa tra Utenti

- [ ] **4.1 Sistema di Messaggistica**
  - [ ] Apertura stanza di chat dedicata tra il proponente dell'annuncio e l'utente interessato
  - [ ] Invio e visualizzazione messaggi per chiarimenti sullo scambio
  - [ ] Elenco delle conversazioni/trattative attive nella sezione messaggi
- [ ] **4.2 Chiusura e Conferma dello Scambio**
  - [ ] Pulsante **"Concludi Scambio"** condiviso tra le parti
  - [ ] Conferma dell'avvenuto scambio senza transazioni in denaro
  - [ ] Aggiornamento dello stato dell'annuncio a _Concluso_

---

## ⭐ Fase 5: Valutazione e Recensioni

- [ ] **5.1 Rilascio Feedback**
  - [ ] Modale/Form automatico a fine scambio per lasciare una valutazione (da 1 a 5 stelle + commento scritto)
  - [ ] Controllo per consentire la recensione solo agli utenti che hanno concluso uno scambio effettivo
- [ ] **5.2 Visualizzazione Recensioni**
  - [ ] Calcolo e ricalcolo automatico della media punteggio dell'utente
  - [ ] Sezione recensioni visibile nella pagina profilo pubblico di ciascun utente

---

## 🎨 Fase 6: UI/UX, Design e Responsive

- [ ] **6.1 Stile Visivo Curato e Moderno**
  - [ ] Definizione palette colori (toni moderni, scuro/chiaro elegante)
  - [ ] Componenti UI puliti (Card annunci con badge, modali fluide, pulsanti d'azione visibili)
  - [ ] Animazioni e micro-interazioni (hover su card, notifiche toast)
- [ ] **6.2 Adattabilità Mobile (Responsive)**
  - [ ] Layout fluido per smartphone, tablet e desktop
  - [ ] Menu di navigazione mobile-friendly

---

## 🧪 Fase 7: Testing, Sicurezza e Deployment

- [ ] **7.1 Validazione e Sicurezza**
  - [ ] Sanificazione degli input per prevenire XSS ed SQL Injection
  - [ ] Protezione delle rotte API riservate (solo utenti autenticati)
- [ ] **7.2 Testing Funzionale**
  - [ ] Test completo del flusso: _Registrazione ➡️ Pubblicazione Annuncio ➡️ Richiesta ➡️ Chat ➡️ Conclusione Scambio ➡️ Recensione_
- [ ] **7.3 Messa in Produzione (Deploy)**
  - [ ] Pubblicazione del Frontend e del Backend su piattaforma cloud gratuita o a basso costo
  - [ ] Verifiche finali in ambiente di produzione live
