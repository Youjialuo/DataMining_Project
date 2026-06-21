# Data Mining / Fouille de Données — Cours Complet Pas à Pas

## Partie 4 : Clustering (CM10) & Analyse en Composantes Principales (CM11)

**CY Cergy Paris Université — Dr. Fatiha Bousbahi**  
**Avec terminologie bilingue 中法对照**

---

## CM10 : Clustering / 聚类分析 — Classification Automatique / 自动分类

### 10.1 Position du Problème / 问题定位

**Clustering / 聚类 (Segmentation / Classification automatique) :**
- Apprentissage **non supervisé** / 无监督学习
- Objectif : Décomposer un ensemble de données en groupes (clusters) / 将数据集分解为有意义的组
- Soient N instances avec n attributs → partition en k clusters
- k peut être donné ou "découvert"

**Clustering vs Classification / 聚类 vs 分类 :**

| | Clustering / 聚类 | Classification / 分类 |
|---|---|---|
| **Labels** | Pas de labels / 无标签 | Labels connus / 有标签 |
| **Approche** | Groupes proches | Règle d'attribution |
| **Apprentissage** | Non supervisé | Supervisé |
| **Résultat** | Structure découverte | Règle appliquée |

### 10.2 Applications du Clustering / 聚类应用

- **Médecine** : Localisation de tumeurs cérébrales / 脑肿瘤定位
- **Environnement** : Zones terrestres similaires / 相似土地区域
- **Marketing** : Segmentation clients / 客户细分
- **Urbanisme** : Groupes d'habitations / 住房群组
- **Climat** : Modèles d'atmosphère et océan / 大气海洋模式
- **Biologie** : Gènes de même fonction / 同功能基因
- **Documents** : Regroupement par sujet / 按主题聚类

### 10.3 Qualité du Clustering / 聚类质量

**Un bon clustering / 好的聚类 :**
- Similarité intra-classe **ÉLEVÉE** / 类内相似度高
- Similarité inter-classe **FAIBLE** / 类间相似度低

Dépend de :
- Mesure de similarité utilisée / 使用的相似度度量
- Implémentation / 实现方式

### 10.4 Fonctions de Distance / 距离函数

Pour les attributs numériques / 数值属性 :
- Distance Euclidienne / 欧几里得距离 (h=2)
- Distance de Manhattan / 曼哈顿距离 (h=1)
- Distance de Minkowski / 闵可夫斯基距离 (générale)

**Distance entre clusters / 簇间距离 :**

| Méthode | Formule |
|---------|---------|
| ① Single link / 最短距离 | $\min\{d(i,j) \mid i \in K_1, j \in K_2\}$ |
| ② Complete link / 最长距离 | $\max\{d(i,j) \mid i \in K_1, j \in K_2\}$ |
| ③ Average / 平均距离 | $avg\{d(i,j) \mid i \in K_1, j \in K_2\}$ |
| ④ Centroïde / 质心距离 | $dist(C_1, C_2)$ |
| ⑤ Médoïde / 中心点距离 | $dist(M_1, M_2)$ |

### 10.5 Méthodes de Clustering / 聚类方法分类

1. **Partitionnement / 划分方法** : K-Means, K-Medoids (PAM)
2. **Classification Hiérarchique / 层次聚类** : groupes disjoints
3. **Nuées dynamiques / 动态聚类** : groupes disjoints
4. **Classification pyramidale / 金字塔分类** : groupes non disjoints

**Caractéristiques / 特征 :**
- Apprentissage non supervisé / 无监督
- Toutes les variables ont le même statut / 所有变量同等地位
- Pas de variable dépendante / 无因变量
- Problème : interprétation des clusters / 聚类解读

### 10.6 K-Means : Méthode des Centres Mobiles / K均值算法

#### 10.6.1 Concept de Base / 基本概念

Méthode de partitionnement : Partitionner D (n objets) en k clusters → minimiser la somme des distances au carré.

$$D = \sum_{j=1}^{k} \sum_{i \in C_j} ||x_i - c_j||^2$$

où $c_j$ est le centroïde du cluster $C_j$.

#### 10.6.2 Algorithme K-Means / K-Means算法步骤

```
1. Choisir k centres initiaux (aléatoirement) / 随机选择k个初始中心
2. Répéter :
   a) Assigner chaque point au centre le plus proche / 将每个点分配给最近的中心
   b) Recalculer les centroïdes (moyenne des points du cluster) / 重新计算质心
3. Jusqu'à convergence (centres inchangés) / 直到收敛（中心不再变化）
```

#### 10.6.3 Exemple Complet K-Means 1D / K-Means一维完整示例

Données : $A = \{6, 7, 8, 11, 12, 13, 18, 20, 22\}$, k = 3  
Centres initiaux : C1={6}, C2={7}, C3={8}

**Itération 1 :**

| | 6 | 7 | 8 | 11 | 12 | 13 | 18 | 20 | 22 |
|---|---|---|---|---|---|---|---|---|---|
| **C1:6** | 0 | 1 | 2 | 5 | 6 | 7 | 12 | 14 | 16 |
| **C2:7** | 1 | 0 | 1 | 4 | 5 | 6 | 11 | 13 | 15 |
| **C3:8** | 2 | 1 | 0 | 3 | 4 | 5 | 10 | 12 | 14 |

- C1 = {6}, C2 = {7}, C3 = {8, 11, 12, 13, 18, 20, 22}
- Nouveaux centres : C1=6, C2=7, C3=104/7=14.857

**Résultat après convergence (6 itérations) :**

| Cluster | Centre | Éléments |
|---------|--------|----------|
| Cluster 1 | 7 | {6, 7, 8} |
| Cluster 2 | 12 | {11, 12, 13} |
| Cluster 3 | 20 | {18, 20, 22} |

#### 10.6.4 Exemple K-Means 2D / 二维K-Means示例

Points : A1(2,10), A2(2,5), A3(8,4), B1(5,8), B2(7,5), B3(6,4), C1(1,2), C2(4,9)  
k = 3, centres initiaux : A1, B1, C1

**Résultat final (convergence en 3 itérations) :**

| Cluster | Centre | Éléments |
|---------|--------|----------|
| Cluster 1 | (3.67, 9) | {A1, B1, C2} |
| Cluster 2 | (7, 4.33) | {A3, B2, B3} |
| Cluster 3 | (1.5, 3.5) | {A2, C1} |

#### 10.6.5 Avantages & Inconvénients / 优缺点

**Avantages / 优点 :**
- Scalabilité / 可扩展 — traite de très grandes BD
- Complexité linéaire / 线性复杂度 O(n)
- Seuls les vecteurs des moyennes en mémoire centrale

**Inconvénients / 缺点 :**
- Lenteur relative (plusieurs passes)
- **Minimum local** / 局部最优
- Dépend du choix initial des centres / 依赖初始中心选择
- Peut dépendre de l'ordre des individus (MacQueen)

### 10.7 Clustering Hiérarchique / 层次聚类

#### 10.7.1 Principe / 原理

Construire un arbre binaire qui fusionne successivement des groupes de points similaires / 构建二叉树，逐级合并相似点组

> **Avantage vs K-Means :** nécessite UNIQUEMENT une mesure de similarité (pas de k à spécifier) / 不需要指定k

#### 10.7.2 CAH — Clustering Ascendant Hiérarchique / 层次凝聚聚类

**Algorithme / 算法 :**
1. Chaque point = son propre cluster singleton / 每个点自己的聚类
2. Répéter : Fusionner les deux groupes les plus proches / 合并最近的两个组
3. Jusqu'à : toutes les données dans un seul cluster / 直到所有数据合并为一个聚类

**Dendrogramme / 树状图 :**
- Arbre binaire décrivant les partitions imbriquées
- Le clustering est obtenu en **coupant le dendrogramme au niveau souhaité** / 在期望的水平切割树状图
- Chaque composante connexe forme un cluster

#### 10.7.3 Distance entre groupes / 组间距离

**Méthode de Ward / Ward方法 :**
Minimise l'augmentation de l'inertie intra-classe :

$$\Delta Ward(A,B) = \frac{|A| \cdot |B|}{|A| + |B|} \cdot ||\mu_A - \mu_B||^2$$

### 10.8 Sommaire Clustering / 聚类总结

- **Partitionnement** : K-Means (centroïdes), K-Medoids/PAM
- **Hiérarchique** : CAH (agglomératif), divisif
- La qualité dépend de la mesure de similarité
- K-Means : linéaire, scalable, mais minimum local

---

## CM11 : Analyse en Composantes Principales (ACP/PCA) / 主成分分析

### 11.1 Introduction / 引言

**Objectif / 目标 :** Explorer des données numériques
- Quels individus (observations) sont similaires ?
- Quelles variables sont liées ?

**ACP = PCA (Principal Component Analysis)**
→ Méthode d'analyse de données multivariées **la plus utilisée** / 最常用的多元数据分析方法
- Apprentissage NON supervisé / 无监督学习

### 11.2 Principe de l'ACP / PCA原理

> « Représenter au mieux dans un espace plus réduit des observations issues d'un espace plus grand »

- Simplification de la réalité / 简化现实
- Concentration d'information diluée / 浓缩稀释信息
- Description du maximum de variabilité dans un espace réduit / "在降维空间中描述最大变异性"

### 11.3 Domaines d'Application / 应用领域

- Réduction du nombre de variables explicatives / 减少解释变量
- Obtention de nouvelles variables non corrélées / 获得无关新变量
- Imagerie : compression, reconnaissance faciale / 图像压缩与人脸识别
- Biostatistique, marketing, sciences sociales / 生物统计、营销、社科

### 11.4 Concepts de Base / 基本概念

#### 11.4.1 Matrice de Données / 数据矩阵

$X = (x_{ij})_{n \times p}$ : n individus décrits sur p variables
- $x_i$ : ligne i de X (description du iᵉ individu)
- $x_j$ : colonne j de X (description de la jᵉ variable)

Nuage d'individus : n points dans $\mathbb{R}^p$ (chaque individu = 1 point)

#### 11.4.2 Centrage et Réduction / 中心化与标准化

**a) Centrage / 中心化 :**
$$y_{ij} = x_{ij} - \bar{x}_j$$
→ Colonnes de moyenne nulle
→ Translation du nuage (**ne change PAS les distances !**)

**b) Centrage-Réduction / 中心化-标准化 :**
$$z_{ij} = \frac{x_{ij} - \bar{x}_j}{\sigma_j}$$
→ Colonnes de moyenne 0 ET variance 1
→ Translation + normalisation (**CHANGE les distances**)

où :
- $\bar{x}_j = \frac{1}{n}\sum_i x_{ij}$ (moyenne)
- $\sigma_j^2 = \frac{1}{n}\sum_i (x_{ij} - \bar{x}_j)^2$ (variance)

> ⚠️ **Important / 重要 :**
> - Centrer ne change pas les distances entre individus
> - Centrer-réduire CHANGE les distances
> - Normaliser donne la même importance à toutes les variables / 标准化使所有变量在距离计算中具有相同权重

#### 11.4.3 Malédiction de la Dimension / 维度灾难

> « Au fur et à mesure que le nombre de variables augmente, la quantité de données nécessaire pour généraliser augmente de façon exponentielle. » — Charles Isbell, Georgia Tech

**Deux options pour réduire / 两种降维方式 :**
1. Élimination directe / 直接删除变量
2. **Extraction de variables / 变量提取** (ACP fait cela)

### 11.5 Algorithme ACP en 6 Étapes / PCA六步算法

**Entrée :** Dataset D avec N points et p dimensions  
**Sortie :** Données projetées en r ≤ p dimensions

```
Étape 1 : Calculer la moyenne μ et centrer les données / 计算均值并中心化
          x_new = (x_i − μ)

Étape 2 : Calculer la matrice de covariance de D centré / 计算协方差矩阵
          Cov ∈ ℝᵖˣᵖ

Étape 3 : Calculer les valeurs propres λ et vecteurs propres v / 计算特征值和特征向量
          Résoudre : det(Cov − λI) = 0

Étape 4 : Sélectionner les r plus grandes valeurs propres / 选择最大r个特征值
          保留其对应的特征向量

Étape 5 : Stocker les top r vecteurs propres dans B (p × r) / 将前r个特征向量存入矩阵B

Étape 6 : Projeter les données / 投影数据
          x_new = Bᵀ (x_old − μ)
          每个x_new ∈ ℝʳ
```

### 11.6 Rappel : Valeurs et Vecteurs Propres / 特征值与特征向量回顾

Pour une matrice carrée $A_{(n \times n)}$ :
$$Av = \lambda v$$
où $v \neq 0$ est le vecteur propre / 特征向量, $\lambda$ est la valeur propre / 特征值

**Exemple :**
$$A = \begin{bmatrix} 2 & 3 \\ 2 & 1 \end{bmatrix}, \quad v = \begin{bmatrix} 3 \\ 2 \end{bmatrix}$$
$$Av = \begin{bmatrix} 12 \\ 8 \end{bmatrix} = 4 \times \begin{bmatrix} 3 \\ 2 \end{bmatrix}$$
→ $\lambda = 4$ est une valeur propre, $v = [3; 2]$ est son vecteur propre

**Pour trouver λ et v :**
1. Résoudre $\det(A - \lambda I) = 0$ → polynôme de degré n
2. Racines du polynôme = valeurs propres λ
3. Pour chaque λ, résoudre $(A - \lambda I)v = 0$ → vecteur propre

### 11.7 Composantes Principales / 主成分

- **CP1 (PC1)** : Direction de la plus grande variance / 最大方差方向 → Le vecteur propre de la plus grande valeur propre
- **CP2 (PC2)** : Direction orthogonale à CP1 avec variance restante max → Deuxième plus grande valeur propre
- **CP3, CP4, ...** : De même

> En général, seules quelques directions capturent l'essentiel de la variabilité / 通常只有少数方向捕获大部分变异

### 11.8 Exemple Complet d'ACP / 完整PCA示例

**Données d'origine :**

| Point | X | Y |
|-------|---|---|
| 1 | 19 | 63 |
| 2 | 39 | 74 |
| 3 | 30 | 87 |
| 4 | 30 | 23 |
| 5 | 15 | 35 |
| 6 | 15 | 43 |
| 7 | 15 | 32 |
| 8 | 30 | 73 |

**Étape 1 :** Centrer — $\mu_x = 24.1$, $\mu_y = 53.75$

**Étape 2 :** Matrice de covariance de (X', Y') :
$$Cov = \begin{bmatrix} 85.8 & 121.3 \\ 121.3 & 551.1 \end{bmatrix}$$

**Étape 3 :** Valeurs propres $\lambda = \{56.1, 580.8\}$, vecteurs propres $v_1 = [0.2381, 0.9712]^T$, $v_2 = [-0.9712, 0.2381]^T$

**Étape 4 :** Choisir $\lambda_1 = 580.8$ (la plus grande variance), $v_1 = [0.2381, 0.9712]^T = B$

**Étape 5 :** Projeter : $x_{new} = 0.2381 \cdot X' + 0.9712 \cdot Y'$

**Résultats (coordonnées CP1) :** {7.8, 23.2, 33.7, −28.5, −20.4, −12.6, −23.3, 20.1}

→ Ces 8 valeurs 1D capturent le maximum de variance des données 2D !

### 11.9 Reconstruction / 重建原始数据

Pour reconstruire les données centrées :
$$(x', y') = X_{new} \times V^T$$

où V contient TOUS les vecteurs propres (avant élimination). La reconstruction est approximative si on a éliminé des CPs.

### 11.10 Bonnes Pratiques ACP / PCA使用建议

| ✓ À faire | ✗ À éviter |
|-----------|------------|
| ACP est très utile pour les datasets larges | Ne pas réduire les dimensions pour éviter le surapprentissage |
| Simple à appliquer | Ne pas appliquer ACP aveuglément avant le ML |
| Très souple — applicable à tout type de données quantitatives | Considérer ACP comme alternative si données d'origine ne fonctionnent pas bien |

### 11.11 Sommaire / 总结

| Concept | Description |
|---------|-------------|
| **ACP** | Réduction de dimension / 降维 |
| **Transformation** | Linéaire des données / 数据线性变换 |
| **Nouvelles variables** | Composantes Principales / 主成分 |
| **CP1** | Capte le max de variance / 捕获最大方差 |
| **Étapes** | centrer → covariance → λ/v propres → sélectionner → projeter |

---

*Fin de la Partie 4 — CM10 & CM11*
