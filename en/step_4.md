## Make one dish appear

Code the `bowl` first. Later, you will copy its scripts to the other dish sprites.

> [!TASK]
>
> Click the `bowl_state_01_clean_sparkle` sprite. Add a `when green flag clicked`{:class="block3events"} block with a `hide`{:class="block3looks"} block.
>
> ```blocks3
> +when green flag clicked
> +hide
> ```

> [!TASK]
>
> Start another script with a `when I receive ()`{:class="block3events"} block and choose the `bowl` message. Set up the dirty bowl so it appears in the sink.
>
> ```blocks3
> +when I receive (bowl v)
> +switch costume to (bowl_state_06_filthy v)
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
> ```blocks3
> when I receive (bowl v)
> switch costume to (bowl_state_06_filthy v)
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
> Add blocks to the bottom of the same script to wait until the bowl is clean, then send the `clean` message.
>
> ```blocks3
> when I receive (bowl v)
> switch costume to (bowl_state_06_filthy v)
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

The bowl starts tiny and grows as it rises out of the sink.

> [!TASK]
>
> Click the green flag. The dirty bowl appears in the middle of the sink.
