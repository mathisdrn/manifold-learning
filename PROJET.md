---
title: Manifold Learning Overview
# short_title: Spam Detection
---

:::{table} Classification report of SVC model
:label: table_report_SVC1
:align: center
![](#table_report_SVC)
:::

La [](#figure_pr_SVC1) présente la courbe précision-rappel pour le modèle de SVC. Cette figure permet d'observer les compromis possible entre la précision et le rappel en fonction du seuil de décision.

:::{figure} #figure_pr_SVC
:label: figure_pr_SVC1
Precision-Recall Curve of SVC model
:::

La [](#figure_roc_SVC1) présente la courbe ROC pour le modèle SVC. On constate que l'aire sous la courbe est de $0,99$. L'aire sous la courbe est de $0.99$ ce qui indique une excellente performance du modèle.


:::{figure} #figure_roc_SVC
:label: figure_roc_SVC1
ROC Curve of SVC model
:::


+++ {"part": "data_availability"}
L'ensemble des fichiers et données relatif à ce travail sont disponible en accès libre sur le [dépot GitHub](https://github.com/mathisdrn/manifold-learning) sous licence MIT.
+++