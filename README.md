# Simulatore RAL → Netto

Calcolatore che, data una retribuzione annua lorda (RAL), mostra quanto resta netto in busta paga — mese per mese, con ogni trattenuta spiegata passo per passo (contributi INPS, IRPEF, addizionali regionale e comunale).

**Prova il calcolatore**: https://teotasso-wq.github.io/simulatore-ral-netto/

## Cosa fa

- Copertura di **tutti i 7.896 comuni e le 21 regioni/province autonome italiane**, non solo un caso singolo
- Selettore CCNL (Commercio, Metalmeccanici) che precompila la RAL dal minimo tabellare del livello scelto
- Gestione figli a carico (detrazioni 21-29 anni, nota informativa separata sull'Assegno Unico per gli under 21)
- **Comparatore RAL**: "prendo X, mi offrono Y, quanto cambia il netto?" — utile per valutare un'offerta di lavoro
- Ogni voce di calcolo è etichettata come `verificato` (fonte ufficiale letta direttamente) o `stimato` (fonti secondarie concordanti), mai presentata come certa se non lo è

## Fonti dei dati

- Addizionale comunale e regionale IRPEF: **Dipartimento delle Finanze (MEF)**, elenchi ufficiali 2025/2026, scaricati e verificati incrociando due formati (CSV e PDF) per ogni comune
- Scaglioni IRPEF, detrazioni, contributi INPS: normativa 2026 (L. 199/2025, L. 207/2024), verificata via ricerca web il 14 agosto 2026
- Dettaglio completo delle fonti e delle semplificazioni applicate: in fondo alla pagina del calcolatore stesso

## Come è fatto

Un solo file HTML (nessun framework, nessuna build), che carica 4 file JSON di dati al volo:

| File | Contenuto |
|---|---|
| `index.html` | Pagina e motore di calcolo |
| `comuni-addizionale.json` | Addizionale comunale per tutti i comuni italiani |
| `regioni-addizionale.json` | Addizionale regionale per tutte le regioni |
| `albero-geografico.json` | Indice Regione → Provincia → Comune per le tendine a cascata |
| `ccnl-tabelle.json` | Tabelle minime CCNL Commercio e Metalmeccanici |

## Limiti dichiarati

Prototipo dimostrativo, non sostituisce un cedolino reale né la consulenza di un consulente del lavoro. L'elenco completo delle semplificazioni applicate (es. reddito complessivo approssimato con la sola RAL, nessuna proporzione per assunzioni infra-annuali) è visibile in fondo alla pagina del calcolatore.
