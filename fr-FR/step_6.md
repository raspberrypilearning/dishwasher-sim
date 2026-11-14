## La mettre dans le rack

Une fois le bol propre, laisse le joueur ou la joueuse le faire glisser dans le rack et marquer une assiette propre.

> [!TASK]
>
> Sélectionne le sprite `serviette` dans le panneau Sprite. Ajoute un script qui indique au joueur ou à la joueuse ce qu'il ou elle doit faire lorsque le bol est propre.
>
> <img src="images/cloth-thumb.png" alt="The cloth sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> +when I receive (clean v)
> +say [Now put it in the rack!] for (2) seconds
> ```
>
> **Vérifier :** Nettoie le bol. La serviette devrait te dire de le mettre dans le rack.

> [!TASK]
>
> Sélectionne le sprite `bol` dans le panneau Sprite. Démarrez son script assiette propre : jouer un son, retirer le savon de la serviette et rendre le bol glissable.
>
> <img src="images/bowl-thumb.png" alt="The bowl sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> +when I receive (clean v)
> +start sound (Coin v)
> +set [soap v] to [false]
> +set drag mode [draggable v]
> ```
>
> **Vérifier :** Nettoie de nouveau le bol. Tu devrais maintenant pouvoir le faire glisser.

> [!TASK]
>
> Continue le même script. Attends que le bol touche le sprite `rack`, puis rétrécis le bol pour qu'il ait l'air d'avoir été rangé.
>
> <img src="images/bowl-thumb.png" alt="The bowl sprite thumbnail." width="138" height="105" style="object-fit: contain;">
>
> ```blocks3
> when I receive (clean v)
> start sound (Coin v)
> set [soap v] to [false]
> set drag mode [draggable v]
> +wait until <touching (rack v)?>
> +repeat (60)
> +change size by (-2)
> end
> ```
>
> **Vérifier :** Nettoie le bol et fais-le glisser dans le rack. Il devrait rétrécir au contact du rack.

> [!TASK]
>
> Ajoute des blocs pour marquer le bol propre, cache-le et réinitialise-le pour une nouvelle manche.
>
> <img src="images/bowl-thumb.png" alt="The bowl sprite thumbnail." width="138" height="105" style="object-fit: contain;">
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
> +change [clean plates v] by (1)
> +hide
> +set size to (0) %
> +go to x: (0) y: (-140)
> +set [clean v] to [false]
> ```
>
> **Vérifier :** Mets le bol propre dans le rack. Il devrait disparaître et le score `assiettes propres`{:class="block3variables"} devrait augmenter.

> [!TASK]
>
> Au bas du script, diffuse un élément aléatoire de la liste `choses`{:class="block3variables"}. En utilisant la longueur de la liste, ce bloc continuera de fonctionner même après l’ajout d’autres éléments de vaisselle.
>
> <img src="images/bowl-thumb.png" alt="The bowl sprite thumbnail." width="138" height="105" style="object-fit: contain;">
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
> +broadcast (item (pick random (1) to (length of [stuff v])) of [stuff v])
> ```

> [!TASK]
>
> Clique sur le drapeau vert. Utilise le savon, frotte le bol, puis déplace-le dans le rack. Le score devrait augmenter et un nouveau bol sale devrait augmenter à partir de l'évier.
>
> <img src="images/bowl-costume-1.png" alt="The dirty bowl sprite." width="138" height="105" style="object-fit: contain;">
