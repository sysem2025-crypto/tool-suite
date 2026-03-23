# Tool Suite — Utility Tecniche Interne

Dashboard di accesso agli strumenti tecnici interni. Deployabile su GitHub Pages senza configurazione.

## Struttura

```
/
├── index.html              # dashboard principale
├── dlms_cosem_gdm.html     # verifica DLMS/COSEM GdM (UNI/TS 11291-14-2)
├── README.md
└── (nuovi strumenti qui)
```

## Deploy su GitHub Pages

1. Crea un repository su GitHub (es. `mia-azienda/tools`)
2. Carica tutti i file nella root del repository
3. Vai su **Settings → Pages → Source** e seleziona `main / (root)`
4. Il sito sarà disponibile su `https://tuonome.github.io/tools/`

## Aggiungere un nuovo strumento

1. Aggiungi il file HTML nella root (es. `nuovo_tool.html`)
2. In `index.html`, copia e adatta una card esistente nella griglia corrispondente
3. Aggiorna i tag `data-tags` per la ricerca

### Template card attiva

```html
<a href="nuovo_tool.html" class="tool-card" data-tags="parole chiave ricercabili">
  <div class="tc-header">
    <div class="tc-icon generic">◆</div>
    <div class="tc-meta">
      <div class="tc-title">Nome strumento</div>
    </div>
    <span class="tc-arrow">↗</span>
  </div>
  <div class="tc-desc">Descrizione breve dello strumento e del suo scopo.</div>
  <div class="tc-footer">
    <span class="tag t-active">Attivo</span>
    <span class="tag t-norm">Riferimento normativo</span>
    <span class="tc-updated">v1.0</span>
  </div>
</a>
```

### Template card WIP (in sviluppo)

```html
<div class="tool-card wip">
  <div class="tc-header">
    <div class="tc-icon generic">◌</div>
    <div class="tc-meta">
      <div class="tc-title">Nome strumento</div>
    </div>
  </div>
  <div class="tc-desc">Descrizione strumento in sviluppo.</div>
  <div class="tc-footer">
    <span class="tag t-wip">In sviluppo</span>
  </div>
</div>
```

## Personalizzare il logo aziendale

Nel file `index.html`, trova il blocco `.logo-area` e sostituisci il contenuto di `.logo-placeholder` con il tuo logo:

```html
<!-- SVG inline -->
<div class="logo-placeholder">
  <img src="logo.svg" alt="Logo" style="width:28px;height:28px">
</div>
<div class="company-name">NOME AZIENDA</div>
```

## Stato e persistenza

Ogni strumento salva il proprio stato nel `localStorage` del browser.  
Il flusso consigliato per il team:

| Azione | Come |
|--------|------|
| Salvataggio automatico | Ad ogni modifica (localStorage) |
| Condivisione stato | Pulsante **Esporta JSON** → manda il file al collega |
| Ripristino stato | Pulsante **Importa JSON** |
| Reset completo | Pulsante **Reset dati** (chiede conferma) |
