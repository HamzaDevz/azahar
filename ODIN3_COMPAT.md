# Compatibilité Odin 3 : Azahar (3DS)

Notre propre liste de compatibilité, tenue d'après nos tests sur l'AYN Odin 3 (Snapdragon 8 Elite, Adreno 830) avec notre build de la branche `odin3`. Chaque test met à jour la ligne du jeu : statut, mesure, date et commit testé.

Autres émulateurs : [Eden (Switch)](https://github.com/HamzaDevz/eden/blob/odin3/ODIN3_COMPAT.md) · [Azahar (3DS)](https://github.com/HamzaDevz/azahar/blob/odin3/ODIN3_COMPAT.md) · [Dolphin (GC/Wii)](https://github.com/HamzaDevz/dolphin/blob/odin3/ODIN3_COMPAT.md) · [Cemu (Wii U)](https://github.com/HamzaDevz/Cemu/blob/odin3/ODIN3_COMPAT.md) · [Vita3K (Vita)](https://github.com/HamzaDevz/Vita3K/blob/odin3/ODIN3_COMPAT.md) · [aPS3e (PS3)](https://github.com/HamzaDevz/aps3e/blob/odin3/ODIN3_COMPAT.md) · [Bachata S4 (PS4)](https://github.com/HamzaDevz/bachata-s4/blob/odin3/ODIN3_COMPAT.md) · [xemu (Xbox)](https://github.com/HamzaDevz/xemu/blob/odin3/ODIN3_COMPAT.md)

## Échelle

| Statut | Sens |
|---|---|
| 🟢 Parfait | vu en partie, plein régime, aucun défaut vu |
| 🔵 Jouable | vu en partie, défauts mineurs |
| 🟡 Problèmes | vu en partie, défauts gênants (fps, graphismes, son) |
| 🟠 Menus/intro | démarre, pas encore vu en partie |
| 🔴 Ne marche pas | crash, écran noir ou blocage |
| ⚪ Non testé | présent sur la console, jamais lancé |

## Comment on teste

Paquet `org.azahar_emu.azahar.odin3`, lancé depuis ES-DE (règle `AZAHAR-ODIN3`) ou par adb. Notre build écrit chaque seconde `AzaharPerf: fps=… speed=… frame_ms=…` dans logcat quand l'overlay est coupé ; « fps » compte les soumissions GSP, la vraie cadence du jeu. Le banc lance le jeu, appuie sur A à l'aveugle et mesure environ 75 s : il voit le titre et l'intro, pas encore une partie. Depuis le 2026-10-22, le banc commun odin3-lab (`emus/azahar/`, local) rejoue aussi chaque test dans une VM qui simule la console, image par image.

Config globale (`config.ini`) : Vulkan, `async_shader_compilation = 1`, grand écran à gauche et écran tactile à droite (`layout_option = 2`, paysage forcé), œil droit coupé. Le premier lancement d'un jeu compile ses shaders ; au second (cache `shaders/vulkan/transferable/`), les saccades disparaissent presque.

## Jeux

Mesure : fps médian, vitesse moyenne (1,00 = plein régime) et vitesse minimale sur une seconde.

| Jeu | Statut | Vu jusqu'à | Mesure | Notes | Testé le | Build |
|---|---|---|---|---|---|---|
| Captain Toad: Treasure Tracker | 🟠 Menus/intro | titre, intro | 30 fps, vitesse 1,00, min 0,95 | 30 fps natifs | 2026-10-18 | 2fc8920e9 |
| Legend of Zelda: A Link Between Worlds | 🟠 Menus/intro | titre | 60 fps, vitesse 0,96, min 0,64 | banc bloqué à la saisie du nom : 10 s mesurées seulement | 2026-10-18 | 2fc8920e9 |
| Legend of Zelda: Majora's Mask 3D (EU) | 🟠 Menus/intro | titre | 29 fps, vitesse 0,89, min 0,20 | 7 s mesurées seulement, à refaire | 2026-10-18 | 2fc8920e9 |
| Legend of Zelda: Ocarina of Time 3D | 🟠 Menus/intro | titre, intro | 30 fps, vitesse 0,99, min 0,48 | 30 fps natifs | 2026-10-18 | 2fc8920e9 |
| Legend of Zelda: Tri Force Heroes | 🟠 Menus/intro | titre, intro | 60 fps, vitesse 0,99, min 0,60 | | 2026-10-18 | 2fc8920e9 |
| Luigi's Mansion | 🟠 Menus/intro | titre, intro | 30 fps, vitesse 0,99, min 0,47 (cache chaud) | à froid vitesse 0,95, min 0,23 | 2026-10-18 | 011e5df1b |
| Luigi's Mansion 2 | 🟠 Menus/intro | titre, intro | 60 fps, vitesse 0,99, min 0,78 (cache chaud) | le plus lourd (frame_ms 11-16) ; à froid min 0,02 sans shaders asynchrones, 0,84 avec | 2026-10-18 | 011e5df1b |
| Mario & Luigi: Dream Team Bros. | 🟠 Menus/intro | titre, intro | 30 fps, vitesse 0,99, min 0,47 | 30 fps natifs | 2026-10-18 | 2fc8920e9 |
| Mario & Luigi: Paper Jam Bros. | 🟠 Menus/intro | titre, intro | 30 fps, vitesse 1,00, min 0,99 (cache chaud) | à froid vitesse 0,95, min 0,23 | 2026-10-18 | 011e5df1b |
| Mario & Luigi: Superstar Saga + Bowser's Minions | 🟠 Menus/intro | titre, intro | 60 fps, vitesse 0,98, min 0,17 | à-coups au premier lancement (cache froid) | 2026-10-18 | 2fc8920e9 |
| Mario Kart 7 (EU) | 🟠 Menus/intro | titre, intro | 60 fps, vitesse 0,99, min 0,87 | | 2026-10-18 | 2fc8920e9 |
| Mario Party: Star Rush | 🟠 Menus/intro | titre, intro | 30 fps, vitesse 0,99, min 0,52 | 30 fps natifs | 2026-10-18 | 2fc8920e9 |
| Mario Party: The Top 100 | 🟠 Menus/intro | titre | 30 fps, vitesse 0,98, min 0,77 | 11 s mesurées seulement | 2026-10-18 | 2fc8920e9 |
| Mario Tennis Open | 🟠 Menus/intro | titre | 30 fps, vitesse 0,97, min 0,73 | 11 s mesurées seulement | 2026-10-18 | 2fc8920e9 |
| New Super Mario Bros. 2 | 🟠 Menus/intro | titre, intro | 60 fps, vitesse 0,99, min 0,64 | | 2026-10-18 | 2fc8920e9 |
| Paper Mario: Sticker Star | 🟠 Menus/intro | titre, intro | 30 fps, vitesse 1,00, min 0,72 | 30 fps natifs | 2026-10-18 | 2fc8920e9 |
| Super Mario 3D Land | 🟠 Menus/intro | titre, démo d'attraction (3000 images) | 59-60 présentations/s sur 50 s, 0 image perdue, deux runs | banc odin3-lab validé : la VM rend les mêmes images, décalées de 50 à 70 images (démarrage plus lent sur la console) ; une nouvelle partie bloque au sélecteur de Mii (aucun Mii dans la NAND) ; le jeu demande le micro au lancement (accordé) | 2026-10-22 | 011e5df1b |
| Super Smash Bros. for Nintendo 3DS (EU) | 🟠 Menus/intro | titre, intro | 60 fps, vitesse 0,99, min 0,80 | | 2026-10-18 | 2fc8920e9 |
| Monster Hunter 4 Ultimate (EU) | ⚪ Non testé | | | | | |
| `ctr-amhp.cci` (CTR-P-AMHP, 00040000000B1D00) | ⚪ Non testé | | | probablement Monster Hunter 3 Ultimate (EU) | | |

Aucun crash sur l'ensemble du banc. Prochaine étape : jouer chaque titre en partie (manette ou `input` adb) pour passer de 🟠 à un vrai statut.
