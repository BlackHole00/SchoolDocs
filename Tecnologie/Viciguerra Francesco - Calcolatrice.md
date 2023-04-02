# Consegna
Creare un'applicazione android che consenta di:
- Risolvere un'espressione matematica con operazioni elementari e parentesi.
- Mostrare l'andamento di una funzione in un grafico.
Ulteriori punti da considerare:
- Utilizzare il minimo ammontare di codice esterno e di librerie aggiuntive

# Ipotesi
Durante la creazione del progetto sono stati ipotetizzati i seguenti punti:
- l'espressione analizzata deve essere matematicamente valida. Le seguenti espressioni, che possono essere considerate casi limite. devono essere gestibili e calcolabili senza errori:
	- mancanza dell'operatore di moltiplicazione:
		- `8(3 + 2)`
		- `(2 + 3)(3 + 2)
		- `8x`
		- `(3 + 2)x2`
	- casi particolari di precedenza:
		- `-3^2`, _risultato: -9_
		- `(-3)^2`, _risultato: 9_
		- `-x^2`, _valutato come: -(x^2)_
		- `(-x)^2`
- l'espressione analizzata è in 