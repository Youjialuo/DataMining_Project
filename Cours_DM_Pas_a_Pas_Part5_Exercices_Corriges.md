# Data Mining / Fouille de Données — Cours Complet Pas à Pas

## Partie 5 : Exercices TD/TP Corrigés / 练习与答案

**CY Cergy Paris Université — Dr. Fatiha Bousbahi**  
**Avec terminologie bilingue 中法对照**

---

## TD Chapitre 2 : Statistiques Descriptives / 描述统计练习

### Exercice 1 : Boxplot (数据集1) / 箱线图

Données : `{1, 1, 3, 5, 6, 6, 7, 8, 12, 13, 15}`, n = 11 (impair)

| Statistique | Valeur |
|-------------|--------|
| Min | 1 |
| Q1 | position (11+1)/4 = 3ᵉ → **3** |
| Médiane (Q2) | position 2×(11+1)/4 = 6ᵉ → **6** |
| Q3 | position 3×(11+1)/4 = 9ᵉ → **12** |
| Max | 15 |
| EI (IQR) | 12 − 3 = 9 |
| 1.5×EI | 13.5 |

**Bornes pour outliers :**
- Inférieure : Q1 − 1.5×EI = 3 − 13.5 = −10.5
- Supérieure : Q3 + 1.5×EI = 12 + 13.5 = 25.5

→ **Aucun outlier** (toutes les valeurs dans [−10.5, 25.5])

**Five-Number Summary :** `{1, 3, 6, 12, 15}`

---

### Exercice 2 : Boxplot (数据集2) / 箱线图

Données : `{2, 3, 3, 6, 7, 7, 7, 9, 13, 15, 30}`, n = 11

| Statistique | Valeur |
|-------------|--------|
| Min | 2 |
| Q1 | 3 |
| Médiane | position 6ᵉ = **7** |
| Q3 | 13 |
| Max | 30 |
| EI (IQR) | 13 − 3 = 10 |
| 1.5×EI | 15 |

**Bornes :**
- Inférieure : 3 − 15 = −12
- Supérieure : 13 + 15 = 28

→ **30 > 28 : OUTLIER !** 30 est une valeur aberrante / 异常值

Boxplot : moustache supérieure s'arrête à 15, point outlier à 30

**Five-Number Summary :** `{2, 3, 7, 13, 30}` (其中30为异常值)

---

### Exercice 3 (Q2) : Note / 成绩统计

Données : `{4, 5, 9, 11, 12, 13, 13, 13, 13, 14, 15, 15, 16, 17, 18, 18, 19, 20}`, n = 18 (pair)

**(a) Moyenne et Médiane / 均值和中位数 :**
- Σ = 245
- **Moyenne** = 245/18 ≈ **13.61**
- **Médiane** = moyenne(9ᵉ, 10ᵉ) = moyenne(13, 14) = **13.5**

**(b) Mode / 众数 :**
- Valeur 13 apparaît 4 fois → **Mode = 13**
- C'est **UNIMODALE / 单峰** (une seule valeur dominante)

**(c) Midrange / 中列数 :**
- Midrange = (4 + 20)/2 = **12**

**(d) Quartiles / 四分位数 :**
- Q1 = médiane de la 1ʳᵉ moitié = 5ᵉ valeur = **12**
- Q3 = médiane de la 2ᵉ moitié = 14ᵉ valeur = **17**

**(e) Five-Number Summary :** `{4, 12, 13.5, 17, 20}`

---

### Exercice 4 (Q3) : Âge / 年龄统计

Données : `{13, 15, 16, 16, 19, 20, 20, 21, 22, 22, 25, 25, 25, 25, 30, 33, 33, 35, 35, 35, 35, 36, 40, 45, 46, 52, 70}`, n = 27 (impair)

**(a) Moyenne et Médiane :**
- Σ = 809 → **Moyenne** ≈ **29.96**
- Médiane = position 14ᵉ = **25**

**(b) Mode / 众数 :**
- 25 apparaît 4 fois, 35 apparaît 4 fois
- → **BIMODAL / 双峰** : Mode = {25, 35}

**(c) Midrange / 中列数 :**
- Midrange = (13+70)/2 = **41.5**

**(d) Quartiles / 四分位数 :**
- Q1 = médiane des 13 premières = 7ᵉ = **20**
- Q3 = médiane des 13 dernières = 21ᵉ = **35**

**(e) Five-Number Summary :** `{13, 20, 25, 35, 70}`

**(f) Boxplot / 箱线图 :**
- EI = 35 − 20 = 15
- 1.5×EI = 22.5
- Borne supérieure : 35 + 22.5 = 57.5
- **70 > 57.5 → OUTLIER !**
- Moustache supérieure à 52 (max non-outlier)

---

### Exercice 5 (Q4) : Âge et Graisse / 年龄与体脂

Données : 18 adultes, variables âge et graisse corporelle

**(a) Statistiques descriptives :**

| | Âge | Graisse |
|---|---|---|
| **Moyenne** | 836/18 ≈ **46.44** | 518.1/18 ≈ **28.78** |
| **Médiane** | moyenne(50,52) = **51** | moyenne(30.2,31.2) = **30.7** |
| **Écart-type σ** | ≈ **12.61** | ≈ **8.75** |

**(b) Boxplot :**
- Âge : Min=23, Q1≈29.5, Méd=51, Q3≈57.5, Max=61
- Graisse : Min=7.8, Q1≈25.9, Méd=30.7, Q3≈34.6, Max=42.5

---

### Exercice 6 (Q5) : Distance / 距离计算

Objets : (22, 1, 42, 10) et (20, 0, 36, 8)

**(a) Distance Euclidienne / 欧几里得距离 :**

$$d = \sqrt{(22-20)^2 + (1-0)^2 + (42-36)^2 + (10-8)^2} = \sqrt{4 + 1 + 36 + 4} = \sqrt{45} \approx \mathbf{6.71}$$

**(b) Distance de Manhattan / 曼哈顿距离 :**

$$d = |22-20| + |1-0| + |42-36| + |10-8| = 2 + 1 + 6 + 2 = \mathbf{11}$$

**(c) Distance de Minkowski (h=3) / 闵可夫斯基距离 :**

$$d = \sqrt[3]{|22-20|^3 + |1-0|^3 + |42-36|^3 + |10-8|^3} = \sqrt[3]{8 + 1 + 216 + 8} = \sqrt[3]{233} \approx \mathbf{6.15}$$

---

## TD Clustering : K-Means Solution Complète / K-Means完整解答

### Exercice 1 : K-Means 1D / 一维K-Means

Données : $A = \{6, 7, 8, 11, 12, 13, 18, 20, 22\}$, k = 3

**Résultat final (convergence en 6 itérations) :**

| Cluster | Centre | Éléments |
|---------|--------|----------|
| Cluster 1 | 7 | {6, 7, 8} |
| Cluster 2 | 12 | {11, 12, 13} |
| Cluster 3 | 20 | {18, 20, 22} |

*(Voir Partie 4, section 10.6.3 pour le détail complet des itérations)*

### Exercice 2 : K-Means 2D / 二维K-Means

Points : A1(2,10), A2(2,5), A3(8,4), B1(5,8), B2(7,5), B3(6,4), C1(1,2), C2(4,9)  
Centres initiaux : A1(2,10), B1(5,8), C1(1,2)

**Résultat final :**

| Cluster | Centre | Éléments |
|---------|--------|----------|
| Cluster 1 | (3.67, 9) | {A1, B1, C2} |
| Cluster 2 | (7, 4.33) | {A3, B2, B3} |
| Cluster 3 | (1.5, 3.5) | {A2, C1} |

---

## TD Clustering : CAH (Classification Ascendante Hiérarchique)

### Question 1 : Dendrogramme / 树状图绘制

**Principe :**
- Chaque fusion correspond à une jonction dans l'arbre
- La hauteur de la jonction = distance de fusion
- L'ordre horizontal des feuilles peut varier

### Question 2 : Nombre de Clusters / 聚类数量

Avec un seuil de coupure à 2.5 cm sur le dendrogramme :
1. Tracer une ligne horizontale à distance = 2.5
2. Compter les intersections → nombre de clusters
3. Chaque intersection = 1 cluster

### Question 3 : CAH avec Méthode de Ward / 用Ward方法的CAH

**Méthode de Ward :**
$$\Delta Ward(A,B) = \frac{|A| \cdot |B|}{|A| + |B|} \cdot ||\mu_A - \mu_B||^2$$

Fusionne les clusters qui minimisent l'augmentation de l'inertie intra-classe.

**Étapes :**
1. Chaque point = cluster singleton → matrice de distance
2. Trouver la distance minimale → fusionner
3. Mettre à jour la matrice de distance
4. Répéter jusqu'à un seul cluster
5. Construire le dendrogramme

---

## TP Clustering & ACP / 聚类与PCA实验

**Objectif :** Pratiquer K-means, CAH et ACP sur Scikit-learn

**Dataset :** `voit_dataset.xls` — 28 véhicules, 5 variables quantitatives  
Colonnes : `mpg, displacement, horsepower, weight, acceleration, origin`

| mpg | displacement | horsepower | weight | acceleration | origin |
|-----|-------------|------------|--------|-------------|--------|
| 35 | 72 | 69 | 1613 | 18 | japanese |
| 31 | 76 | 52 | 1649 | 17 | japanese |
| 39 | 79 | 58 | 1755 | 17 | japanese |
| 35 | 81 | 60 | 1760 | 16 | japanese |
| 31 | 71 | 65 | 1773 | 19 | japanese |

### Étapes du TP :

#### 1) K-Means :
- Standardiser les données (`StandardScaler`) / 标准化数据
- Choisir k (**méthode du coude / elbow method**) / 用肘部法则选择k
- Appliquer K-Means
- Visualiser les clusters (avec ACP pour 2D) / 用PCA降维到2D后可视化
- Interpréter les clusters / 解读聚类结果

#### 2) CAH (Clustering Hiérarchique) :
- Choisir une mesure de distance (euclidienne)
- Choisir un linkage (**Ward**)
- Construire et visualiser le dendrogramme
- Couper pour obtenir le nombre de clusters souhaité
- Comparer avec les résultats K-Means

#### 3) ACP (Analyse en Composantes Principales) :
- Standardiser les données
- Appliquer PCA (`sklearn.decomposition.PCA`)
- Analyser la variance expliquée par chaque composante (**scree plot / 碎石图**)
- Visualiser le **cercle de corrélation** / 相关性圆
- Projeter les individus sur les 2 premières CPs
- Interpréter les axes / 解读主轴

### Code Scikit-learn de Référence :

```python
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
from sklearn.decomposition import PCA
from scipy.cluster.hierarchy import dendrogram, linkage

# Standardisation
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

# K-Means
kmeans = KMeans(n_clusters=3, random_state=42)
clusters = kmeans.fit_predict(X_scaled)

# ACP
pca = PCA()
X_pca = pca.fit_transform(X_scaled)
print(pca.explained_variance_ratio_)  # variance expliquée

# CAH
Z = linkage(X_scaled, method='ward')
dendrogram(Z)
```

---

## Formulaire Rapide / 公式速查卡

### Statistiques Descriptives / 描述统计

| Concept | Formule |
|---------|---------|
| Moyenne / 均值 | $\bar{x} = \frac{1}{n}\sum x_i$ |
| Variance | $\sigma^2 = \frac{1}{n}\sum (x_i - \mu)^2$ |
| Écart-type / 标准差 | $\sigma = \sqrt{\sigma^2}$ |
| EI (IQR) / 四分位距 | $Q3 - Q1$ |
| Outlier / 异常值 | $x < Q1-1.5\times EI$ ou $x > Q3+1.5\times EI$ |

### Distances / 距离

| Distance | Formule |
|----------|---------|
| Manhattan | $d = \sum \|x_i - y_i\|$ |
| Euclidienne | $d = \sqrt{\sum (x_i - y_i)^2}$ |
| Minkowski | $d = (\sum \|x_i - y_i\|^h)^{1/h}$ |

### Similarité / 相似度

| Mesure | Formule |
|--------|---------|
| Cosinus | $\cos(x,y) = \frac{x \cdot y}{\|\|x\|\| \cdot \|\|y\|\|}$ |
| Jaccard (asym. binaire) | $sim = \frac{q}{q+r+s}$ |

### Règles d'Association / 关联规则

| Mesure | Formule |
|--------|---------|
| Support | $support(X \rightarrow Y) = \frac{count(XY)}{\|D\|}$ |
| Confiance | $confiance(X \rightarrow Y) = \frac{support(XY)}{support(X)}$ |
| Lift | $lift = \frac{support(XY)}{support(X) \times support(Y)}$ |

### Corrélation / 相关性

| Mesure | Formule |
|--------|---------|
| Pearson | $r(A,B) = \frac{\sum(a_i-\bar{A})(b_i-\bar{B})}{n \cdot \sigma_A \cdot \sigma_B}$ |
| Khi-deux | $\chi^2 = \sum \frac{(O-E)^2}{E}$ |
| Covariance | $Cov(A,B) = \frac{1}{n}\sum (a_i-\bar{A})(b_i-\bar{B})$ |

### Normalisation / 归一化

| Méthode | Formule |
|---------|---------|
| Min-Max | $v' = \frac{v-min}{max-min} \times (N_{max}-N_{min}) + N_{min}$ |
| Z-Score | $v' = \frac{v-\mu}{\sigma}$ |
| Décimale | $v' = \frac{v}{10^j}$ |

### ACP / PCA

1. Centrer : $x' = x - \mu$
2. Covariance : $Cov = \frac{1}{n} X'^T X'$
3. $\det(Cov - \lambda I) = 0$ → $\lambda$ (valeurs propres)
4. $(Cov - \lambda I)v = 0$ → $v$ (vecteurs propres)
5. Projection : $X_{new} = B^T(x - \mu)$, où $B = [v_1, v_2, ..., v_r]$ (top r vecteurs propres)

### K-Means

- Objectif : $\min \sum_j \sum_{i \in C_j} \|x_i - c_j\|^2$
- Centroïde : $c_j = \frac{1}{\|C_j\|} \sum_{i \in C_j} x_i$

---

## Table des Matières Complète / 完整目录

| Partie | Fichier | Contenu |
|--------|---------|---------|
| **Partie 1** | Part1_Intro_Donnees | Ch.1 Intro au DM, Ch.2 Apprendre à connaître vos données (types d'attributs, statistiques, similarité) |
| **Partie 2** | Part2_Pretraitement | Ch.3 Prétraitement (nettoyage, intégration, réduction, transformation) |
| **Partie 3** | Part3_MotifsFrequents | Ch.4 Motifs fréquents (Apriori, FP-Growth, ECLAT, Lift) |
| **Partie 4** | Part4_Clustering_ACP | CM10 Clustering (K-Means, CAH) + CM11 ACP/PCA |
| **Partie 5** | Part5_Exercices_Corriges | TD (Boxplot, Stats, Distances) + TD Clustering + TP + Formulaire |

---

*Fin du cours complet de Data Mining / 中法对照数据挖掘完整教程 — CY Cergy Paris Université*
