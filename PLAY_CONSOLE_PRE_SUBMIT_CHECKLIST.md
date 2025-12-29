# Play Console – Pre‑Submit Checklist (IT/EN)

Questa checklist serve a evitare rifiuti in review (policy + scheda store) e a mantenere coerenza tra **app**, **Play Console** e **Store Listing**.

---

## 1) Release / build
- [ ] Hai incrementato `versionName` / `versionCode` (Flutter: `pubspec.yaml` `version:`) e generato **un nuovo AAB**.
- [ ] Hai testato la build su device reale o emulatore (almeno: onboarding → feature chiave → logout/exit).
- [ ] Crash-free smoke test (avvio, permessi, feature principale).

---

## 2) Store Listing (Scheda dello Store)
- [ ] **Short description** coerente con le feature reali (no promesse non presenti).
- [ ] **Full description / Descrizione lunga** completa in **tutte le lingue attive**.
- [ ] Se usi API sensibili (es. Accessibility), la descrizione lunga lo dichiara chiaramente.

### Snippet consigliato (EN) – Accessibility Service
> Accessibility Service (optional): To support the “hold volume button for 3 seconds” shortcut, this app can use Android’s Accessibility Service only to detect the shortcut action and start/stop recording. It does not read, collect, or share the content of your screen, typed text, passwords, messages, or any other personal data. You can enable/disable this feature anytime in system settings.

### Snippet consigliato (IT) – Servizio di Accessibilità
> Servizio di Accessibilità (opzionale): per supportare la scorciatoia “tieni premuto il tasto volume per 3 secondi”, l’app può utilizzare il Servizio di Accessibilità di Android solo per rilevare l’azione della scorciatoia e avviare/interrompere la registrazione. Non legge, non raccoglie e non condivide i contenuti mostrati sullo schermo, il testo digitato, password, messaggi o altri dati personali. Puoi attivare/disattivare questa funzione in qualsiasi momento dalle impostazioni di sistema.

---

## 3) Privacy Policy / Data Safety
- [ ] La **Privacy Policy** è pubblicata via URL e linkata correttamente in Play Console.
- [ ] La sezione **Data safety** è aggiornata e coerente con SDK (Ads/Analytics) e comportamento app.
- [ ] Se dichiari “non raccoglie dati”, verifica che non ci siano SDK che raccolgono (Ads/Analytics spesso raccolgono identificatori).

---

## 4) Permessi / API sensibili (high‑risk)
Controlla se usi una di queste (lista non esaustiva):
- Accessibility Service
- All files access / file manager, gestione storage estesa
- SMS / Call log
- VPN
- Install packages / Device admin
- Background location

Per ciascuna:
- [ ] Scopo legittimo, minimo necessario (least privilege).
- [ ] Niente raccolta/trasmissione non necessaria.
- [ ] UI e testi coerenti con la policy.

---

## 5) Accessibility API – requisiti pratici (quando NON sei un’app di accessibilità)
Se usi AccessibilityService per scorciatoie/automazioni:

### 5.1 Prominent disclosure (Informativa ben visibile)
- [ ] Mostrata **prima** di inviare l’utente nelle impostazioni di Accessibilità.
- [ ] Spiega **cosa fa**, **perché serve**, **cosa NON fa** (es. non legge contenuti schermo).
- [ ] Richiede **consenso esplicito** con 2 scelte: **Accetta** / **Rifiuta**.
- [ ] Non è sufficiente “chiudere” la schermata: uscire dal dialog **non** è consenso.

### 5.2 Design corretto
- [ ] La disclosure è **non dismissible** (niente tap fuori / tasto back).
- [ ] Il percorso “Rifiuta” **non** apre le impostazioni e non abilita la feature.
- [ ] Il percorso “Accetta” apre le impostazioni o abilita la feature.

### 5.3 Video dimostrativo (richiesto spesso in Play Console)
Il video deve mostrare:
- [ ] Entrata nel punto dell’app dove si attiva la feature
- [ ] Comparsa della disclosure **prima** delle impostazioni
- [ ] Impossibilità di chiuderla con back/tap esterno
- [ ] Click su **Rifiuta** → nessuna apertura impostazioni
- [ ] Ripeti e click su **Accetta** → apertura impostazioni accessibilità

---

## 6) Play Console – dichiarazioni
- [ ] Sezione “Servizi di accessibilità” compilata (scopo + link video + checkbox richieste).
- [ ] Le risposte su raccolta “dati sensibili” sono coerenti con il comportamento reale.

---

## 7) Ultimi controlli prima di inviare
- [ ] Nessun placeholder (testo/lorem, link vuoti, “TODO”).
- [ ] Screenshot e grafica aggiornati (se richiesti).
- [ ] Note di rilascio (What’s new) coerenti.

---

## Quick template – Prominent disclosure (EN)
Title: Accessibility Service required (optional)
Body: We use Android’s Accessibility Service only to enable the volume-button shortcut (hold for 3 seconds) to start/stop recording. We do not read or collect on-screen content, typed text, passwords, or messages. You can disable this anytime in system settings.
Buttons: Decline / Allow

## Quick template – Informativa ben visibile (IT)
Titolo: Servizio di Accessibilità (opzionale)
Testo: Usiamo il Servizio di Accessibilità di Android solo per abilitare la scorciatoia col tasto volume (pressione prolungata 3 secondi) per avviare/interrompere la registrazione. Non leggiamo né raccogliamo contenuti dello schermo, testo digitato, password o messaggi. Puoi disattivarlo in qualsiasi momento dalle impostazioni di sistema.
Bottoni: Rifiuta / Consenti
