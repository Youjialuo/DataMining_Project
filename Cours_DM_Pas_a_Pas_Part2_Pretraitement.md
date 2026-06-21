# Data Mining / Fouille de Données — Cours Complet Pas à Pas

## Partie 2 : Prétraitement des données (Chapitre 3)

**CY Cergy Paris Université — Dr. Fatiha Bousbahi**  
**Avec terminologie bilingue 中法对照**

---

## Chapitre 3 : Prétraitement des Données / 数据预处理

### 3.1 Pourquoi Prétraiter ? / 为什么需要预处理？

**Les données réelles sont souvent / 现实数据通常是 :**
- **Incomplètes / 不完整** — valeurs manquantes / 缺失值
- **Bruitées / 有噪声** — erreurs et exceptions / 错误和异常
- **Incohérentes / 不一致** — nommage, codage / 命名、编码差异
- **Problèmes de crédibilité / 可信度问题** — données correctes ?
- **Problèmes d'interprétation / 可解释性问题** — facile à comprendre ?

> « Les résultats de la fouille dépendent de la qualité des données »  
> **"挖掘结果取决于数据质量" — Garbage In, Garbage Out**

### 3.2 Principales Tâches du Prétraitement / 预处理四大任务

| # | Tâche | Description |
|---|-------|-------------|
| ① | **Nettoyage des données / 数据清洗** | Remplir valeurs manquantes, lisser les données bruitées, identifier/supprimer outliers, résoudre les incohérences |
| ② | **Intégration des données / 数据集成** | Combiner plusieurs BD, cubes ou fichiers |
| ③ | **Réduction des données / 数据归约** | Réduction de la dimensionnalité / 降维, Réduction de la numérosité / 数量减少, Compression des données / 数据压缩 |
| ④ | **Transformation et discrétisation / 数据变换与离散化** | Normalisation / 归一化, Génération de hiérarchies de concepts / 概念分层生成 |

### 3.3 Nettoyage des Données / 数据清洗

#### 3.3.1 Données Incomplètes / 不完整数据

**Causes :** instrument défectueux, erreur humaine/informatique, erreur de transmission

**Exemples :**
- `Occupation=""` (valeur manquante)
- `Salaire="−10"` (erreur)
- `Age="42"` mais `date de naissance="03/07/2010"` (incohérence)
- 1er janvier comme date de naissance pour tout le monde

**Comment gérer les données manquantes ? / 如何处理缺失值？**

| Méthode | Description | Avantage / Inconvénient |
|---------|-------------|--------------------------|
| ❶ Ignorer le tuple / 忽略元组 | Supprimer les lignes incomplètes | Peu efficace si le % de valeurs manquantes est élevé |
| ❷ Compléter manuellement / 手动填充 | Saisie humaine | Laborieux ou infaisable |
| ❸ Constante globale / 全局常量 | Ex: « inconnue » comme nouvelle catégorie | Simple mais arbitraire |
| ❹ Moyenne de l'attribut / 属性均值 | Remplacer par la moyenne | Simple mais pas toujours optimal |
| ❺ **Moyenne pour la même classe / 同类均值** | Moyenne conditionnelle | **Meilleure approche** |
| ❻ **Valeur la plus probable / 最可能值** | Formule bayésienne ou arbre de décision | Plus sophistiqué |

#### 3.3.2 Données Bruitées / 噪声数据

**Techniques de lissage / 平滑技术 :**

**a) Binning / 分箱法 :**

Exemple : `{4, 8, 15, 21, 21, 24, 25, 28, 34}`

1. Trier / 排序
2. Partitionner en bins de taille égale :
   - Bin1 = {4, 8, 15}
   - Bin2 = {21, 21, 24}
   - Bin3 = {25, 28, 34}
3. Remplacer :
   - **Par la moyenne / 均值平滑** : {9, 22, 29}
   - **Par les bornes / 边界平滑** : {{4,4,15}, {21,21,24}, {25,25,34}}

> ⚠️ Implique une perte de précision / 精度损失

**b) Clustering / 聚类 :**
- Valeurs similaires dans une même classe
- On ignore les classes avec trop peu d'éléments

**c) Régression linéaire / 线性回归 :**
- Hypothèse : Y dépend linéairement de X
- $Y = aX + b$, remplacer les valeurs par celles prédites

### 3.4 Intégration des Données / 数据集成

#### 3.4.1 Problème d'Identification d'Entité / 实体识别问题

1. **Intégration de schéma / 模式集成** — Ex: `C_ID` dans BD Paris ↔ `CUST_ID` dans BD Londres
2. **Correspondance d'objets / 对象匹配** — Associer entités du monde réel de sources différentes

#### 3.4.2 Gestion de la Redondance / 冗余处理

**Données redondantes causes :**
- Même attribut avec noms différents
- Attribut dérivé (ex: chiffre d'affaires annuel)

**Détection par :**
- Analyse de corrélation / 相关性分析
- Analyse de covariance / 协方差分析

#### 3.4.3 Analyse de Corrélation — Données Nominales / 名义数据相关性

**Test χ² (卡方检验 / Khi-deux / Chi carré) de Pearson :**

$$\chi^2 = \sum \frac{(Observed - Expected)^2}{Expected}$$

- Plus χ² est grand, plus les variables sont liées
- **Corrélation n'implique PAS causalité / 相关≠因果 !**

**Exemple : Sexe et Lecture préférée sont-ils corrélés ?**

| | male | Female | Σ |
|---|---|---|---|
| **fiction** | 250 (90) | 200 (360) | 450 |
| **Non-fiction** | 50 (210) | 1000 (840) | 1050 |
| **Σ** | 300 | 1200 | 1500 |

$$\chi^2 = \frac{(250-90)^2}{90} + \frac{(200-360)^2}{360} + \frac{(50-210)^2}{210} + \frac{(1000-840)^2}{840}$$
$$= 284.4 + 71.1 + 121.9 + 30.5 = 507.93$$

Pour signification 0.001, χ² critique = 10.828  
**507.93 >> 10.828 → fortement corrélé !**

#### 3.4.4 Analyse de Corrélation — Données Numériques / 数值数据相关性

**Coefficient de corrélation de Pearson / 皮尔逊相关系数 :**

$$r(A,B) = \frac{\sum (a_i - \bar{A})(b_i - \bar{B})}{n \cdot \sigma_A \cdot \sigma_B} = \frac{\sum(a_i b_i) - n \cdot \bar{A} \cdot \bar{B}}{n \cdot \sigma_A \cdot \sigma_B}$$

- r > 0 → corrélation positive / 正相关
- r = 0 → indépendants / 独立
- r < 0 → corrélation négative / 负相关
- $-1 \leq r \leq +1$

#### 3.4.5 Covariance / 协方差

$$Cov = \frac{1}{n}\sum_{i=1}^{n} (a_i - \bar{A})(b_i - \bar{B})$$

- Cov > 0 → A et B augmentent ensemble / 同向变化
- Cov < 0 → A grand quand B petit / 反向变化
- Cov = 0 → indépendants (mais l'inverse n'est pas toujours vrai !)

**Exemple : Deux actions A et B en une semaine**

| | A | B |
|---|---|---|
| Jour 1 | 2 | 5 |
| Jour 2 | 3 | 8 |
| Jour 3 | 5 | 10 |
| Jour 4 | 4 | 11 |
| Jour 5 | 6 | 14 |

$\bar{A} = 4$, $\bar{B} = 9.6$

$$Cov = \frac{2\times5+3\times8+5\times10+4\times11+6\times14}{5} - 4\times9.6$$
$$= \frac{212}{5} - 38.4 = 42.4 - 38.4 = 4$$

→ Cov > 0, A et B augmentent ensemble

### 3.5 Réduction des Données / 数据归约

> **Objectif :** Garder uniquement les données pertinentes → Représentation réduite qui produit les mêmes résultats

#### 3.5.1 Réduction de la Dimensionnalité / 降维

**ACP — Analyse en Composantes Principales** (Voir Chapitre CM11 pour les détails complets)

- Idée : Trouver une projection qui capture la plus grande quantité de variation dans les données
- Vecteurs propres de la matrice de covariance
- Projeter sur un espace plus petit

**Sélection de sous-ensemble d'attributs / 属性子集选择 :**
- **Attributs redondants / 冗余属性** : dupliquent l'information — Ex: prix d'achat + montant de la taxe
- **Attributs non pertinents / 无关属性** : aucune information utile — Ex: n° de téléphone pour prédire un achat

**Méthodes de sélection :**
- Stepwise forward selection / 逐步向前选择
- Stepwise backward elimination / 逐步向后消除
- Combinaison des deux
- Arbre de décision (Decision tree induction)

#### 3.5.2 Réduction de la Numérosité / 数量归约

**Méthodes paramétriques / 参数方法 :**
- Régression linéaire / 线性回归
- Régression multiple / 多元回归
- Modèles log-linéaires / 对数线性模型
→ Seuls les paramètres sont stockés

**Méthodes non paramétriques / 非参数方法 :**

| Méthode | Description |
|---------|-------------|
| **Histogramme / 直方图** | Largeur égale / 等宽分箱 ou Fréquence égale / 等深分箱 |
| **Clustering / 聚类** | Stocker seulement centroïde et diamètre |
| **Échantillonnage / 抽样** | Voir ci-dessous |
| **Agrégation de cubes** | 数据立方体聚合 |

**Types d'échantillonnage / 抽样类型 :**
- Aléatoire simple / 简单随机抽样
- Sans remplacement / 不放回抽样
- Avec remplacement / 放回抽样
- En grappe / 整群抽样
- **Stratifié / 分层抽样** : partition + tirage proportionnel

**Échantillonnage stratifié — Exemple complet :**
1. Diviser la population en strates homogènes
2. Chaque individu fait partie d'UNE SEULE strate
3. Déterminer la proportion de chaque strate — Ex: Strate A: 15/40=0.375, Strate B: 20/40=0.5, Strate C: 5/40=0.125
4. Taille d'échantillon n=8 → A: 0.375×8=3, B: 0.5×8=4, C: 0.125×8=1
5. Tirage aléatoire dans chaque strate

#### 3.5.3 Compression des Données / 数据压缩

- **Sans perte (lossless) / 无损压缩** : manipulation limitée
- **Avec perte (lossy) / 有损压缩** : audio/vidéo

### 3.6 Transformation des Données / 数据变换

> Pour éviter de privilégier les attributs de grande valeur (ex: salaire vs âge) / 避免偏向大数值属性

#### 3.6.1 Normalisation / 归一化

**❶ Normalisation Min-Max / 最小-最大归一化 :**

$$v' = \frac{v - min_A}{max_A - min_A} \times (new\_max_A - new\_min_A) + new\_min_A$$

*Exemple :* Revenu $12,000 ~ $98,000 normalisé dans [0, 1]  
$73,000 → (73000−12000)/(98000−12000) = 61000/86000 ≈ **0.716**

**❷ Normalisation Z-Score / Z分数归一化 :**

$$v' = \frac{v - \mu_A}{\sigma_A}$$

*Exemple :* μ = $54,000, σ = $16,000  
$73,000 → (73000−54000)/16000 = **1.225**

**❸ Normalisation par échelle décimale / 小数定标归一化 :**

$$v' = \frac{v}{10^j} \quad \text{où j = le plus petit entier tel que max(|v'|) < 1}$$

*Exemple :* A = −986 à 917, max absolue = 986 → j = 3 → $v' = v/1000 \in [-0.986, 0.917]$

#### 3.6.2 Discrétisation / 离散化

Diviser la plage d'un attribut continu en intervalles / 将连续属性划分成区间

- Supervisée / 有监督 vs Non supervisée / 无监督
- Top-down (split) vs Bottom-up (merge)
- Se préparer pour la classification

*Exemple :* ($0...$200] → ($0...$100], ($100...$200]

#### 3.6.3 Génération de Hiérarchie de Concepts / 概念分层

Pour données nominales :
`country → province/state → city → street`
(15 valeurs → 365 → 3567 → 674,339 valeurs distinctes)

### 3.7 Sommaire du Chapitre 3 / 第3章总结

| Domaine | Points clés |
|---------|-------------|
| **Qualité des données** | exactitude, exhaustivité, cohérence, actualité, crédibilité, interprétabilité / 准确性、完整性、一致性、时效性、可信度、可解释性 |
| **Nettoyage** | valeurs manquantes, bruitées, outliers |
| **Intégration** | identification d'entité, redondances, incohérences |
| **Réduction** | dimensionnalité (ACP), numérosité (échantillonnage, histogrammes, clustering), compression |
| **Transformation** | normalisation (min-max, z-score, décimale), discrétisation, hiérarchies de concepts |

---

*Fin de la Partie 2 — Chapitre 3*
