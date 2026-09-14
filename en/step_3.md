## Add soap and a cloth

Make the soap clickable and make the cloth change to show the state of the game.

> [!TASK]
>
> Select the `soap` sprite in the Sprite pane. Add code so the player can use the soap before they scrub a dish.
>
> <img src="images/soap-thumb.png" alt="The soap sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> +when this sprite clicked
> +start sound (Bubbles v)
> +set [soap v] to [true]
> ```

> [!TASK]
>
> Add another script to the `soap` sprite to make it sit behind the dishes.
>
> <img src="images/soap-thumb.png" alt="The soap sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> +when green flag clicked
> +set drag mode [not draggable v]
> +go to [back v] layer
> ```

> [!NOTE]
>
> `set drag mode [not draggable]` only prevents dragging in full-screen mode. While you test in the editor, you can still drag the soap and other sprites.

> [!TASK]
>
> Start one more script on the `soap` sprite. Set its size to `30` percent before adding any blocks that change its size. This known starting size makes it easy to reset the soap if you make a mistake.
>
> Add a `forever`{:class="block3control"} loop beneath the size block.
>
> <img src="images/soap-thumb.png" alt="The soap sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> +when green flag clicked
> +set size to (30) %
> +forever
> end
> ```

> [!TIP]
>
> `30` percent is the preset starting size for the soap. You can experiment by changing the value in the `set size to () %`{:class="block3looks"} block, and return it to `30` if you want to reset it.
>
> ![The soap sprite's Size set to 30, with the value circled.](images/soap-size-30.png)

> [!TASK]
>
> Inside the `forever`{:class="block3control"} loop, add a `repeat ()`{:class="block3control"} loop that gradually makes the soap larger.
>
> <img src="images/soap-thumb.png" alt="The soap sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> when green flag clicked
> set size to (30) %
> forever
> +repeat (15)
> +change size by (0.2)
> end
> end
> ```

> [!TIP]
>
> To save time, right-click the top block in a group and choose **Duplicate** to copy the whole group. Try this with the `repeat ()` and `change size by ()` blocks, or with an `if () then else` block that already contains its operator and variable. Then change only what needs to be different.

> [!TASK]
>
> Beneath the first `repeat ()`{:class="block3control"} loop, add another loop that returns the soap to `30` percent.
>
> Together, the two loops make the soap gently grow and shrink. This draws the player's attention and makes it clear that they can interact with the soap.
>
> <img src="images/soap-thumb.png" alt="The soap sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> when green flag clicked
> set size to (30) %
> forever
> repeat (15)
> change size by (0.2)
> end
> +repeat (15)
> +change size by (-0.2)
> end
> end
> ```

> [!TASK]
>
> Select the `cloth` sprite in the Sprite pane. Add another script that starts by showing the dry cloth.
>
> <img src="images/cloth-thumb.png" alt="The cloth sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> +when green flag clicked
> +forever
> +switch costume to (cloth1 v)
> end
> ```

> [!TASK]
>
> Replace the `switch costume to (cloth1 v)`{:class="block3looks"} block with an `if () then else`{:class="block3control"} block. Keep the dry cloth in the `else`{:class="block3control"} branch.
>
> <img src="images/cloth-thumb.png" alt="The cloth sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> when green flag clicked
> forever
> +if <(clean) = [true]> then
> else
> switch costume to (cloth1 v)
> end
> end
> ```

> [!TASK]
>
> Add a `switch costume to ()`{:class="block3looks"} block inside the first branch to show the hand when the dish is clean.
>
> <img src="images/cloth-thumb.png" alt="The cloth sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> when green flag clicked
> forever
> if <(clean) = [true]> then
> +switch costume to (hand v)
> else
> switch costume to (cloth1 v)
> end
> end
> ```

> [!TASK]
>
> Inside the `else`{:class="block3control"}, add another `if () then else`{:class="block3control"} block to check whether the player has picked up soap. Keep the dry cloth in the new `else`{:class="block3control"} branch.
>
> <img src="images/cloth-thumb.png" alt="The cloth sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> when green flag clicked
> forever
> if <(clean) = [true]> then
> switch costume to (hand v)
> else
> +if <(soap) = [true]> then
> else
> switch costume to (cloth1 v)
> end
> end
> end
> ```

> [!TASK]
>
> Add a `switch costume to ()`{:class="block3looks"} block inside the soap branch to show the soapy cloth.
>
> <img src="images/cloth-thumb.png" alt="The cloth sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> when green flag clicked
> forever
> if <(clean) = [true]> then
> switch costume to (hand v)
> else
> if <(soap) = [true]> then
> +switch costume to (cloth2 v)
> else
> switch costume to (cloth1 v)
> end
> end
> end
> ```

> [!TASK]
>
> <p align="center"><img src="images/soap.png" alt="The soap sprite." width="150" height="120" style="object-fit: contain;"></p>
>
> Click the green flag, then click the soap on the Stage. The soap should pulse gently, and the cloth should change to the soapy costume.

> [!TIP]
>
> **Visual feedback** shows the player that an action worked. Changing the cloth costume makes it clear when the player has picked up soap.
