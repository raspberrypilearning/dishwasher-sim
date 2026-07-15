## Start the dishwasher

Set up the game state, place the rack, and show the first utensil.

> [!TASK]
>
> Open the `Dishwasher simulator starter` project. It already has the sprites, sounds, variables, and the `stuff`{:class="block3variables"} list.

> [!TASK]
>
> Click the `Stage`. Add this script to reset the game and show the `spoon` first.
>
> ```blocks3
> when green flag clicked
> set [clean plates v] to (0)
> set [clean v] to [false]
> set [soap v] to [false]
> broadcast (spoon v)
> ```

> [!TASK]
>
> Click the `rack` sprite and put it in the right place when the green flag is clicked.
>
> <p align="center"><img src="images/rack.png" alt="The rack sprite." width="180" height="120" style="object-fit: contain;"></p>
>
> ```blocks3
> when green flag clicked
> go to x: (140) y: (-38)
> ```

Click the green flag. Nothing appears yet, but the score resets and the rack moves into place.

