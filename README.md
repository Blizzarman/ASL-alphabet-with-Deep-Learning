# 📌 ASL Recognition - Deep Learning Project

## 🏆 Objectif du projet  
Ce projet vise à faciliter la communication entre les personnes pratiquant la langue des signes américaine (ASL) et celles qui ne la connaissent pas. Il repose sur un modèle de **Deep Learning** capable de reconnaître les lettres de l'alphabet en **temps réel via une webcam**.

## 📂 Bases de données utilisées  
Deux ensembles de données ont été testés pour entraîner le modèle :  

### 1. **Base de données 1** 
- **Accès aux données** : [kaggle_bdd1](https://www.kaggle.com/datasets/grassknoted/asl-alphabet)
- **Caractéristiques** : Fond unique 
- **Objectif** : Faciliter l’apprentissage du modèle  
- **Taille** : 87 000 images, 29 classes (A-Z + "del", "nothing", "space")  

### 2. **Base de données 2**  
- - **Accès aux données** : [kaggle_bdd2](https://www.kaggle.com/datasets/lexset/synthetic-asl-alphabet)
- **Caractéristiques** : Fonds variés (nature, mur, ciel…), conditions réalistes  
- **Objectif** : Tester la robustesse du modèle  
- **Taille** : 27 000 images, 27 classes (A-Z + "blank")  

## 🛠️ Prétraitement des données  
Les images ont subi plusieurs transformations pour optimiser l’apprentissage :  
✅ **Redimensionnement** : 128x128 pixels  
✅ **Normalisation des pixels**  
✅ **Division des données** : Train / Validation / Test  
✅ **Batch size** : 32  

## 🔍 Modèle et architecture  
Un **réseau de neurones convolutif (CNN) personnalisé** a été conçu et appliqué aux deux bases de données.  

- **3 couches de convolution** avec :  
  - BatchNorm  
  - ReLU  
  - MaxPooling  
- **1 couche dense** de 512 neurones avec Dropout  
- **Sortie Softmax** pour la classification des classes  
- **Utilisation du GPU (`cuda`)** pour accélérer l'entraînement  

## 🚀 Expérimentations et optimisations  
🔹 **Transfert Learning** : Tests avec **AlexNet** et **VGG19** ✅  
🔹 **Optimisation des hyperparamètres** (optimiseur, taux d’apprentissage, fine-tuning) ❌ (aucune amélioration)  
🔹 **Data Augmentation** ❌ (pas d’amélioration)  
🔹 **Entraînement** :  
   - 20 époques max  
   - Early Stopping pour éviter l’overfitting  

## 📊 Résultats et performances 
Le modèle **CNN personnalisé** a obtenu des résultats optimaux sur la **base de données 1 (fond blanc)** avec une **précision de 99,2%**, tandis que les performances sur la **base 2 (fonds variés)** étaient légèrement inférieures (**96,7%**).  
Les modèles pré-entraînés **AlexNet** et **VGG19** ont été testés mais ont offert des performances inférieures, notamment sur la base 2, où ils ont atteint **58-60% de précision**.  

