## Frotte la vaisselle

Fais en sorte que le joueur ou la joueuse ajoute du savon, puis frotte les costumes sales du bol pour les nettoyer.

> [!TASK]
>
> Sélectionne le sprite `bol` dans le panneau Sprite, puis sélectionne l'onglet **Costumes**. Vérifie que ses six costumes sont nommés de `1` à `6` : le costume `1` est sale et le costume `6` est d'une propreté éclatante.
>
> ![Les costumes bol passent de la saleté à la propreté éclatante.](images/bowl-cleaning-states.png)

> [!TASK]
>
> Sélectionne l'onglet **Code** pour le sprite `bol`. Démarre un script qui répond lorsque le joueur ou la joueuse clique sur le bol sur la scène, mais seulement pendant qu'il doit encore être nettoyé.
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
> Dans le bloc `si () alors`{:class="block3control"}, ajoute un bloc `si () alors sinon`{:class="block3control"}. Vérifie si le joueur ou la joueuse a ramassé du savon. Laisse les deux parties vides pour le moment.
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
> Dans la partie savon, ajoute une boucle `répéter jusqu'à ()`{:class="block3control"}. Arrête-le lorsque le bol atteint le numéro de costume `6`.
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
> Dans la nouvelle boucle, attends que le joueur ou la joueuse appuie sur le bouton de la souris.
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
> Sous le bloc `attendre jusqu'à ()`{:class="block3control"}, joue un son de nettoyage aléatoire, se déplace vers le costume suivant et ajoute un court délai.
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
> Après la boucle `répéter jusqu'à ()`{:class="block3control"}, définis `propre`{:class="block3variables"} à `true`. Cela indique aux autres scripts que le nettoyage est terminé.
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
> Enfin, ajoute des commentaires à la partie `sinon`{:class="block3control"} pour un joueur ou une joueuse qui essaie de nettoyer le bol sans savon.
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
> Clique sur le drapeau vert, puis clique sur le bol avant d'utiliser le savon. Ensuite, clique sur le savon et clique et maintiens enfoncé sur le bol pour le nettoyer.
>
> <img src="images/bowl-costume-1.png" alt="The dirty bowl sprite." width="138" height="105" style="object-fit: contain;"> <img src="images/soap.png" alt="The soap sprite." width="128" height="105" style="object-fit: contain;">

> [!TIP]
>
> Avant que le joueur ou la joueuse n'utilise du savon, le bol indique ce dont il a besoin. Après que le joueur ou la joueuse utilise du savon, la boucle `répéter jusqu'à`{:class="block3control"} se déplace à travers les costumes et s'arrête sur le costume `6`, le bol étincelant propre.
