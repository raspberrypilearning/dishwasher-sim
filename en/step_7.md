## Copy the dish scripts

Copy the spoon scripts to the other dish sprites, then edit the message and costume names.

> [!TIP]
>
> Game developers often build and test one working **prototype** first. Fixing the spoon before copying its scripts makes problems easier to find.

> [!TASK]
>
> Copy the four spoon scripts to these sprites:
>
> - `bowl_state_01_clean_sparkle`
> - `fork_state_01_clean_sparkle`
> - `knife_state_01_clean_sparkle`
> - `mug_state_01_clean_sparkle`
> - `plate_state_01_clean_sparkle`
> - `side_plate_state_01_clean_sparkle`
> - `tea_cup_state_01_clean_sparkle`

> [!TASK]
>
> On each copied sprite, edit the `when I receive (spoon v)`{:class="block3events"} block and the first `switch costume to ()`{:class="block3looks"} block.
>
> | Sprite | Receive message | Dirty costume |
> | --- | --- | --- |
> | `bowl_state_01_clean_sparkle` | `bowl` | `bowl_state_06_filthy` |
> | `fork_state_01_clean_sparkle` | `fork` | `fork_state_06_filthy` |
> | `knife_state_01_clean_sparkle` | `knife` | `knife_state_06_filthy` |
> | `mug_state_01_clean_sparkle` | `mug` | `mug_state_06_filthy` |
> | `plate_state_01_clean_sparkle` | `plate` | `plate_state_06_filthy` |
> | `side_plate_state_01_clean_sparkle` | `sideplate` | `side_plate_state_06_filthy` |
> | `tea_cup_state_01_clean_sparkle` | `teacup` | `tea_cup_state_06_filthy` |

> [!TASK]
>
> Click the `Stage`. From the `Variables`{:class="block3variables"} blocks menu, choose **Make a List**. Make a list called `stuff`{:class="block3variables"} for all sprites.
>
> Add these eight items to the list, one item on each line:
>
> 1. `bowl`
> 2. `fork`
> 3. `knife`
> 4. `mug`
> 5. `plate`
> 6. `sideplate`
> 7. `spoon`
> 8. `teacup`
>
> Untick the list so it does not appear on the Stage.

> [!TASK]
>
> Click the `Stage`. Update the `when green flag clicked`{:class="block3events"} script so the game chooses a random item from the `stuff`{:class="block3variables"} list.
>
> ```blocks3
> when green flag clicked
> set [clean plates v] to (0)
> set [clean v] to [false]
> set [soap v] to [false]
> +broadcast (item (pick random (1) to (8)) of [stuff v])
> ```

> [!TASK]
>
> Update the last `broadcast ()`{:class="block3events"} block in the clean script on the spoon and on each copied dish sprite, so the next item is random too.
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
> +broadcast (item (pick random (1) to (8)) of [stuff v])
> ```

Click the green flag and play a few rounds. Different dirty dishes appear after you put each clean one in the rack.
