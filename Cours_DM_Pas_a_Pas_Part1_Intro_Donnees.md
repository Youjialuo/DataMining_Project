# Data Mining / Fouille de Données — Cours Complet Pas à Pas

## Partie 1 : Introduction + Apprendre à connaître vos données (Chapitres 1-2)

**CY Cergy Paris Université — Dr. Fatiha Bousbahi**  
**Avec terminologie bilingue 中法对照**

---

## Chapitre 1 : Introduction au Data Mining / 数据挖掘导论

### 1.1 Définition du Data Mining / 数据挖掘定义

**Data Mining** / Fouille de données / Exploration de données  
数据挖掘 = 数据开采 = 数据探索

> **Définition classique (Han, Kamber & Pei, 2012) :**  
> « Extraction de modèles ou de corrélations significatives (implicites, auparavant inconnus et potentiellement utiles) à partir de grands volumes de données. »

**Autres noms équivalents / 等价名称 :**
- KDD — Knowledge Discovery in Databases / 数据库知识发现
- Business Intelligence (BI) / 商业智能
- Le data mining utilise des outils statistiques ET informatiques / 数据挖掘同时使用统计学和计算机工具

### 1.2 Références Fondamentales / 基础参考书

- **Jiawei Han, Micheline Kamber, Jian Pei** — *"Data Mining: Concepts and Techniques"*, 3rd Edition, Morgan Kaufmann, 2012
- **Pang-Ning Tan, Michael Steinbach, Vipin Kumar** — *"Introduction to Data Mining"*, 2nd Edition, Pearson

### 1.3 Historique / 历史发展

| Année | Événement |
|-------|-----------|
| 1990 | Apparition du concept de Data Mining / 数据挖掘概念出现 |
| 1993 | Arbre C4.5 (J. Ross Quinlan) / C4.5决策树 |
| 1996 | Bagging (Breiman) + Boosting (Freund-Shapire) |
| 1998 | SVM (Vladimir Vapnik) / 支持向量机 |
| 2001 | Régression logistique / 逻辑回归 |

### 1.4 Pourquoi le Data Mining ? / 为什么需要数据挖掘？

> « Nous sommes noyés dans les données, mais assoiffés de connaissances ! »  
> "我们被数据淹没，却渴望知识"

**Catalyseurs / 催化因素 :**
- Augmentation des capacités de stockage / 存储能力增强
- Augmentation des capacités de traitement / 处理能力增强
- Maturation des bases de données relationnelles / 关系数据库成熟
- Croissance explosive de la collecte (scanners, internet...) / 数据收集爆炸性增长
- Disponibilité via les réseaux (intranet, internet)
- Développement de logiciels spécialisés

### 1.5 Intérêt du Data Mining / 数据挖掘的价值

> « Trop d'information tue l'information » / 信息过多会扼杀信息

- Les entreprises sont inondées de données qui languissent dans les data warehouses (entrepôts de données / 数据仓库)
- Le DM renforce la capacité à découvrir des phénomènes et des tendances lucratives / 发现盈利趋势
- Augmente le ROI des systèmes d'information / 提高信息系统ROI

### 1.6 Applications / 应用领域

**CRM — Customer Relationship Management / 客户关系管理**
- Principe : améliorer la rentabilité par la connaissance du client / 原理：通过了解客户提高盈利能力
- CRM analytique : collecte et analyse / 分析型CRM
- CRM opérationnel : communication entreprise↔client / 操作型CRM
- Objectif : « Quel est leur profil ? Quels autres produits les intéresseront ? Quand seront-ils intéressés ? »

**Autres applications / 其他应用 :**
- Analyse et gestion des risques / 风险分析管理 — Scoring bancaire / 银行评分
- Fidélisation de la clientèle / 客户忠诚度
- Segmentation clients / 客户细分
- Web mining & E-commerce / 网络挖掘与电商
- Détection de fraude et outliers / 欺诈检测和异常检测
- Technologie / 技术领域：Reconnaissance faciale / 面部识别, Reconnaissance de la parole / 语音识别
- Médecine, industrie pharmaceutique / 医学制药 — Analyse ADN et bio-données
- Énergie, transport / 能源交通 — Prévision de consommation électrique, Prévision de trafic routier

### 1.7 Intégration de Multiples Disciplines / 多学科融合

```
           ┌──────────────┐
Machine ───┤              ├─── Statistiques
Learning    │ Data Mining  │    统计学
机器学习     │   数据挖掘    │
           ─┤              ├─
IA          │              │   Database
人工智能     └──────────────┘    数据库
                               Algorithmique 算法学
```

### 1.8 Distinction Statistiques vs Data Mining / 统计学与DM的区别

| Statistiques / 统计学 | Data Mining |
|----------------------|-------------|
| ① Définition et collecte des données | Utilise des techniques issues de l'IA / 使用AI技术 |
| ② Présentation en tableaux | Recherche parfois plus la compréhensibilité que la précision |
| ③ Analyse des données | Modèles plus localisés que ceux des statisticiens |
| ④ Comparaison avec des lois statistiques connues | Six types d'analyse (voir ci-dessous) |

**Six types d'analyse / 六种分析类型 :**
1. Description / 描述
2. Classification / 分类
3. Association / 关联
4. Estimation / 估计
5. Segmentation / 分割
6. Prévision / 预测

### 1.9 Panorama des Méthodes / 方法全景

```
Data Mining
    ├── Méthodes Descriptives / 描述性方法
    │     (Pas de variable cible / 无目标变量)
    │     • Visent à mettre en évidence des informations cachées
    │     • Réduisent, résument, synthétisent les données
    │     • Types : ① Description  ③ Association  ⑤ Segmentation
    │
    └── Méthodes Prédictives / 预测性方法 (Scoring)
          (Variable cible à prédire / 有目标变量)
          • Visent à extrapoler de nouvelles informations
          • Types : ② Classification (catégorie)  ④ Estimation (numérique)  ⑥ Prévision
```

### 1.10 Les Étapes du Data Mining / 数据挖掘步骤

1. **Inventaire, sélection et intégration des données / 数据盘点、选择与集成** → Déterminer les objectifs, choisir les variables
2. **Exploration et transformation des données / 数据探索与转换** → Statistiques descriptives, gestion des valeurs manquantes
3. **Analyse statistique : segmentation, régression, classement / 统计分析** → Phase de modélisation : sélectionner, calibrer, adapter
4. **Validation, visualisation et interprétation / 验证、可视化与解读** → Évaluer la qualité, valider sur données indépendantes

> **Résumé synthétique / 综合总结 :**
> 1. Poser le problème / 提出问题
> 2. Comprendre et préparer les données / 理解和准备数据
> 3. Appliquer des modèles et évaluer / 应用模型并评估
> 4. Faire un rapport de synthèse / 撰写综合报告

### 1.11 Outils Logiciels / 软件工具

- **R / Python** (open source)
- **TANAGRA** — logiciel gratuit pour l'enseignement et la recherche
- **ORANGE** — logiciel libre d'apprentissage et de DM
- **WEKA** — logiciel libre d'apprentissage et de DM
- **SAS, SPSS, RapidMiner** (commerciaux)

### 1.12 Problèmes Majeurs du DM / 数据挖掘主要问题

- Méthodologie de fouille / 挖掘方法学
- Extraction de différents types de connaissances / 从不同数据类型的知识提取
- Performance : efficacité et évolutivité / 效率与可扩展性
- Données incomplètes / 不完整数据
- Fusion des connaissances / 知识融合
- Visualisation des résultats / 结果可视化
- Sécurité et confidentialité / 安全与隐私保护

### 1.13 Mesures d'Intérêt / 有趣性度量

Un modèle est intéressant s'il est :
- **Facilement compris** par les humains / 易于人类理解
- **Valide** sur des données nouvelles / 在新数据上有效
- **Potentiellement utile** / 潜在有用
- **Nouveau** / 新颖

**Mesures :**
- **Objectives / 客观的** : basées sur statistiques (support, confidence...)
- **Subjectives / 主观的** : basées sur la croyance de l'utilisateur (inattendu, nouveauté...)

---

## Chapitre 2 : Apprendre à connaître vos données / 了解你的数据

### 2.1 Objets de Données et Types d'Attributs / 数据对象与属性类型

**Objet de données / 数据对象** — également appelé : 样本 (échantillon), 示例 (exemple), 实例 (instance), 点 (point), 元组 (tuple), 对象 (objet)

**Attribut / 属性** — également appelé : 维度 (dimension), 特征 (caractéristique), 变量 (variable)

#### 2.1.1 Types d'attributs / 属性类型

| | Qualitatif / 定性 (Catégorique / 类别) | Quantitatif / 定量 (Numérique / 数值) |
|---|---|---|
| **Opérations** | Les opérations mathématiques n'ont pas de sens | Les opérations mathématiques ont un sens |
| **Sous-types** | • Nominal / 名义<br>• Binaire / 二元<br>• Ordinal / 序数 | • Intervalle / 区间<br>• Ratio / 比率 |

**Discrète / 离散 vs Continu(e) / 连续 :**
- **Discrète** : ensemble fini ou dénombrable (codes postaux, profession, mots dans documents)
- **Continu** : nombres réels (température, taille, poids)

#### Types détaillés :

**① Nominal / 名义属性（标称属性）**
- Catégories, états ou "noms de choses"
- Ex: `Hair_color = {auburn, noir, blond}`, état civil, profession, n° ID, codes postaux

**② Binaire / 二元属性（二进制属性）**
- Attribut nominal avec seulement 2 états (0 et 1)
- *Binaire symétrique / 对称二元* : les 2 résultats importants — Ex: genre (M/F)
- *Binaire asymétrique / 非对称二元* : résultats d'importance inégale — Ex: test médical (positif/négatif)

**③ Ordinal / 序数属性（有序属性）**
- Valeurs avec ordre significatif, mais amplitude inconnue
- Ex: `Taille = {petit, moyen, grand}`, notes, classements de l'armée

**④ Intervalle / 区间属性**
- Échelle d'unités de taille égale, pas de vrai point zéro
- Ex: température en °C ou °F, dates du calendrier

**⑤ Ratio / 比率属性**
- Point zéro inhérent, on peut parler de rapport
- Ex: température Kelvin, longueur, comptes, quantités monétaires

### 2.2 Description Statistique des Données / 数据的统计描述

#### 2.2.1 Tendance Centrale / 集中趋势

**Moyenne / 均值 (Mean) :**
$$\bar{x} = \frac{1}{n}\sum_{i=1}^{n} x_i$$

**Médiane / 中位数 (Median) :**
- Valeur médiane si nombre impair
- Moyenne des 2 valeurs médianes si nombre pair

**Mode / 众数 :**
- Valeur la plus fréquente
- *Unimodale / 单峰* — 1 mode
- *Bimodale / 双峰* — 2 modes
- *Plurimodale / 多峰* — plusieurs modes

**Relation selon la distribution / 分布的关系 :**
- *Symétrique / 对称* : Moyenne ≈ Médiane ≈ Mode
- *Biaisée positivement / 正偏（右偏）* : Mode < Médiane < Moyenne
- *Biaisée négativement / 负偏（左偏）* : Moyenne < Médiane < Mode

#### 2.2.2 Dispersion des Données / 数据离散度

**Variance / 方差 :**
$$\sigma^2 = \frac{1}{N}\sum_{i=1}^{n}(x_i - \mu)^2$$

**Écart-type / 标准差 :** $\sigma = \sqrt{\sigma^2}$
- Grand σ → données étalées / 数据分散
- Petit σ → données proches de la moyenne / 接近均值
- σ = 0 seulement quand toutes les observations sont identiques

**Étendue / 极差 (Range) :** Max − Min

**Quartiles / 四分位数 :**
- **Q1** — 25ᵉ percentile / 第25百分位
- **Q2** — Médiane / 中位数 (50ᵉ percentile)
- **Q3** — 75ᵉ percentile / 第75百分位
- **EI (IQR)** = Q3 − Q1 / 四分位距

**Five-Number Summary / 五数概括 :** `{Minimum, Q1, Médiane, Q3, Maximum}`

**Boxplot / 箱线图 :**
- La boîte va de Q1 à Q3 / 箱子从Q1到Q3
- La médiane est marquée dans la boîte / 中位数在箱内
- Moustaches / 须线 : étendues à Min et Max
- **Outliers / 异常值** : points au-delà de 1.5×EI
  - Si valeur < Q1 − 1.5×EI → outlier bas
  - Si valeur > Q3 + 1.5×EI → outlier haut

#### 2.2.3 Affichages Graphiques / 图形显示

**Histogramme / 直方图 :**
- Axe x : classes (modalités) / x轴：类别
- Axe y : densité d'effectif ou densité de fréquence / y轴：频数密度
- Chaque classe → rectangle proportionnel à son effectif

**Nuage de points / 散点图 (Scatter plot) :**
- Aperçu des données bivariées / 双变量数据概览
- Groupes de points, outliers, relations
- Corrélation positive / 正相关 : points montent
- Corrélation négative / 负相关 : points descendent
- Non corrélé / 不相关

**Q-Q Plot / Q-Q图 (Quantile-Quantile plot) :**
- Quantiles d'une distribution vs quantiles d'une autre
- Détecte les glissements entre distributions

### 2.3 Visualisation des Données / 数据可视化

**Pourquoi visualiser ? / 为什么需要可视化？**
- Aperçu qualitatif de grands ensembles de données
- Recherche de modèles, tendances, structures, irrégularités / 搜索模式、趋势、结构、异常
- Trouver des régions intéressantes
- Preuve visuelle des représentations informatiques

**Techniques orientées pixels / 面向像素的可视化 :**
- Pour un dataset de m dimensions, créer m fenêtres
- Chaque enregistrement → m pixels correspondants
- Les couleurs reflètent les valeurs

### 2.4 Mesure de Similarité et Dissimilarité / 相似度与相异度

**Similarité / 相似度 :**
- Mesure numérique de la ressemblance entre 2 objets
- Plus élevée quand les objets se ressemblent davantage
- Souvent dans [0, 1]

**Dissimilarité / 相异度 :**
- Mesure numérique de la différence entre 2 objets
- Plus basse quand les objets se ressemblent
- Minimale souvent = 0
- Synonyme : distance

**Proximité / 邻近度** : terme générique

**Structures de données :**
1. **Matrice de données / 数据矩阵** — Objet × Attribut, n points de données avec p dimensions, matrice deux-mode / 双模矩阵
2. **Matrice de dissimilarité / 相异度矩阵** — Objet × Objet, matrice triangulaire, matrice un-mode / 单模矩阵

#### 2.4.1 Proximité pour Variables Nominales / 名义变量邻近度

$$d(i,j) = \frac{p - m}{p}$$

où m = # de correspondances / 属性匹配数, p = # total de variables / 属性总数

#### 2.4.2 Proximité pour Variables Binaires / 二元变量邻近度

**Tableau de contingence / 列联表 :**

| Objet i \ Objet j | 1 | 0 |
|---|---|---|
| **1** | q | r |
| **0** | s | t |

**Binaire symétrique / 对称二元 :**
$$d(i,j) = \frac{r + s}{q + r + s + t}$$

**Binaire asymétrique / 非对称二元 :**
$$d(i,j) = \frac{r + s}{q + r + s} \quad \text{(ignore t — les correspondances 0-0)}$$

**Coefficient de Jaccard (similarité pour asymétrique) :**
$$sim(i,j) = \frac{q}{q + r + s} = 1 - d(i,j)$$

#### 2.4.3 Proximité pour Variables Numériques / 数值变量邻近度

**Distance de Minkowski / 闵可夫斯基距离 :**
$$d(i,j) = \left( \sum |x_{ik} - x_{jk}|^h \right)^{1/h}$$

- **h = 1** → Distance de Manhattan / 曼哈顿距离 (L1 norm) : $d(i,j) = \sum |x_{ik} - x_{jk}|$
- **h = 2** → Distance Euclidienne / 欧几里得距离 (L2 norm) : $d(i,j) = \sqrt{\sum |x_{ik} - x_{jk}|^2}$

**Propriétés d'une métrique / 度量性质 :**
1. Non-négative : d(i,j) ≥ 0
2. Identité : d(i,i) = 0
3. Symétrie : d(i,j) = d(j,i)
4. Inégalité triangulaire / 三角不等式 : d(i,j) ≤ d(i,k) + d(k,j)

> **Comparaison Manhattan vs Euclidienne :** Dans ℝ², points séparés de 6 et 8 unités :
> - Manhattan = 6 + 8 = 14
> - Euclidienne = √(6²+8²) = 10
> - Manhattan supérieure de 40%

#### 2.4.4 Proximité pour Variables Ordinales / 序数变量邻近度

1. Remplacer $x_i$ par son rang $r_i \in \{1, ..., M\}$
2. Normaliser dans [0, 1] : $z_i = (r_i - 1) / (M - 1)$
3. Calculer la dissimilarité avec z (méthode numérique)

#### 2.4.5 Similarité Cosinus / 余弦相似度

$$\cos(x, y) = \frac{x \cdot y}{||x|| \times ||y||} = \frac{\sum x_i \times y_i}{\sqrt{\sum x_i^2} \times \sqrt{\sum y_i^2}}$$

- $\cos(\theta) \in [0, 1]$ pour vecteurs non négatifs
- $\cos(0°) = 1$ → vecteurs identiques
- $\cos(90°) = 0$ → vecteurs orthogonaux
- Très utilisé pour les documents textuels (TF vectors / 词频向量)
- Ignore les zéro-matches — idéal pour vecteurs creux / 稀疏向量

**Exemple de calcul / 计算示例 :**

```
d1 = (5, 3, 0, 2, 0, 0, 2, 0, 3, 0)
d2 = (3, 0, 0, 0, 0, 2, 0, 0, 1, 1)

||d1|| = √(5²+3²+2²+2²+3²) = √48 ≈ 6.93
||d2|| = √(3²+2²+1²+1²) = √15 ≈ 3.87
d1•d2 = 5×3 + 2×2 + 3×1 = 15+4+3 = 22

cos(d1,d2) = 22/(6.93×3.87) = 22/26.8 ≈ 0.82
```

#### 2.4.6 Dissimilarité pour Variables Mixtes / 混合变量相异度

$$d(i,j) = \frac{\sum \delta_{ij}^k \times d_{ij}^k}{\sum \delta_{ij}^k}$$

où $\delta_{ij}^k = 0$ si valeur manquante ou les deux = 0 (asymétrique), = 1 sinon.

---

## Activités Self-Study du Chapitre 2 / 第2章自学习练习

### Activité #1 : Attribut Nominal / 名义属性

Données :

| Obj ID | Test-1 | Test-2 | Test-3 |
|--------|--------|--------|--------|
| 1 | Code A | Excellent | 45 |
| 2 | Code B | Fair | 22 |
| 3 | Code C | Good | 64 |
| 4 | Code A | Excellent | 28 |

Pour Test-1 (nominal), d(i,j) = 0 si même catégorie, 1 sinon.

**Matrice de dissimilarité :**

| | 1 | 2 | 3 | 4 |
|---|---|---|---|---|
| **1** | 0 | | | |
| **2** | 1 | 0 | | |
| **3** | 1 | 1 | 0 | |
| **4** | 0 | 1 | 1 | 0 |

(1 et 4 sont Code A → d=0)

### Activité #2 : Variables Binaires Asymétriques / 非对称二元变量

Données :

| Name | Gender | Fever | Cough | Test-1 | Test-2 | Test-3 | Test-4 |
|------|--------|-------|-------|--------|--------|--------|--------|
| Jack | M | Y | N | P | N | N | N |
| Mary | F | Y | N | P | N | P | N |
| Jim | M | Y | P | N | N | N | N |

- Gender = symétrique (M/F également importants)
- Autres attributs = asymétriques binaires (Y et P = 1, N = 0)

Pour asymétrique : $d(i,j) = (r+s)/(q+r+s)$ [ignore t]

- **Jack-Mary** : q=3, r=0, s=1, t=3 → d = 1/4 = **0.25**
- **Jack-Jim** : q=3, r=0, s=1, t=3 → d = 1/4 = **0.25**
- **Mary-Jim** : q=2, r=1, s=1, t=3 → d = 2/4 = **0.5**

### Activité #3 : Variables Ordinales / 序数变量

Données (Test-2) : Excellent, Fair, Good, Excellent

1. Ordonner : Fair < Good < Excellent
2. Rangs : Fair=1, Good=2, Excellent=3 → Mf = 3
3. Normaliser dans [0,1] : z = (r−1)/(Mf−1) = (r−1)/2

| Obj | Test-2 | rang | z |
|-----|--------|------|---|
| 1 | Excellent | 3 | 1.0 |
| 2 | Fair | 1 | 0.0 |
| 3 | Good | 2 | 0.5 |
| 4 | Excellent | 3 | 1.0 |

**Matrice de dissimilarité (utilisant z) :**

| | 1 | 2 | 3 | 4 |
|---|---|---|---|---|
| **1** | 0 | | | |
| **2** | 1.0 | 0 | | |
| **3** | 0.5 | 0.5 | 0 | |
| **4** | 0.0 | 1.0 | 0.5 | 0 |

### Activité #5 : Similarité Cosinus / 余弦相似度

Matrice termes-documents :

| | T1 | T2 | T3 | T4 | T5 | T6 | T7 | T8 |
|---|---|---|---|---|---|---|---|---|
| **Doc1** | 0 | 4 | 0 | 0 | 0 | 2 | 1 | 3 |
| **Doc2** | 3 | 1 | 4 | 3 | 1 | 2 | 0 | 1 |
| **Doc3** | 3 | 0 | 0 | 0 | 3 | 0 | 3 | 0 |
| **Doc4** | 0 | 1 | 0 | 3 | 0 | 0 | 2 | 0 |
| **Doc5** | 2 | 2 | 2 | 3 | 1 | 4 | 0 | 2 |

cos(d1,d2) = (0×3+4×1+0×4+0×3+0×1+2×2+1×0+3×1) / (√(0+16+0+0+0+4+1+9) × √(9+1+16+9+1+4+0+1))
= 11 / (5.48 × 6.40) = 11 / 35.07 ≈ **0.31**

---

*Fin de la Partie 1 — Chapitres 1 & 2*
