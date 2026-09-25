# 5IRC-2026-2027-CYBER-SIA

# 🛡️ Adversarial Attacks & Robustness Evaluation on YOLOv8

Bienvenue sur ce dépôt dédié à l'étude de la robustesse des modèles de vision par ordinateur, et plus particulièrement aux attaques adversariales appliquées à **YOLOv8** (You Only Look Once, version 8).

---

## 🎯 1. Introduction à YOLOv8
**YOLOv8**, développé par [Ultralytics](https://github.com/ultralytics/ultralytics), est l'un des modèles de state-of-the-art les plus rapides et précis pour la détection d'objets, la segmentation d'instances et la classification. 
* 🧪 **Tester en ligne :** Vous pouvez tester les capacités de détection en temps réel via l'interface [Hugging Face Spaces - YOLOv8](https://huggingface.co/spaces/keremberke/yolov8).
* 📚 **Ressources Officielles :** Pour aller plus loin sur l'architecture, la structure des **datasets** (comme COCO) et l'entraînement de vos propres modèles, consultez la [documentation officielle d'Ultralytics](https://docs.ultralytics.com/).

---

## 🦠 2. Comprendre l'Empoisonnement de Données & les Attaques Adversariales
Contrairement aux erreurs classiques de classification, les **attaques adversariales** consistent à injecter des perturbations infimes (ou des patchs ciblés) dans l'image d'entrée afin de tromper le réseau de neurones sans altérer la compréhension humaine. 

Dans le cadre de l'**empoisonnement de données** et des attaques d'inférence, l'objectif est d'exploiter la sensibilité des gradients du modèle pour :
* Faire chuter la **confiance** des prédictions.
* Provoquer des **faux négatifs** (faire disparaître des objets du radar de YOLO).
* Induire des hallucinations (faux positifs).

---

## 📂 3. Les Notebooks du Projet (Étude comparative)

Ce dépôt contient trois approches méthodologiques implémentées sous Google Colab pour évaluer la vulnérabilité de YOLOv8 :

1. **`Attaques_yolov8_FGSM.ipynb` (Fast Gradient Sign Method)**
   * *Principe :* Une attaque en une seule étape basée sur le signe du gradient de la loss par rapport à l'image d'entrée. Rapide mais facilement détectable.
2. **`Attaques_yolov8_PGD.ipynb` (Projected Gradient Descent)**
   * *Principe :* Une version iterative et plus puissante de FGSM. Elle projette les perturbations dans une __epsilon-boule__ pour maximiser la destruction des prédictions de manière contrôlée.
3. **`Attaques_yolov8_EOM.ipynb` (Expectation Over Transformation / Patchs Furtifs & Style)**
   * *Principe :* L'implémentation de patchs adversariaux physiques localisés. Ce carnet intègre :
     * L'approche **EOT** pour simuler les variations de l'environnement réel (bruit de capture).
     * L'initialisation furtive basée sur les **pixels réels** de l'objet (vêtement) pour masquer l'attaque.
     * Une contrainte de style par **Total Variation (TV) Loss** pour lisser les textures et éviter les artéfacts numériques agressifs.

---

## 🚀 4. Conclusion & Perspectives : Robustesse en Conditions Réelles
Si ces travaux démontrent la vulnérabilité des modèles actuels face à des perturbations optimisées (patchs physiques, bruits subtils), la recherche en IA se tourne massivement vers la **défense et la robustesse**. 

Pour sécuriser ces systèmes en conditions réelles (véhicules autonomes, vidéosurveillance, etc.), les pistes actuelles incluent l'entraînement contradictoire (*Adversarial Training*), le renforcement des architectures et la purification des entrées.
* 💡 *Pour aller plus loin sur la défense robuste :* [OpenCV Adversarial Robustness Guide](https://opencv.org/) (ou littérature connexe sur l'adversarial training).

---
*Créé et documenté dans le cadre de l'évaluation de la sécurité des architectures de Deep Learning.*
