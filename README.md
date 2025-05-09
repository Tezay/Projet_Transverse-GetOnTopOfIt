Game presentation :
    Title : GetOnTopOfIt
    Contributors : Clément DRIESCH, Tom GARRIDO, Faustin MOUROT, Maxime LAURENT, Denyce NEGAi 
    Description : Un jeu de plateforme inspiré de Jump King et Celeste, où la progression se fait à travers différents "tableaux" divisant l’espace de jeu en plusieurs séquences avec une progression verticale.
    Main features : Système de scène dynamique/Trajectoire du bâton/Collision du bâton
    Technologies Used : Python avec le module pygame pour l'interface graphique, Git pour les dépots de groupe, Piksl pour les sprites, Notion pour la gestion de l'avancé du projet
    Installation : Cloner le dépot Git, installer python et le moduel pygame
    Use : Lancer le fichier main.py (python main.py)

Technical Documentation :
    Game Algorithm : 
        Le jeu est structuré autour d'une classe principale `Game` dans `main.py`.
        - Initialisation (`__init__`): Met en place Pygame, l'écran, et l'horloge.
        - Nouvelle partie (`new`): Prépare les objets du jeu (joueur, carte, groupes de sprites) et lance la boucle de jeu.
        - Boucle de jeu (`run`): Contient la logique principale : gestion des événements, mises à jour de l'état du jeu, et dessin à l'écran, répétée à chaque frame.
        - Événements (`events`): Traite les entrées utilisateur (clavier pour le mouvement et le saut, fermeture de la fenêtre).
        - Mise à jour (`update`): Appelle les méthodes `update` de tous les sprites actifs (joueur, plateformes si elles avaient un comportement dynamique). Le joueur gère sa propre physique (gravité, mouvement, collisions).
        - Dessin (`draw`): Efface l'écran et redessine tous les sprites à leur nouvelle position.

    Structure des fichiers :
        - `main.py`: Point d'entrée du jeu, classe `Game` gérant la boucle principale et l'orchestration.
        - `settings.py`: Contient toutes les constantes et configurations du jeu (dimensions de l'écran, couleurs, propriétés physiques, etc.).
        - `player.py`: Définit la classe `Player`, gérant son apparence, ses mouvements, sauts, la gravité et les collisions avec les plateformes.
        - `map.py`: Définit la classe `Map`. Actuellement, elle génère une carte simple de manière procédurale (via `MAP_DATA`) et crée les sprites `Platform`.
        - `sprites.py`: Contient les classes pour les objets du jeu, comme `Platform`. Chaque sprite gère sa propre image et son rectangle de collision.

    Functions details : 
        - `Player.update()`: Gère la logique de mouvement horizontal basée sur les entrées, applique la gravité, et appelle les fonctions de vérification de collision.
        - `Player.jump()`: Modifie la vélocité verticale du joueur pour initier un saut.
        - `Player.check_collision_x()` et `Player.check_collision_y()`: Détectent les collisions avec les plateformes et ajustent la position et la vélocité du joueur pour empêcher la pénétration et simuler l'arrêt ou l'atterrissage.
        - `Map.load_map()`: Itère sur une structure de données (une liste de chaînes de caractères) représentant la carte et instancie des objets `Platform` pour chaque tuile de plateforme.
        - `Game.run()`: Boucle principale qui maintient le jeu en fonctionnement, en appelant `events`, `update`, et `draw` à la fréquence définie par `FPS`.

    Input and Error Management :
        - Input : Les mouvements du joueur (gauche, droite) sont gérés par les touches fléchées gauche/droite ou Q/D. Le saut est géré par la barre d'espace, la flèche du haut ou Z. La touche Echap permet de quitter le jeu.
        - Error Management : La structure actuelle est basique et ne contient pas de gestion d'erreurs explicite avancée. La sortie du jeu est gérée proprement via `pg.quit()` et `sys.exit()`.
