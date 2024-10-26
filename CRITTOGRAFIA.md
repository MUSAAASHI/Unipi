# **CRITTOGRAFIA**
### **CIFRARI A CHIAVE SEGRETA (simmetrici)**
- la chiavi di cifratura è uguale a quella di decifratura o facilmente calcolabile  
  
### **CIFRARI A CHIAVE PUBBLICA (asimmetrici)**
- le operazioni di cifratura e decifratura sono *diverse e pubbliche*:
    - <mark style= "background-color: #98FB98">**k[pub]** &rarr; cifratura   **c = C(m, k[pub])**
    - <mark style= "background-color: #98FB98">**k[prv]** &rarr; decifratura   **m = D(c, k[prv])**  
- Esiste una coppia **<k[pub], k[prv]>** per ogni utente del sistema
- D è nota a tutti ma la la chiave no (_computazionalmente difficile_)
- C (One-way trap-door)
- "Tutti gli utenti possono inviare messaggi allo stesso destinatario (rouli diversi)" &rarr; **molti a uno**  
  
- #### **VANTAGGI**:
    > - Numero chiavi pub e prv è __2n per n utenti__
    > - Non è richiesto nessuno scambio segreto di chiavi
- #### **SVANTAGGI**:
    > - Molto lenti
    > - Attacchi __Chosen Plain-Text__
  
 ### **ATTACCHI CHOSEN PLAIN-TEXT**
 - Scegliere il numero di messaggi da cifrare (1...h), ottendo i crittogrammi (c<sub>1</sub>...c<sub>h</sub>)
 - Confrontare i crittogrammi in possesso con un qualsiasi messaggio che viaggia verso il destinario per decrifrarlo  
  
### **CRIFRARI IBRIDI**
- **SI USA**:
    - <mark style= "background-color: #98FB98">CIFRARI A CHIAVE PRV</mark> (AES) per comunicazioni di massa
    - <mark style= "background-color: #98FB98">CIFRARI A CHIAVE PUB</mark> per scambiare le chiavi segrete
- Le chiavi sono composte al massimo da qualche byte
- L'attacco Chosen Plain-Text non funzina se le chiavi scambiate sono **imprevedibili**
- Trasmissione veloce dei messaggi, lenta delle chiavi  

#### **APPLICAZIONI SU RETE**:
- Identificazione dell'utente
- Autentificazione
- Firma digitale  
  
---
### **<mark style= "background-color: #20B2AA">ALGEBRA**
### RAPPRESENTAZIONE MATEMATICA DI OGGETTI
- <u> **ALFABETO**</u>: Insieme finito di **caratteri**
- Per rappresentare un qualsiasi oggetto dobbiamo assegnarli una **sequenza** di caratteri
- per diversi oggetti diverse seq.
    > Prendiamo l'alfabeto A, **|A| = n** caratteri e **N**, il numero di ogg. da rappresentare.  
    >Il metodo di rappresentazione è tanto migliore quanto più d<sub>min</sub>(n,N) si avvicina a d(n,N)&#x219D;(rapp. possibili)
- Se **n = 1** le rapp. non sono che **seq. di quel carattere**
- Se poniamo **n = 2** (rapp. binaria) con A = {0,1}. Per k>=1 le possibili sequenze di lunghezza k costituiscono le disposizioni con ripetizione di 0,1 e sono in totale 2<sup>k</sup>  
**Per rappresentare N oggetti**:
    > **2<sup>k+1</sup>**<sub>(_num. tot. di seq. lunghe da 1 a k, meno la seq. di l = 0_)</sub> **- 2 >= N**, ovvero **k >= lg<sub>2</sub> (N+2) -1**  
    > **lg<sub>2</sub>N -1 <= d<sub>min</sub> (2,N) <= lg<sub>2</sub>N**  
  
### ALGEBRA MODULARE
>..  
  

---
### <mark style= "background-color: #20B2AA">CIFRARI STORICI
> **MSG DA CIFRARE**: Frasi di senso compiuto in liguaggio naturale  

#### PRINCIPI DI BACONE (XIII Secolo) 
- **C e D** facili da calcolare
- **D** impossibile da ricavare senza **C**
- **c = C(m)** deve sembrare "_innocente_"  
#### CIFRARIO DI CESARE <u> GENERALIZZATO</u> <mark style= "background-color: #98FB98">SOSTITUZIONE MONOALFABETICA</mark>
- <u>Ruotiamo</u> l'alfabeto di **k** posizioni arbitrariamente **1<=k<=25**
- **CIFRATURA DI X**
    >**Pos(y) = (Pos(x) + k) mod 26**
- **DECIFRATURA DI Y**
    >**Pos(x) = (Pos(y) - k) mod 26**
- "Comporre più cifrari non aumenta la sicurezza"

#### CIFRARI A SOSTITUZIONE
- Sostituiscono ogni lettera del testo ad una o più dell'alfabeto secondo una regola prefissata (monoalfabetica/polialfabetica)
#### CIFRARI A TRASPOSIZIONE
- Permutuano le lettere testo secondo una regola prefissata
  
#### CIFRARIO AFFINE
- ##### CIFRATURA:
    - una lettera **x** in chiaro viene sostituita con la lettera cifrato y nella posizione:
        > **pos(y) = (*a* pos(x)+*b*) mod 26**  
        > **k = *<a,b>*** &rarr; chiave segreta
- ##### DECIFRATURA:
    - ***a*<sup>-1</sup> &rarr;** inverso di ***a* mod 26**
        > **pos(x) = *a*<sup>-1</sup> (pos(y)-*b*) mod 26**
- ##### VINCOLI:
    - *a*<sup>-1</sup> <mark style= "background-color: #98FB98">esiste ed è unico</mark> _**se e solo se**_ **MCD(*a*,m) = 1**
    - Se **MCD(*a*,m) != 1** C non è <U>INNIETTIVA</U>  
  
- ##### CHIAVI SEGRETE:
    1. ***a* e 26** <u>devono essere</u> **<mark style= "background-color: #98FB98">co-primi</mark>**:
        - i fattori primi di 26 sono 2 e 13
        - a può assumere qualsiasi valore dispari tra 1 e 25, ad
eccezione di 13 (**12 valori** possibili)
    2. *b* può essere scelto liberamente tra 0 e 25
        - può assumere **26 valori**
    3. Le chiavi legittime sono tutte le possibili *<a, b>*
    4. In totale **311 chiavi** (12*26 -1)
        - Troppo poche
        - La coppia <1,0> lascia inalterato il messaggio
    - **Se la segretezza dipende unicamente dalla chiave**:
        - il numero delle chiavi deve essere così grande da
essere praticamente immune da ogni tentativo di
provarle tutte
        - la chiave segreta deve essere scelta in modo
causale  


#### CIFRARIO COMPLETO
- Spazio delle chiavi esteso a **26! - 1 (~ 4 ∙1026)**
- si può forzare (senza ricorrere a un attacco esauriente)
sfruttando:
    - Struttura logica dei messaggi in chiaro
    - Occorrenza statica delle lettere:    
        ![](https://upload.wikimedia.org/wikipedia/commons/thumb/5/58/Frequenze-ord-alf_it.png/310px-Frequenze-ord-alf_it.png) 
   
"Le cifrature monoalfabetiche sono facili da violare perché conservano
le informazioni di frequenza dell’alfabeto originario"  
&rarr; La struttura del testo in chiaro permane nel testo cifrato  
  
#### CIFRARI A SOSTITUZIONE POLIALFABETICA
- **Una stessa lettera** che si incontra in punti diversi del
messaggio in chiaro **ammette un insieme di lettere sostitutive
possibili** scelte con una regola opportuna  
  
#### CIFRARIO DI AUGUSTO:
- **ESEMPIO**:
    - lettera in posizione **i** nel documento: **α**
    - lettera in posizione **i** nell’Iliade: **ε**
    - carattere in posizione i nel crittogramma: **4 (distanza tra α e ε)**  

- **VANTAGGIO**:
    > Cifrario difficile da forzare se la chiave è lunghissima  

- **SVANTAGGIO**:
    > Registrazione per iscritto della chiave  

#### CIFRARIO ALBERTI






