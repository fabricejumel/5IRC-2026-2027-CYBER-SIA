# 5IRC-2026-2027-CYBER-SIA

# 🛡️ Adversarial Attacks & Robustness Evaluation on YOLOv8

Bienvenue sur ce dépôt dédié à l'étude de la robustesse des modèles de vision par ordinateur, et plus particulièrement aux attaques adversariales appliquées à **YOLOv8** (You Only Look Once, version 8).

---

## 🎯 1. Introduction à YOLOv8
**YOLOv8**, développé par [Ultralytics](https://github.com/ultralytics/ultralytics), est l'un des modèles de state-of-the-art les plus rapides et précis pour la détection d'objets, la segmentation d'instances et la classification. 
* 🧪 **Tester en ligne :** Vous pouvez tester les capacités de détection en temps réel via l'interface [Hugging Face Spaces - YOLOv8](https://huggingface.co/spaces/Ultralytics/YOLOv8).
* 📚 **Ressources Officielles :** Pour aller plus loin sur l'architecture, la structure des **datasets** (comme COCO) et l'entraînement de vos propres modèles, consultez la [documentation officielle d'Ultralytics](https://docs.ultralytics.com/).

--

## 🦠 2. L'Empoisonnement de Données (Data Poisoning)
L'empoisonnement de données est une attaque menée lors de la phase **d'entraînement** du modèle. Elle consiste à injecter ou modifier discrètement des échantillons dans le jeu d'entraînement pour :
* Introduire des portes dérobées (*backdoors*) qui déclenchent un comportement spécifique à la demande.
* Dégrader la qualité globale de l'apprentissage ou biaiser les performances de généralisation du réseau de neurones avant même sa mise en production.

---

## ⚡ 3. Les Attaques Adversariales à l'Inférence
Contrairement à l'empoisonnement, les attaques adversariales se produisent au moment de l'**inférence** (en phase de test). Elles exploitent la sensibilité des gradients du modèle entraîné pour manipuler la perception du réseau :
* Injecter des perturbations infimes ou des patchs ciblés dans l'image d'entrée.
* Faire chuter la **confiance** des prédictions.
* Provoquer des **faux négatifs** (faire disparaître des objets du radar de YOLO).
* Induire des faux positifs (hallucinations).

---

## 📂 4. Les Notebooks du Projet (Étude comparative)

Ce dépôt contient trois approches méthodologiques implémentées sous Google Colab pour évaluer la vulnérabilité de YOLOv8 :

1. **`Attaques_yolov8_FGSM.ipynb` (Fast Gradient Sign Method)**
   * *Principe :* Une attaque en une seule étape basée sur le signe du gradient de la loss par rapport à l'image d'entrée. Rapide mais facilement détectable.
2. **`Attaques_yolov8_PGD.ipynb` (Projected Gradient Descent)**
   * *Principe :* Une version itérative et plus puissante de FGSM. Elle projette les perturbations dans une epsilon-boule pour maximiser la destruction des prédictions de manière contrôlée.
3. **`Attaques_yolov8_EOM.ipynb` (Expectation Over Transformation / Patchs Furtifs & Style)**
   * *Principe :* L'implémentation de patchs adversariaux physiques localisés. Ce carnet intègre :
     * L'approche **EOT** pour simuler les variations de l'environnement réel (bruit de capture).
     * L'initialisation furtive basée sur les **pixels réels** de l'objet (vêtement) pour masquer l'attaque.
     * Une contrainte de style par **Total Variation (TV) Loss** pour lisser les textures et éviter les artéfacts numériques agressifs.

---

## 🚀 5. Conclusion & Perspectives : Robustesse en Conditions Réelles
Si ces travaux démontrent la vulnérabilité des modèles actuels face à des perturbations optimisées (patchs physiques, bruits subtils), la recherche en IA se tourne massivement vers la **défense et la robustesse**. 

Pour sécuriser ces systèmes en conditions réelles (véhicules autonomes, vidéosurveillance, etc.), les pistes actuelles incluent l'entraînement contradictoire (*Adversarial Training*), le renforcement des architectures et la purification des entrées.
* 💡 *Pour aller plus loin sur la défense robuste :* [OpenCV Adversarial Robustness Guide](https://opencv.org/).

---
*Créé et documenté dans le cadre de l'évaluation de la sécurité des architectures de Deep Learning.*
