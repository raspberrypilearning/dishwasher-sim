## Scrub the dish

Make the player add soap, then scrub through the bowl's dirty-to-clean costumes.

> [!TASK]
>
> Select the `bowl` sprite in the Sprite pane, then select the **Costumes** tab. Check that its six costumes are named `1` to `6`: costume `1` is filthy and costume `6` is sparkling clean.
>
> ![The bowl costumes from filthy to sparkling clean.](images/bowl-cleaning-states.png)

> [!TASK]
>
> Select the **Code** tab for the `bowl` sprite. Start a script that responds when the player clicks the bowl on the Stage, but only while it still needs cleaning.
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
> Inside the `if () then`{:class="block3control"} block, add an `if () then else`{:class="block3control"} block. Check whether the player has picked up soap. Leave both branches empty for now.
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
> In the soap branch, add a `repeat until ()`{:class="block3control"} loop. Make it stop when the bowl reaches costume number `6`.
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
> Inside the new loop, wait until the player is pressing the mouse button.
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
> Under the `wait until ()`{:class="block3control"} block, play a random cleaning sound, move to the next costume, and add a short delay.
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
> After the `repeat until ()`{:class="block3control"} loop, set `clean`{:class="block3variables"} to `true`. This tells the other scripts that scrubbing has finished.
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
> Finally, add feedback to the `else`{:class="block3control"} branch for a player who tries to clean the bowl without soap.
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
> Click the green flag, then click the bowl before using the soap. Next, click the soap and click and hold the bowl to scrub it clean.
>
> <img src="images/bowl-costume-1.png" alt="The dirty bowl sprite." width="138" height="105" style="object-fit: contain;"> <img src="images/soap.png" alt="The soap sprite." width="128" height="105" style="object-fit: contain;">

> [!TIP]
>
> Before the player uses soap, the bowl says what it needs. After the player uses soap, the `repeat until`{:class="block3control"} loop moves through the costumes and stops on costume `6`, the sparkling-clean bowl.
