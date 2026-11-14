## Strofinare il piatto

Fai aggiungere il sapone al giocatore, poi strofina i costumi nella ciotola, passando da sporchi a puliti.

> [!TASK]
>
> Selezionare lo sprite `bowl` nel riquadro Sprite, quindi selezionare la scheda **Costumi**. Controlla che i suoi sei costumi siano chiamati `1` a `6`: il costume `1` è sporco e il costume `6` è scintillante pulito.
>
> ![La ciotola costumi da sporco a scintillante pulito.](images/bowl-cleaning-states.png)

> [!TASK]
>
> Seleziona la scheda **Codice** per lo sprite `bowl`. Avvia uno script che risponde quando il giocatore fa clic sulla ciotola sullo Stage, ma solo mentre ha ancora bisogno di pulizia.
>
> <img src="images/bowl-thumb.png" alt="The bowl sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> +when this sprite clicked
> +if <(clean) = [false]> then
> end
> ```

> [!TASK]
>
> Innanzitutto, racchiudi il blocco `go to x: y:`{:class="block3motion"} in un blocco `if () then`{:class="block3control"}. Verifica se il giocatore ha raccolto il sapone. Per ora, lascia entrambi i rami vuoti.
>
> <img src="images/bowl-thumb.png" alt="The bowl sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> when this sprite clicked
> if <(clean) = [false]> then
> +if <(soap) = [true]> then
> else
> end
> end
> ```

> [!TASK]
>
> Nel ramo sapone, aggiungi un ciclo `ripeti fino a quando ()`{:class="block3control"}. Fallo fermare quando la ciotola raggiunge il costume numero 6.
>
> <img src="images/bowl-thumb.png" alt="The bowl sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> when this sprite clicked
> if <(clean) = [false]> then
> if <(soap) = [true]> then
> +repeat until <(costume [number v]) = (6)>
> end
> else
> end
> end
> ```

> [!TASK]
>
> All'interno del nuovo ciclo, attendi che il giocatore prema il pulsante del mouse.
>
> <img src="images/bowl-thumb.png" alt="The bowl sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> when this sprite clicked
> if <(clean) = [false]> then
> if <(soap) = [true]> then
> repeat until <(costume [number v]) = (6)>
> +wait until <mouse down?>
> end
> else
> end
> end
> ```

> [!TASK]
>
> Sotto il blocco `attendi fino a quando ()`{:class="block3control"}, riproduci un suono di pulizia casuale, passa al costume successivo e aggiungi un breve ritardo.
>
> <img src="images/bowl-thumb.png" alt="The bowl sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> when this sprite clicked
> if <(clean) = [false]> then
> if <(soap) = [true]> then
> repeat until <(costume [number v]) = (6)>
> wait until <mouse down?>
> +start sound (pick random (1) to (4))
> +next costume
> +wait (0.2) seconds
> end
> else
> end
> end
> ```

> [!TASK]
>
> Dopo il ciclo `ripeti fino a quando ()`{:class="block3control"}, imposta `puliti`{:class="block3variables"} a `vero`. Questo comunica agli altri script che la pulizia dei dati è terminata.
>
> <img src="images/bowl-thumb.png" alt="The bowl sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> when this sprite clicked
> if <(clean) = [false]> then
> if <(soap) = [true]> then
> repeat until <(costume [number v]) = (6)>
> wait until <mouse down?>
> start sound (pick random (1) to (4))
> next costume
> wait (0.2) seconds
> end
> +set [clean v] to [true]
> else
> end
> end
> ```

> [!TASK]
>
> Infine, aggiungi un feedback al ramo `altrimenti`{:class="block3control"} per un giocatore che cerca di pulire la ciotola senza sapone.
>
> <img src="images/bowl-thumb.png" alt="The bowl sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> when this sprite clicked
> if <(clean) = [false]> then
> if <(soap) = [true]> then
> repeat until <(costume [number v]) = (6)>
> wait until <mouse down?>
> start sound (pick random (1) to (4))
> next costume
> wait (0.2) seconds
> end
> set [clean v] to [true]
> else
> +say [You need soap!] for (2) seconds
> +start sound (Collect v)
> end
> end
> ```

> [!TASK]
>
> Test: Clicca sulla bandierina verde e muovi il mouse sullo stage. Successivamente, fai clic sul sapone e tieni premuto sulla ciotola per strofinarla e pulirla.
>
> <img src="images/bowl-costume-1.png" alt="The dirty bowl sprite." width="138" height="105" style="object-fit: contain;">1 2<img src="images/soap.png" alt="The soap sprite." width="128" height="105" style="object-fit: contain;">

> [!TIP]
>
> Prima che il giocatore utilizzi il sapone, la ciotola dice ciò di cui ha bisogno. Dopo che il giocatore usa il sapone, il ciclo `ripeti fino a quando`{:class="block3control"} scorre i costumi e si ferma sul costume `6`, la ciotola pulitissima.
