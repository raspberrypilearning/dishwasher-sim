## Add soap and a cloth

Make the soap clickable and make the cloth follow the pointer.

> [!TASK]
>
> Click the `soap` sprite. Add code so the player can click the soap before they scrub a dish.
>
> <p align="center"><img src="images/soap.png" alt="The soap sprite." width="150" height="120" style="object-fit: contain;"></p>
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
> ```blocks3
> +when green flag clicked
> +set size to (25) %
> +set drag mode [not draggable v]
> +go to [back v] layer
> ```

> [!TASK]
>
> Add one more script to the `soap` sprite to make it pulse gently.
>
> ```blocks3
> +when green flag clicked
> +forever
> +repeat (15)
> +change size by (0.2)
> end
> +repeat (15)
> +change size by (-0.2)
> end
> end
> ```

> [!TASK]
>
> Click the `cloth1` sprite. Make it follow the mouse pointer.
>
> <p align="center"><img src="images/cloth-states.png" alt="The dry cloth, soapy cloth, and hand costumes." width="600" height="257" style="object-fit: contain;"></p>
>
> ```blocks3
> +when green flag clicked
> +forever
> +go to (mouse-pointer v)
> +go to [front v] layer
> end
> ```

> [!TASK]
>
> Add another script to the `cloth1` sprite. Start by showing the dry cloth.
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

> [!TIP]
>
> **Visual feedback** shows the player that an action worked. Changing the cloth costume makes it clear when the player has picked up soap.

Click the green flag and move the pointer. The cloth follows the pointer; when you click the soap, it changes to a soapy cloth.
