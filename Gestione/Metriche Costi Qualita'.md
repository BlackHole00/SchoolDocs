# Metriche
Le **metriche del software** sono strumento che forniscono misure quantitative del prodotto e delle sue componenti. Esse sono importante sia dal **punto di vista del produttore** che da quello **dell'utilizzatore finale**.

Le metriche vengono utilizzate per qualificare e quantificare:
- **i prodotti dell'ingegneria del software**: progetti, sorgenti e casi di test
- **i processi dell'ingegneria del software**: attivita'di analisi, progettazione e codifica
- **gli "attori" del software**: efficienza collaudatori e progettisti.

Le metriche vengono divise in piu'tipi:
- **metrica primitiva**: anche detta diretta,
- **metrica calcolata**: anche detta indiretta,

Oltre alla tipologia, le metriche vengono anche divise in piu'gruppi:
- **metriche del prodotto**
- **metriche di processo**
- **metriche di qualita'**

**Mole di software**: quantita'di software da produrre. Misurato in *tempo/persona* (quindi *giorni/uomo*). Utilizzato per stimare la quantita'di lavoro.
**linee di codice (LOC)**: *primo* metodo di misura per la valutazione della quantita' del software. Piu'semplice. Comprende il alternativa:
	- *Non Comment LOC (NLOC),*
	- *Non Comment Non Blanck (NCNB)*
	- *Solo Commenti (CLOC)*
	- *Solo Codice Eseguibile (EXEC)*

**Funtion Points (FP)**: metodo alternativo per la valutazione della quantita'di lavoro. Da questi ultimi e'possibile ottenere le *linee di codice (LOC)*. Introdotto da *Allan Albrecht* nel 1979, per rendere piu'adeguate le stime create utilizzando solo le LOC. Tiene conto di nuovi linguaggi e tecniche di programmazione (assembly comincia ad non essere l'unico linguaggio). Si basa sull'analisi del software dal punto di vista della richiesta dell'utente, analizzando le *features* che un programma deve fornire, senza analizzare il late tecnico.

- 