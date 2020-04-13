# Relazione primo progetto Interactive 3d Graphics

![final](screenshots/final.gif)

## Descrizione
Come si può notare dall'immagine, la scena rappresenta un faro in funzione di notte in una ambientazione di mare.
Le animazioni implementate sono il movimento della luce del faro e quello della zattera che si avvicina e si allontana alla riva, simulando l'idea della corrente.


## Strumenti utilizzati
- Hardware:
  - CPU: 2,3 GHz Intel Core i5 quad-core
  - Scheda grafica: Intel Iris Plus Graphics 655 1536 MB
- Software:
  - Git
  - Atom
  - Google Chrome
  - Safari


## Realizzazione
Ogni Mesh è stata realizzata manualmente tramite l'editor Atom, in particolare, ogni punto spiegato nel [diario](journal.md) è stato implementato in una diversa cartella nella repository git su un branch diverso dal master (chiamato dev) prima del commit finale che prevede il merge con il master.


## Funzionamento
Il ragionamento con cui si è implementato il codice si basa sul risultato fornito dalla funzione getHeightData fornita di partenza: scorrendo l'array si può disegnare un tipo di terreno diverso e aggiungere il tipo appropriato di vegetazione con una certa probabilità.
Nel punto di altezza viene generato il faro mentre la zattera viene aggiuinta in un punto specifico.
La velocità di movimento dell'animazione della luce del faro dipende dalla velocità di render della pagina, mentre quella della zattera è legata ad un determinato intervallo di tempo.
La vegetazione viene generata dinamicamente a seconda della posizione, della probabilità di esserci o meno, nonchè le sue dimensioni e rotazione sull'asse y dipendono da un valore casuale generato ad ogni chiamata della rispettiva funzione.


## Ottimizzazione
Si è cercato di ottimizzare l'efficenza del codice cercando di dimunire il numero delle facce generate, in particolare:
- vengono rimosse le facce non necessarie nel perimetro;
- dei punti interni del terreno vengono sempre generati:
  - il cubo relativo all'altezza corretta senza la faccia inferiore,
  - la faccia inferiore del cubo nel punto più basso e,
    - se il punto si trova sotto al livello del mare la faccia superiore dell'acqua alla giusta altezza,
    - se si trova sopra al livello del mare le facce laterali di un cubo sottostante per evitare "buchi".

L'ottimizzazione viene fornita anche a livello di vegetazione, faro e zattera.

Nonostante questi accorgimenti, il codice risulta comunque abbastanza lento, la causa però non può essere attribuita solo al numero di facce generate, ma anche alla generazione delle ombre della luce del faro.
