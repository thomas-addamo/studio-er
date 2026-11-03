# Studio ER

**Editor di diagrammi Entità-Relazione che funziona nel browser, senza installare niente.**

Un progetto di **Thomas Addamo** · [thoadd.com](https://thoadd.com)

**▶ Apri Studio ER:** https://thomas-addamo.github.io/studio-er/

Studio ER serve a disegnare schemi ER per la progettazione di basi di dati. Si usa notazione **Batini** (quella dei libri di Atzeni et al.) oppure **Chen**. Il programma controlla gli errori più comuni e traduce il diagramma nello schema logico relazionale e in SQL. È pensato per chi studia basi di dati: apri la pagina e inizi a disegnare.

---

## Indice

- [Funzionalità](#funzionalità)
- [Come si usa](#come-si-usa)
- [Regole automatiche](#regole-automatiche)
- [Scorciatoie da tastiera](#scorciatoie-da-tastiera)
- [Salvataggio e formato dei file](#salvataggio-e-formato-dei-file)
- [Privacy](#privacy)
- [Usarlo in locale o modificarlo](#usarlo-in-locale-o-modificarlo)
- [Autore e contributi](#autore-e-contributi)
- [Licenza](#licenza)

---

## Funzionalità

### Disegno
- **Entità** ed **entità deboli**, **relazioni** e **relazioni identificanti**
- **Attributi**:
  - chiave, chiave parziale e identificatore esterno
  - multivalore, derivati, facoltativi
  - composti, con sotto-attributi
- **Generalizzazioni (ISA)** con copertura totale/parziale ed esclusiva/sovrapposta
- **Cardinalità** `(min,max)` oppure `1 / N / M`, partecipazione totale e **ruoli** per le relazioni ricorsive
- **Note** di testo sul foglio

### Due notazioni
- **Batini** (predefinita):
  - attributi a "lecca-lecca"
  - identificatore con pallino pieno, o con barra per quelli composti ed esterni
  - cardinalità degli attributi come (0,1) e (1,N)
  - generalizzazioni con freccia piena o vuota
- **Chen**: attributi a ellisse, chiavi sottolineate, doppi bordi per entità deboli e attributi multivalore.

Si passa dall'una all'altra con il selettore in alto, senza perdere niente.

### Controllo e traduzione
- **Verifica del modello**: segnala chiavi mancanti, cardinalità vuote o scritte male, relazioni con una sola entità, attributi scollegati, generalizzazioni incomplete e nomi duplicati.
- **Schema logico**: traduce il diagramma in tabelle relazionali, con chiavi primarie, chiavi esterne e vincoli di integrità referenziale.
- **SQL**: genera le istruzioni `CREATE TABLE`, da copiare o scaricare come `.sql`.
- **Copia in Markdown**: copia lo schema logico in Markdown, con la chiave primaria sottolineata e le chiavi esterne in corsivo.

### Lavoro comodo
- Annulla e ripeti (fino a 150 passi), copia, incolla e duplica
- Zoom, griglia con aggancio e adattamento del diagramma alla finestra
- Tema chiaro e scuro
- Funziona anche su tablet e telefono: pinch per lo zoom, trascinamento con il dito

---

## Come si usa

1. **Crea un'entità**: fai doppio clic su un punto vuoto del foglio, oppure premi `E` e clicca.
2. **Dalle un nome**: scrivi e premi Invio. Puoi rinominare in qualsiasi momento con un doppio clic.
3. **Aggiungi gli attributi**: seleziona l'entità e usa **+ Attributo** o **+ Chiave** nel pannello a destra. In alternativa premi `A` e clicca sull'entità.
4. **Crea una relazione**: premi `R` e clicca sul foglio.
5. **Collega**: premi `C`, poi clicca la relazione e l'entità.
6. **Imposta le cardinalità**: seleziona il collegamento e scegli la cardinalità nel pannello.
7. **Controlla**: apri la scheda **Verifica** e correggi quello che segnala.
8. **Traduci**: la scheda **Schema logico** mostra le tabelle e il codice SQL.

Per un esempio pronto, il primo avvio carica un piccolo schema di una scuola, che puoi modificare o cancellare con **Nuovo**.

---

## Regole automatiche

Studio ER applica da solo alcune convenzioni, così il diagramma resta ordinato e uniforme.

| Regola | Cosa succede |
| --- | --- |
| **Nomi delle entità** | Diventano tutti MAIUSCOLI: `Studente` → `STUDENTE` |
| **Nomi degli attributi** | Diventano tutti minuscoli: `DataNascita` → `datanascita` |
| **Spazi** | Diventano underscore: `data di nascita` → `data_di_nascita` |
| **Lettere accentate** | Perdono l'accento: `città` → `citta` |
| **Disposizione degli attributi** | Ogni nuovo attributo nasce vicino all'entità. Tutti gli attributi si dispongono in colonna o in riga, sui lati liberi dai collegamenti, con le chiavi per prime. |
| **Trascinamento** | Spostando un'entità o una relazione si spostano anche i suoi attributi |
| **Cancellazione** | Eliminando un'entità o una relazione si eliminano anche i suoi attributi. Se serve, Ctrl+Z la recupera. |
| **Cardinalità** | Sono scritte accanto all'entità a cui si riferiscono |

Le regole sui nomi valgono mentre scrivi e anche per i progetti che apri. I nomi delle relazioni e delle note restano come li scrivi. Se trascini a mano un singolo attributo, resta dove lo lasci finché non aggiungi un nuovo attributo alla stessa entità.

---

## Scorciatoie da tastiera

| Tasto | Azione |
| --- | --- |
| `V` · `H` | Seleziona · sposta la vista (anche tenendo premuto Spazio) |
| `E` · `W` · `R` | Entità · entità debole · relazione |
| `A` · `G` · `N` | Attributo · generalizzazione · nota |
| `C` | Collega due elementi |
| Doppio clic | Rinomina; sul vuoto crea un'entità |
| `Invio` / `F2` | Rinomina l'elemento selezionato |
| Frecce | Spostano la selezione (con `Shift` di un passo più lungo) |
| `Canc` / `Backspace` | Elimina |
| `Esc` | Annulla il collegamento, torna allo strumento di selezione, deseleziona |
| `Ctrl Z` · `Ctrl Shift Z` / `Ctrl Y` | Annulla · ripeti |
| `Ctrl C` · `Ctrl X` · `Ctrl V` · `Ctrl D` | Copia · taglia · incolla · duplica |
| `Ctrl A` | Seleziona tutto |
| `Ctrl S` · `Ctrl O` · `Ctrl E` | Salva il progetto · apri · esporta l'immagine |
| `+` · `-` · `0` · `F` | Zoom avanti · zoom indietro · zoom 100% · adatta alla finestra |

Su Mac usa `Cmd` al posto di `Ctrl`.

---

## Salvataggio e formato dei file

- **Salvataggio automatico**: il lavoro si salva da solo nel browser e lo ritrovi alla riapertura della pagina.
- **Salva progetto** (`Ctrl S`): scarica un file `.json` con tutto il diagramma.
- **Apri** (`Ctrl O`): carica un file `.json`. Puoi anche trascinarlo direttamente sul foglio.
- **Esporta immagine** (`Ctrl E`):
  - formato **PNG** (da 1× a 4×) o **SVG**
  - sfondo bianco, scuro o trasparente

Il file `.json` è leggibile e ha questa forma:

```json
{
  "app": "studio-er",
  "version": 1,
  "name": "Nome del progetto",
  "nodes": [
    { "id": "n1", "type": "entity", "label": "STUDENTE", "x": 200, "y": 300 },
    { "id": "n2", "type": "attribute", "label": "matricola", "x": 300, "y": 300, "key": true }
  ],
  "edges": [
    { "id": "e1", "from": "n1", "to": "n2", "card": "", "total": false, "role": "" }
  ]
}
```

I tipi di nodo sono `entity`, `relationship`, `attribute`, `isa` e `note`.

---

## Privacy

Studio ER non ha server, account o tracciamento: tutto avviene nel tuo browser.
- I diagrammi restano sul tuo dispositivo, nel salvataggio automatico del browser o nei file che scarichi.
- L'unica risorsa esterna sono i caratteri IBM Plex, caricati da Google Fonts.

---

## Usarlo in locale o modificarlo

Tutta l'applicazione è in un solo file, `index.html` (HTML, CSS e JavaScript, senza librerie e senza passaggi di compilazione).

Per usarlo senza internet basta aprire `index.html` nel browser. Per lavorarci con un piccolo server locale:

```bash
python3 -m http.server 8000
```

poi apri http://localhost:8000.

Il sito pubblico è servito da **GitHub Pages** a partire dal ramo `main`: ogni modifica pubblicata su `main` va online in meno di un minuto.

---

## Autore e contributi

**Studio ER è un progetto di Thomas Addamo** — [thoadd.com](https://thoadd.com) · GitHub [@thomas-addamo](https://github.com/thomas-addamo).

Hanno contribuito:
- **Daniele Porcaro** ([@dany80213](https://github.com/dany80213)): favicon e copia dello schema logico in Markdown.

Segnalazioni e proposte sono benvenute tramite le *issue* e le *pull request* del repository. Inviando un contributo accetti che venga distribuito con la stessa licenza del progetto.

---

## Licenza

Studio ER è distribuito con la **licenza MIT**.

Copyright © 2026 **Thomas Addamo** ([thoadd.com](https://thoadd.com)). Il testo completo è nel file [`LICENSE`](LICENSE).

### Cosa significa, in breve

| Puoi | A condizione di | Non è previsto |
| --- | --- | --- |
| ✅ Usare Studio ER per qualsiasi scopo, anche a scuola, al lavoro o in prodotti commerciali | 📄 Mantenere l'avviso di copyright con il nome di **Thomas Addamo** e il testo della licenza MIT in tutte le copie o parti sostanziali del codice | ❌ Garanzia di alcun tipo: il software è fornito "così com'è" |
| ✅ Copiare e ridistribuire il codice | | ❌ Responsabilità dell'autore per danni o problemi derivanti dall'uso |
| ✅ Modificarlo e creare opere derivate | | |
| ✅ Distribuire le versioni modificate, anche con un'altra licenza per le tue modifiche | | |

Se usi Studio ER o ne pubblichi una versione modificata, una citazione visibile è gradita, anche se non è obbligatoria oltre a quanto richiesto dalla licenza. Per esempio:

> Basato su Studio ER di Thomas Addamo — thoadd.com

Questo riepilogo serve solo a orientarsi e non sostituisce il testo ufficiale della licenza, che è quello in inglese nel file `LICENSE`.

### Componenti di terze parti

- **IBM Plex Sans / IBM Plex Mono**: caratteri di IBM, distribuiti con la [SIL Open Font License 1.1](https://openfontlicense.org). Sono caricati da Google Fonts e non sono inclusi nel repository.

Il nome "Studio ER" e il logo identificano il progetto di Thomas Addamo. Se pubblichi una versione modificata, usa un nome che non faccia pensare a una versione ufficiale.
