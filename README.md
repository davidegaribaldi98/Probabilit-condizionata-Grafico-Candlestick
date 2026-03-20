# Probabilit-condizionata-Grafico-Candlestick
Con questo progetto si persegue l'obiettivo di ottenere, per ogni candela del grafico a candele, in ogni time-frame e per ogni ticker selezionato. Le modalità di calcolo della probabilità sono elencate successivamente.

Le modalità di calcolo della probabilità condizionata si basano su questi principi:
    a) Le candele prese come campione (quelle sulla quale si basano gli studi di probabilità) sono pari ad almeno 800 (questo è il numero di osservazioni campionarie);
    b) La probabilità si pone di rispondere alla domanda: "dato il comportamento pregresso delle nostre osservazioni, quando le ultime k osservazioni sono distribuite come si nota, qual è la probabilità che la candela seguente sia rialzista?";
    c) Per rispondere alla domanda occorre effettuare più calcoli, in particolare:
          c.1) la dimensione campionaria sulla quale si basa lo studio è pari a 800 osservazioni;
          c.2) La probabilità si basa su n osservazioni che precedono l'ultima osservazione, le k osservazioni
        sono n, cioè, n è il numero di k osservazioni precedenti a quella attuale. Sia n=5 allora: n1 calcolerà la probabilità che la prossima osservazione sia ribassista date le ultime k=3 osservazioni (in poche parole, controllo all'interno del campione corrisposto da 800 osservazioni la direzione della candela successiva. Cioè, controllo per ogni k appartenente al campione le 3 osservazioni che la precedono e calcolo la probabilità che questa sia positiva basandomi sulla candela che ha succeduto la serie), proseguo con lo stesso calcolo per n2 e n3. in n1 K=3 in n2 k=5 e in n3 k=8
        c.3) calcolo della probabilità:
        sia 1: candela positiva e -1: candela negativa, allora P(X=1)=P(X=1\x_n1)*w1+P(X=1\x_n2)*w2+P(X=1\x_n3)*w3 dove n1= 3 obs precedenti; n2= 5 obs precedenti; n3= 8 obs precedenti; w1, w2 e w3 sono i pesi dati alle probabilità.
        c.4) quando calcolo la probabilità devo pesarla in quanto la probabilità che si basa sulle 3 obs precedenti peserà meno rispetto a quella che si basa sulle 5 obs e sulle 10 obs. il peso è calcolato come wk​=nk/∑​nk;​​
  d) siccome basarsi solamente su una funzione di probabilità che viene calcolata tenendo conto del numero di volte nelle quali la candela successiva è positiva sulla numerosità campionaria, il risultato non è molto attendibile, inserisco il metodo di Laplace che la calcola come numero di successi + il parametro di smoothing sulla numerosità campionaria + due volte il parametro di smoothing. il parametro di smoothing è pari a α=0,87
