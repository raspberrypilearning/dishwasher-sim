## Add music controls

Add background music and a button that skips to the next song.

> [!TASK]
>
> Click the `Stage`. Add music setup blocks near the start of the green flag script.
>
> ```blocks3
> when green flag clicked
> set [clean plates v] to (0)
> set [clean v] to [false]
> set [soap v] to [false]
> +set [song v] to (pick random (1) to (3))
> +set [music volume v] to (25)
> +set volume to (music volume) %
> broadcast (item (pick random (1) to (8)) of [stuff v])
> ```

> [!TASK]
>
> Add the music loop to the bottom of the same script.
>
> ```blocks3
> when green flag clicked
> set [clean plates v] to (0)
> set [clean v] to [false]
> set [soap v] to [false]
> set [song v] to (pick random (1) to (3))
> set [music volume v] to (25)
> set volume to (music volume) %
> broadcast (item (pick random (1) to (8)) of [stuff v])
> +forever
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
> set [song v] to (1)
> end
> end
> ```

> [!TASK]
>
> Click the `Sprite1` button sprite. Make it broadcast `skip` when the player clicks it, and make it not draggable.
>
> <p align="center"><img src="images/skip-button.png" alt="The skip button sprite." width="150" height="120" style="object-fit: contain;"></p>
>
> ```blocks3
> when this sprite clicked
> broadcast (skip v)
> ```
>
> ```blocks3
> when green flag clicked
> set drag mode [not draggable v]
> ```

> [!TASK]
>
> Click the `Stage` and add a script to play the next song when it receives `skip`.
>
> ```blocks3
> when I receive (skip v)
> stop [other scripts in sprite v]
> stop all sounds
> change [song v] by (1)
> if <(song) > (3)> then
> set [song v] to (1)
> end
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
> set [song v] to (1)
> end
> end
> ```

Click the green flag and clean dishes. The music plays, and the skip button changes the song.

> [!SAVE]
