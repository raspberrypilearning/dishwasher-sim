## Fai apparire un piatto

Codifica prima la `ciotola`. In seguito, copierai i suoi script sugli altri sprite dei piatti.

Il progetto iniziale chiama questo `bowl` dello sprite e i suoi costumi `1` a `6`. Il costume `1` è la ciotola sporca, e il costume `6` è la ciotola scintillante.

![La ciotola costumi da sporco a scintillante pulito.](images/bowl-cleaning-states.png)

> [!TASK]
>
> Seleziona lo sprite `cloth` nel pannello Sprite. Aggiungi un blocco `quando si clicca sulla bandiera verde`{:class="block3events"} con un blocco `nascondi`{:class="block3looks"}.
>
> <img src="images/bowl-thumb.png" alt="The bowl sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> +when green flag clicked
> +hide
> ```

> [!TASK]
>
> Avvia un nuovo script sullo sprite dell'ostacolo con un blocco `quando vengo clonato`{:class="block3control"}. Seleziona la trasmissione "bowl" che hai creato in precedenza.
>
> Cambia lo sprite con il costume numero `1` in modo che la ciotola sporca appaia nel lavandino.
>
> <img src="images/bowl-thumb.png" alt="The bowl sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> +when I receive (bowl v)
> +switch costume to (1)
> +set [clean v] to [false]
> +set size to (0) %
> +go to x: (0) y: (-120)
> +show
> +set drag mode [not draggable v]
> ```

> [!TASK]
>
> Aggiungi un ciclo allo stesso script per far sì che la ciotola si sollevi dal lavandino.
>
> <img src="images/bowl-thumb.png" alt="The bowl sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> when I receive (bowl v)
> switch costume to (1)
> set [clean v] to [false]
> set size to (0) %
> go to x: (0) y: (-120)
> show
> set drag mode [not draggable v]
> +repeat (20)
> +change y by (6)
> +change size by (6)
> end
> ```

> [!TASK]
>
> Aggiungi dei blocchi in fondo allo stesso script per attendere che la ciotola sia pulita. Nel blocco `broadcast ()`{:class="block3events"}, scegli **Nuovo messaggio** e crea un broadcast chiamato `clean`.
>
> <img src="images/bowl-thumb.png" alt="The bowl sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> when I receive (bowl v)
> switch costume to (1)
> set [clean v] to [false]
> set size to (0) %
> go to x: (0) y: (-120)
> show
> set drag mode [not draggable v]
> repeat (20)
> change y by (6)
> change size by (6)
> end
> +wait until <(clean) = [true]>
> +broadcast (clean v)
> ```

> [!TASK]
>
> <img src="images/bowl-costume-1.png" alt="The dirty bowl sprite." width="138" height="105" style="object-fit: contain;">
>
> Clicca sulla bandierina verde. La ciotola sporca dovrebbe apparire al centro del lavandino.

> [!TIP]
>
> La ciotola inizia minuscola e cresce man mano che emerge dal lavandino.
