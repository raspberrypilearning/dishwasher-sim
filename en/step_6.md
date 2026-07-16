## Put it in the rack

Once the spoon is clean, let the player drag it into the rack and score a clean plate.

> [!TASK]
>
> Add a `when I receive ()`{:class="block3events"} block to the `cloth1` sprite and choose the `clean` message.
>
> ```blocks3
> when I receive (clean v)
> say [Now put it in the rack!] for (2) seconds
> ```

> [!TASK]
>
> Add this script to the `spoon_state_01_clean_sparkle` sprite. It uses `set drag mode ()`{:class="block3sensing"} to unlock the clean spoon, then `wait until ()`{:class="block3control"} and `touching ()?`{:class="block3sensing"} to wait for the rack before starting the next round.
>
> ```blocks3
> when I receive (clean v)
> start sound (Coin v)
> set [soap v] to [false]
> set drag mode [draggable v]
> wait until <touching (rack v)?>
> repeat (60)
> change size by (-2)
> end
> change [clean plates v] by (1)
> hide
> set size to (0) %
> go to x: (0) y: (-140)
> set [clean v] to [false]
> broadcast (spoon v)
> ```

> [!TASK]
>
> **Test:** Click the green flag, use the soap, scrub the spoon, then drag it into the rack.

The spoon disappears, the `clean plates`{:class="block3variables"} score goes up, and a new spoon appears.
