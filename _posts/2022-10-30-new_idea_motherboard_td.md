---
layout: post
title: "Idée projet: Tower defense sur une carte mère"
summary: ""
excerpt : "TODO"
date: 2022-10-30 14:27:25 +0200
comments: true
---

# Motivation

Ca fait quelques temps que je réfléchis à faire un petit tower defense, mais ce n'est qu'après avoir rejoué à la
franchise Bloons TD (plus particulièrement le 6 qui était en promo) que j'ai eu envie de me lancer dedans.

# Idée de départ

Le jeu sera un tower defense, la carte sera une grille représentant une carte mère où chaque case est un trou.
Les tours seront des composants montés en surface (CMS) à installer sur la carte mère, elles aurons des formes et des
rayons d'actions différents.
Les ennemis seront des bugs (?) se déplaçant le long d'un cable reliant l'entrée (un port USB?) au processeur (base à
défendre). Comme dans tout tower defense, chaque tour pourra être évoluée.
Par ailleurs, en plus de l'argent qui servira à acheter et faire évoluer les tours, il y aura une autre ressource: les
ticks CPU.
Il y aura une jauge de ticks au niveau du CPU qui se rempli en permanence en fonction de la fréquence de ce dernier (
exprimée en Hz), il sera possible d'améliorer le CPU suivant deux branches:

- fréquence: accélère la récupération de ticks
- capacité: augmente la taille de la jauge

Il y aura de même une jauge de ticks au niveau de chaque tour qui se remplira en consommant des ticks cpu. La vitesse de
remplissage de cette jauge déterminera la fréquence de déclenchement de la tour. Lorsque cette jauge sera au max elle se
déclenchera pour activer son effet.

Idée piquées à Bloons:

- pas de bar de vie, la force d'un ennemi est représenté par son sprite
- les caractéristiques d'un ennemi (vitesse, résistances) dépendent de son état
- un arbre d'amélioration pour chaque tour, les branches peuvent être exclusives
- cartes fixes
- vagues prédéfinies
- notion de type de dégâts, de résistance et d'immunité, peut être un système de roue des éléments (feu > air > terre >
  eau) ou de tableau des éléments (à la pokemon)
- notion d'ennemi caché: modificateur cheval de troie

# Objectif

J'aimerais garder les choses les plus simples possibles pour commencer.

A faire:

- **1 carte**
- **système d'argent**
- **système ressource CPU**
- **tours**:
    - *CPU*:
        - récupère des ticks
    - *Condensateur*:
        - 1pv par coup
        - dégâts de base (e.g. type neutre dans le système pokemon)
        - cible unique
        - portée moyenne
    - *Générateur d'IEM (Impulsion ElectroMagnétique)*:
        - 1pv par coup
        - dégâts de base
        - dégats en zone autour de la tour
        - portée faible
    - *CCE (Code Correcteur d'Erreur)*:
        - 1pv par coup
        - dégâts de base
        - cible unique
        - portée infinie
    - *Module RAM*:
        - aucun dégâts
        - boost toutes les tours dans une zone autour d'elle
        - boost initial: augmentation de la fréquence de déclenchement
        - cette tour n'ayant pas d'effect actif au déclenchement, elle consomme une quantité fixe de ticks de manière
          permanente
- **améliorations pour chaque tour**: deux branches par tour avec 2 améliorations dans chaque, possible de prendre les 2
  améliorations 1 de chaque branche mais une seule amélioration 2 (tour 2-1 ou 1-2 mais pas 2-2)
    - *CPU*:
        - récupération de ticks plus rapide (upgrade infini)
        - capacité de stockage de ticks plus élevée (upgrade infini)
    - *Condensateur*:
        - déclenchement plus fréquent > 2 pv par coup
        - plus de portée > ricochet vers 1 cible supplémentaire
    - *Générateur d'IEM*:
        - zone plus grande > 2 pv par coup
        - portée plus grande > capacité active: déclenchement n'importe ou sur la carte (même zone mais ciblage à la
          souris)
    - *CCE*:
        - 2 pv par coup > 4 pv par coup
        - déclenchement plus fréquent > retire "cheval de troie" aux ennemis touchés
    - *Module RAM*:
        - zone d'effet plus grande > réduction des coûts d'achat/évolution des composants dans la zone
        - réduction du coût fixe en CPU de cette tour > réduction des coût CPU des composants dans la zone
- **stratégies de ciblage**:
    - premier, dernier, proche, fort
    - modificateur "cheval de troie": permet en + de prioriser les chevaux de troie

# Nom

Il est temps de donner un nom à ce projet. Pour l'instant ce sera: **Corrupted Drive - Defense** ou CDD pour faire
court. 