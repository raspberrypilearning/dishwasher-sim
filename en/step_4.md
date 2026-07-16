## Make one utensil appear

Code the `spoon` first. Later, you will copy its scripts to the other dish sprites.

> [!TASK]
>
> Click the `spoon_state_01_clean_sparkle` sprite. Add a `when green flag clicked`{:class="block3events"} block with a `hide`{:class="block3looks"} block.
>
> ```blocks3
> when green flag clicked
> hide
> ```

> [!TASK]
>
> Start another script with a `when I receive ()`{:class="block3events"} block and choose the `spoon` message.
>
> ```blocks3
> when I receive (spoon v)
> switch costume to (spoon_state_06_filthy v)
> set [clean v] to [false]
> set size to (0) %
> go to x: (0) y: (-120)
> show
> repeat (20)
> change y by (6)
> change size by (6)
> end
> set drag mode [not draggable v]
> wait until <(clean) = [true]>
> broadcast (clean v)
> ```

The spoon starts tiny and grows as it rises out of the sink.

> [!TASK]
>
> Click the green flag. The dirty spoon appears in the middle of the sink.
