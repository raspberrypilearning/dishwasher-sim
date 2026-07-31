## Make one dish appear

Code the `bowl` first. Later, you will copy its scripts to the other dish sprites.

The starter project names this sprite `bowl` and its costumes `bowl 1` to `bowl 6`. The dirty bowl is costume number `1`, and the sparkling-clean bowl is costume number `6`.

![The bowl costumes from filthy to sparkling clean.](images/bowl-cleaning-states.png)

> [!TASK]
>
> Select the `bowl` sprite in the Sprite pane. Add a `when green flag clicked`{:class="block3events"} block with a `hide`{:class="block3looks"} block.
>
> <img src="images/bowl-costume-1.png" alt="The dirty bowl sprite." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> +when green flag clicked
> +hide
> ```

> [!TASK]
>
> Start another script on the `bowl` sprite with a `when I receive ()`{:class="block3events"} block. Choose the `bowl` broadcast that you created earlier.
>
> Switch the sprite to costume number `1` so that the dirty bowl appears in the sink.
>
> <img src="images/bowl-costume-1.png" alt="The dirty bowl sprite." width="138" height="105" style="object-fit: contain;">
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
> Add a loop to the same script to make the bowl rise out of the sink.
>
> <img src="images/bowl-costume-1.png" alt="The dirty bowl sprite." width="138" height="105" style="object-fit: contain;">
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
> Add blocks to the bottom of the same script to wait until the bowl is clean. In the `broadcast ()`{:class="block3events"} block, choose **New message** and create a broadcast called `clean`.
>
> <img src="images/bowl-costume-1.png" alt="The dirty bowl sprite." width="138" height="105" style="object-fit: contain;">
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
> Click the green flag. The dirty bowl should appear in the middle of the sink.

> [!TIP]
>
> The bowl starts tiny and grows as it rises out of the sink.
