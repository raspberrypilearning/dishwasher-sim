## Add music controls

Add background music and a button that skips to the next song.

> [!TASK]
>
> Click the `Stage`, then make these variables **for all sprites** from the `Variables`{:class="block3variables"} blocks menu:
>
> - `song`{:class="block3variables"} stores which song is playing. Untick this variable.
> - `music volume`{:class="block3variables"} stores how loud the music should be. Leave this variable ticked so it appears on the Stage.
>
> <p align="center"><img src="images/music-volume.png" alt="The music volume variable ticked in the Variables menu." width="240" height="66" style="object-fit: contain;"></p>

> [!TASK]
>
> On the Stage, double-click the `music volume`{:class="block3variables"} variable display until it changes into a slider. The player can drag the slider to change the music volume.

> [!TASK]
>
> Click the `Stage`. Add the music setup blocks near the start of the `when green flag clicked`{:class="block3events"} script.
>
> ```blocks3
> when green flag clicked
> set [clean plates v] to (0)
> set [clean v] to [false]
> set [soap v] to [false]
> +set [song v] to (pick random (1) to (3))
> +set [music volume v] to (25)
> +set volume to (music volume) %
> +broadcast (play music v)
> broadcast (item (pick random (1) to (8)) of [stuff v])
> ```

> [!TASK]
>
> Add another script to the `Stage` so the sound volume follows the `music volume`{:class="block3variables"} slider while the game runs.
>
> ```blocks3
> +when green flag clicked
> +forever
> +set volume to (music volume) %
> end
> ```

> [!TIP]
>
> Balancing the volume of music and sound effects is called **audio mixing**. Quieter music leaves room for the cleaning and scoring sounds.

> [!TASK]
>
> Add a new script to the `Stage` with a `when I receive ()`{:class="block3events"} block and choose the `play music` message. Start with `song2` as the default song.
>
> ```blocks3
> +when I receive (play music v)
> +forever
> +play sound (song2 v) until done
> end
> ```

> [!TASK]
>
> Replace the `play sound (song2 v) until done`{:class="block3sound"} block with an `if () then else`{:class="block3control"} block. Keep `song2` in the `else`{:class="block3control"} branch.
>
> ```blocks3
> when I receive (play music v)
> forever
> +if <(song) = (1)> then
> else
> play sound (song2 v) until done
> end
> end
> ```

> [!TASK]
>
> Add the `play sound () until done`{:class="block3sound"} block inside the first branch so `song1` can play.
>
> ```blocks3
> when I receive (play music v)
> forever
> if <(song) = (1)> then
> +play sound (song1 v) until done
> else
> play sound (song2 v) until done
> end
> end
> ```

> [!TASK]
>
> Inside the `else`{:class="block3control"}, add another `if () then else`{:class="block3control"} block so the script can choose between `song2` and `song3`. Keep `song2` in the first branch.
>
> ```blocks3
> when I receive (play music v)
> forever
> if <(song) = (1)> then
> play sound (song1 v) until done
> else
> +if <(song) = (2)> then
> play sound (song2 v) until done
> else
> end
> end
> end
> ```

> [!TASK]
>
> Add the `play sound () until done`{:class="block3sound"} block inside the final `else`{:class="block3control"} branch so `song3` can play.
>
> ```blocks3
> when I receive (play music v)
> forever
> if <(song) = (1)> then
> play sound (song1 v) until done
> else
> if <(song) = (2)> then
> play sound (song2 v) until done
> else
> +play sound (song3 v) until done
> end
> end
> end
> ```

> [!TASK]
>
> Add a `change () by ()`{:class="block3variables"} block to the bottom of the `forever`{:class="block3control"} loop so the next song plays after the current song finishes.
>
> ```blocks3
> when I receive (play music v)
> forever
> if <(song) = (1)> then
> play sound (song1 v) until done
> else
> if <(song) = (2)> then
> play sound (song2 v) until done
> else
> play sound (song3 v) until done
> end
> end
> +change [song v] by (1)
> end
> ```

> [!TASK]
>
> Add an `if () then`{:class="block3control"} block below the song change to check whether the song number has gone past `3`.
>
> ```blocks3
> when I receive (play music v)
> forever
> if <(song) = (1)> then
> play sound (song1 v) until done
> else
> if <(song) = (2)> then
> play sound (song2 v) until done
> else
> play sound (song3 v) until done
> end
> end
> change [song v] by (1)
> +if <(song) > (3)> then
> end
> end
> ```

> [!TASK]
>
> Inside the `if () then`{:class="block3control"} block, reset the song number to `1`.
>
> ```blocks3
> when I receive (play music v)
> forever
> if <(song) = (1)> then
> play sound (song1 v) until done
> else
> if <(song) = (2)> then
> play sound (song2 v) until done
> else
> play sound (song3 v) until done
> end
> end
> change [song v] by (1)
> if <(song) > (3)> then
> +set [song v] to (1)
> end
> end
> ```

> [!TASK]
>
> Click the `skip` button sprite. Add a `broadcast ()`{:class="block3events"} block and choose the `skip` message. Set its drag mode to `not draggable`{:class="block3sensing"}.
>
> <p align="center"><img src="images/skip-button.png" alt="The skip button sprite." width="150" height="120" style="object-fit: contain;"></p>
>
> ```blocks3
> +when this sprite clicked
> +broadcast (skip v)
> ```
>
> ```blocks3
> +when green flag clicked
> +set drag mode [not draggable v]
> ```

> [!TASK]
>
> Click the `Stage`. Add a `when I receive ()`{:class="block3events"} script for the `skip` message to stop the current song, move to the next song, and restart the music player.
>
> ```blocks3
> +when I receive (skip v)
> +stop [other scripts in sprite v]
> +stop all sounds
> +change [song v] by (1)
> +broadcast (play music v)
> ```

> [!TASK]
>
> Add an `if () then`{:class="block3control"} block before the `broadcast ()`{:class="block3events"} block to check whether the song number has gone past `3`.
>
> ```blocks3
> when I receive (skip v)
> stop [other scripts in sprite v]
> stop all sounds
> change [song v] by (1)
> +if <(song) > (3)> then
> end
> broadcast (play music v)
> ```

> [!TASK]
>
> Inside the `if () then`{:class="block3control"} block, reset the song number to `1`.
>
> ```blocks3
> when I receive (skip v)
> stop [other scripts in sprite v]
> stop all sounds
> change [song v] by (1)
> if <(song) > (3)> then
> +set [song v] to (1)
> end
> broadcast (play music v)
> ```

Click the green flag and clean dishes. The music plays, and the skip button changes the song.

> [!SAVE]
