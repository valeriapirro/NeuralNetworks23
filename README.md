# NeuralNetworks23

Prepare a public repository with your code, which should be properly polished and documented. 
Inside the repository, add:

-A README file describing very briefly the method and the instructions to install everything that is needed to run the code.
One notebook containing:
-a description of the method you have implemented (up to 1-2 pages);
-a detailed example of how to use the method and the code (similar to our lab sessions);
-a summary of the main results you have obtained.

-------------
# Estimating Training Data Influence by Tracing Gradient Descent 

https://arxiv.org/abs/2002.08484

This paper formalizes the process of identifying the influence that a training instance has on the prediction performed by the Neural Network on a test instance. In the paper, two different methods are implemented. 

First of all, the influence that the training instance z exerts on a test example z' is defined as the change of loss measured between the prediction made on z' before giving z to the Network and the prediction made on z' after giving z to the Network (rivedere la frase). To apply this principle on the whole dataset, the loss changes have to be accumulated while training is progressing. 

This application of the approach is clearly an ideal one since it lays under the assumption to optimize each observation at a time. It's the first approach analyzed by the research, resulting in the $TracInIdeal(z, z') = \sum\limits_{\substack{t:z_t \\ =z}} (l(w_t, z) - l(w_{t+1}, z'))$ 

-------------

- california housing prices dataset
- regressione
- 8 feature densità pop area longitudine latitudine dell'immobile servizi limitrofi
- per il training va fatto preprocessing tramite standard scaler su fetch california housing anziche usare il csv tanto il dataset è uguale ma importato piu facile
- features scalate con standard scaler perchè float32 le features
- training salva i checkpoint tramite anziche quello del paper, viene salvato solo i pesi del modello in state dict 
- fa evaluation la loss scende quindi ok
- (cella models = []) inutilizzata
- DA QUI
- la self influence su tutti i training point per sapere quanto influenzano l'andamento della loss nel training (formula 5 pagina 4 ma z e z' sono lo stesso datapoint)
- pagina 8 esperimento del paper calif housing prices anche loro self influence e opponent/proponent anzi solo proponent che facevano prendono 11 esempi di case a palo alto e si aspetta che proponent siano altre case con prezzi altissimi (nella nota viene detto il metodo di train) 
- vedere esperimento con stessi parametri del paper
- grad sum formula del trackin prodotto tra gradienti (SELF INFLUENCE)
- poi rifaccio fetch cali housing ma riporto in pandas dataframe per il plot delle figure
- ultime 100 istanze self influence che verranno plottate sono quelle con self influence piu alta (nella colonna 1 per quelle alte e 2 per quelle basse )


-proponent opponent ha un for in piu che gira sui punti di test, nel paper prendono 11 punti di palo alto. fatto rate di latitude e longitude coerenti con palo alto e seleziona 11 ma è troppo lento e ripetuto tutto per fare come l'altro e la figura è coerente

