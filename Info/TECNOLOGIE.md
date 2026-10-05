# 🛠️ Stack Tecnologico e Strumenti - Switcha

> **Guida alle Tecnologie da Utilizzare e Integrazioni Potenziali** per realizzare una web app per lo scambio di prestazioni occasionali semplice, compatta e funzionale.

---

## 🎯 1. Filosofia del Progetto
- **Semplice**: Codice pulito, poche dipendenze superflue, facilità di manutenzione.
- **Compatto**: Architettura snella, avvio rapido e consumi di memoria contenuti.
- **Funzionale**: Piena reattività per l'utente, chat immediata, bacheca dinamica e sistema di recensioni trasparente.

---

## 🚀 2. Stack Tecnologico Consigliato (Soluzione Principale)

### 🎨 Frontend (Interfaccia Utente)
- **HTML5 & Vanilla JavaScript / React (con Vite)**
  - *Perché*: **Vite + React** garantisce uno sviluppo ultra-veloce, componenti riutilizzabili (Card annuncio, Chat, Profilo, Modale recensione) e gestione reattiva dello stato.
  - *Alternativa ultra-snella*: **Vanilla JS + HTML5** per zero build step e massima leggerezza.
- **CSS3 Moderno (Vanilla CSS con Custom Properties)**
  - *Perché*: Permette di implementare un design unico con temi scuri/chiari, variabili di colore, Flexbox/Grid e micro-animazioni fluide per le interazioni (hover sulle schede, modali).
  - *Alternativa*: **TailwindCSS** per una prototipazione rapida tramite classi utility.
- **Lucide-React / FontAwesome**
  - *Perché*: Set di icone leggere e moderne per identificare categorie (fotografia, grafica, programmazione, ecc.), stelle di valutazione e pulsanti d'azione.

---

### ⚙️ Backend (Server & API)
- **Node.js + Express.js**
  - *Perché*: È il framework backend più diffuso, leggero e veloce da configurare. Gestisce le API RESTful per annunci, utenti, proposte e recensioni.
- **JSON Web Tokens (JWT) + Bcrypt.js**
  - *Perché*: Gestione semplice e sicura dell'autenticazione utente. Le password vengono cifrate con `bcrypt.js` e la sessione viene gestita tramite token JWT.

---

### 🗄️ Database & Storage
- **PostgreSQL (o SQLite in Locale)**
  - *Perché*: Un database relazionale è perfetto per questo progetto in quanto garantisce la corretta associazione tra Utenti, Annunci, Messaggi e Recensioni.
  - *ORM consigliato*: **Prisma ORM** oppure **Sequelize** per interagire con il database scrivendo codice JavaScript sicuro senza SQL grezzo.
- **Multer / Cloudinary (o Storage Locale)**
  - *Perché*: Gestione del caricamento foto profilo degli utenti e di eventuali immagini allegate agli annunci.

---

### 💬 Realtime & Messaggistica (Chat)
- **Socket.io**
  - *Perché*: Permette la comunicazione bidirezionale in tempo reale tra i due utenti interessati allo scambio senza dover ricaricare la pagina.

---

## ⚡ 3. Stack Alternativo "Ultra-Compatto" (BaaS - Backend as a Service)

Se l'obiettivo è ridurre al minimo la quantità di codice backend da scrivere e gestire:

### **Supabase (PostgreSQL + Auth + Realtime + Storage)**
- **Autenticazione Pronta**: Login/Registrazione gestiti out-of-the-box.
- **Database PostgreSQL cloud gratuito**: Tabelle gestibili con interfaccia grafica visuale.
- **Realtime Subscriptions**: La chat in tempo reale funziona direttamente dal client con poche righe di codice.
- **Storage Integrato**: Caricamento immagini avatar/annunci incluso.

> **Consiglio**: Se vuoi la soluzione in assoluto più veloce e compatta, **React + Supabase** permette di avere l'app pronta in un solo repository frontend!

---

## 🔮 4. Tecnologie e Moduli Potenziali (Integrabili in Futuro)

| Categoria | Tecnologia / Libreria | Scopo |
| :--- | :--- | :--- |
| **Notifiche UI** | `SweetAlert2` / `Sonner` / `React-Toastify` | Feedback visivo immediato (es. *"Proposta inviata con successo!"*, *"Scambio concluso!"*) |
| **PWA (Progressive Web App)** | `vite-plugin-pwa` | Rende la web app installabile sullo smartphone come se fosse un'app nativa |
| **Validazione Dati** | `Zod` / `Joi` | Garantisce che i form di creazione annuncio e recensione contengano dati validi |
| **Geolocalizzazione** | HTML5 Geolocation API / Leaflet | Opzionale: mostra gli annunci di scambio più vicini alla posizione dell'utente |

---

## ☁️ 5. Deployment & Hosting (Gratuito / Low-Cost)

- **Frontend**: [Vercel](https://vercel.com) oppure [Netlify](https://netlify.com) *(Deploy automatico da GitHub)*
- **Backend (Express)**: [Render.com](https://render.com) oppure [Railway](https://railway.app)
- **Database Cloud**: [Supabase](https://supabase.com) / [Neon.tech](https://neon.tech)
