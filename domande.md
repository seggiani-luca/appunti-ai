1) Perche i paradigmi già visti (supervised e unsupervised) non bastano? A cosa serve il reinforcement learning?
> Il reinforcement learning ci permette di dare comunque indicazioni al modello, ma in manierà più facile da definire

2) Che cosa cambia fra il reinforcement learning e un comune Markov decision process (MDP)?
> Il modello di reinforcement learning è *dentro* l'MDP, e deve ricavarlo mentre lo risolve

3) (Riguardo all'esempio sulla griglia) come il variare dei reward influenza la scelta ottima?
> Nell'esempio dato, a reward sufficientemente bassi il modello ignora la differenza fra 1 (vittoria) e -1 (sconfitta)

4) Come mai la direct estimation nel passive reinforcement learning non è efficiente? Come possiamo sfruttare la proprietà di Markov a nostro vantaggio?
> Perchè non usa la proprietà di Markov; possiamo sfruttarla inserendo qualche euristica che si basi sulla differenza temporale data da un "salto" fra uno stato e un altro

5) Quando non ci sono differenze fra TD e ADP? In generale, quali sono similarità e differenze?
> Non ci sono differenze sul lungo termine; sul corto termine la TD osserva il *prossimo* stato mentre l'ADP li osserva *tutti*

6) I modelli visti per l'esplorazione sicura sono sempre utili? Quando conviene adottarli? Anche negli stati dove sono effettivamente utili, possiamo dare per scontato che risolveranno ogni problema?
> Sono utili quando gli stati negativi o assorbenti penalizzano il processo di apprendimento; conviene adottarli in casistiche reali e non in simulazioni; anche se li adottiamo dobbiamo fornirli di priori e modelli adeguati

7) Esistono dei legami fra il bayesian reinforcement learning e l'approccio del controllo robusto?
> L'insieme H del controllo robusto è dato dalle ipotesi che rispettano una certa soglia di likelihood sul bayesian reinforcement learning

8) Quali sono le differenze fra TD Q-learning e SARSA? Quali casistiche vengono coperte meglio dal SARSA, e viceversa?
> Il TD Q-learning si aspetta scelte ottime, il SARSA segue la politica; il SARSA gestirà potrà dare penalità sulla politica corrente; il Q-learning darà stime migliori per casi più generali
