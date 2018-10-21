# Technologie RAID

## Principe

Le RAID (Redundant Array of Independent Disks) est une technologie dont le but est d'améliorer les performances et / ou la tolérance aux fautes du système de stockage. Elle prepose sur une virtualisation du stockage sur plusieurs disques (magnétiques ou SSD). Le RAID peut être géré par un contrôleur dédié (on parle alors de RAID matériel) ou par le processeur de l'ordinateur (RAID logiciel). Les performance (débits, vitesse général de l'orindateur) sont généralement meilleurs dans le premier cas. Il existe également des  configurations intermédiaires ou le contrôleur ne prend en charge qu'une partie des opérations et où le processeur central est nécessaire.

Il existe plusieurs modes RAID qui diffèrent dans leur façon d'utiliser les différents disques constituant le grappe de stockage, ce qui immplique des performances différentes. Dans ce qui suit, nous allons aborder certains de ces modes et en présenter leurs principales caractéristiques.

Pour simplifier, on considérera que tous les disques utilisés ont la même taille.

## Modes « simples » : 0 et 1

![](figures/raid0.png)

*RAID 0*

Le mode RAID 0 consisite à utiliser en parallèle l'ensemble des disques de la grappe de stockage lors des opérations de lecture et d'écriture afin d'augmenter les débits. On parle d'agrégation de données par bande. Chaque fichier est découpé en plusieurs bandes qui sont répartis sur les différents disques constituant la grappe.Ainsi, sur l'exemple illustré par la figure ci-dessus, les bandes A1, A3, A5 et A7 sont copiés sur le disque 0 pendant que les bandes A2, A4, A6 et A8 le sont sur le disque 1.

Les débit sont multipliés par *n*, le nombre de disques. La capacité totale utilisable est la somme des capacités des disqques.
Ce mode RAID est sensible aux défaillances. En effet, la perte d'un disque entraîne la perte de la totalité des données du RAID.

![](figures/raid1.png) 

*RAID 1*

## Modes « composites »

![](figures/raid0p1.png) 

*RAID 0+1*

![](figures/raid1p0.png) 

*RAID 1+0*


## Un compromis : RAID 5

![](figures/raid5.png) 


*RAID 5*
