# Technologie RAID

## Principe

Le RAID (Redundant Array of Independent Disks) est une technologie dont le but est d'améliorer les performances et / ou la tolérance aux fautes du système de stockage. Elle prepose sur une virtualisation du stockage sur plusieurs disques (magnétiques ou SSD). Le RAID peut être géré par un contrôleur dédié (on parle alors de RAID matériel) ou par le processeur de l'ordinateur (RAID logiciel). Les performance (débits, vitesse général de l'orindateur) sont généralement meilleurs dans le premier cas. Il existe également des  configurations intermédiaires ou le contrôleur ne prend en charge qu'une partie des opérations et où le processeur central est nécessaire.

Il existe plusieurs modes RAID qui diffèrent dans leur façon d'utiliser les différents disques constituant le grappe de stockage, ce qui immplique des performances différentes. Dans ce qui suit, nous allons aborder certains de ces modes et en présenter leurs principales caractéristiques.

Pour simplifier, on considérera que tous les disques utilisés ont la même taille.

## Modes « simples » : 0 et 1

![](figures/raid0.png)

*RAID 0*

Le mode RAID 0 consisite à utiliser en parallèle l'ensemble des disques de la grappe de stockage lors des opérations de lecture et d'écriture afin d'augmenter les débits. On parle d'agrégation de données par bande. Chaque fichier est découpé en plusieurs bandes qui sont répartis sur les différents disques constituant la grappe.Ainsi, sur l'exemple illustré par la figure ci-dessus, les bandes A1, A3, A5 et A7 sont copiées sur le disque 0 pendant que les bandes A2, A4, A6 et A8 le sont sur le disque 1.

Les débit sont multipliés par *n*, le nombre de disques. La capacité totale utilisable est la somme des capacités des disqques.
Le principal inconvénient de ce mode RAID est sa sensibilité aux défaillances. En effet, la perte d'un disque entraîne la perte de la totalité des données du RAID.

![](figures/raid1.png) 

*RAID 1*

On parle de disque en mirroir pour décire le mode 1. En effet, dans ce mode les disques du système de stockage contiennent exactement les même données. Une telle grappe constituée *n* disques tolère donc la perte de *n*-1 disques. Ce mode offre ddonc un très bons niveau de fiabilité. En contrepartie, l'espace de stockage utilisable ne correspond qu'à celui d'un disque et donc cette solution est relativement coûteuse, au regard de la capacité disponible.

## Modes « composites »

Il est possible de combiner les modes précédents afin d'atteindre une augmentation simultanées des débits et de la fiabilité.

![](figures/raid0p1.png) 

*RAID 0+1*

Dans le mode 0+1, on dispose de *m* grappes RAID 0 consituées chacune de *n* disques. Un contrôleur RAID 1 chapeaute ces grappes. Les débits sont multipliés par *n* tandis que la perte de la grappe est causée par la perte d'au moins un disque dans chacune des *m* grappes RAID 0. L'espace de stockage visible par l'utilisateur correspond à celui d'une grappe RAID 0, c'est à dire le contenu de *n* disques.

![](figures/raid1p0.png) 

*RAID 1+0*

Le mode 1+0 correspond à l'utilisation de *m* grappes RAID 1 de *n* disques chacune, et placées sous la supervision d'un contrôleur RAID 0. Pour obtenir un défaut global, il est nécessaire que tous les éléments d'une grappe soient défectueux.
Les débits sont multpliés par *m* et la taille des données stockables correspond à celle de *m* disques.


## Un compromis : RAID 5

![](figures/raid5.png) 

*RAID 5*

Le RAID 5 permet d'atteindre un certain compromis sur les aspects fiabilité et performances pour des coûts raisonnables. Ce mode reprend le principe des bandes du RAID 0, en y ajoutant des bandes supplémentaires de parité. Sur l'exemple illustré par la figure ci-dessus, les bandes Ap, Bp, Cp et Dp sont de telles bandes. En cas de perte du disque 3, il est possible de le remplacer par un nouveau disque. Les données des bandes B3, C3 et D3 sont alors reconstitués grâce aux bandes de parité Bp, Cp et Dp.

Dans une grappe RAID 5 de *n* disques, les débits sont multipliés par *n-1* et l'espace de stockage acessible correspond à celui de *n-1* disques. Le perte de l'ensemble des données du système est provoquée par la défaillance d'au moins deux disques.


