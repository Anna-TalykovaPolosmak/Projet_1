# Projet_1

# Tableau de bord interactif pour l’entreprise : Ventes, Finances, Logistique et Ressources humaines

## Description du projet
Ce projet vise à créer un tableau de bord interactif et actualisable pour une entreprise afin de fournir des informations stratégiques sur quatre domaines clés : **ventes, finances, logistique et ressources humaines**.  
L’objectif est de permettre au directeur de l’entreprise de suivre les performances et de prendre des décisions éclairées grâce à des **indicateurs clés de performance (KPI)**.

Le tableau de bord a été développé à partir d’une base de données existante contenant des informations détaillées sur les employés, les produits, les commandes, etc.  
Le projet met en œuvre des techniques avancées de **visualisation des données** et d’**analyse des KPI** pour répondre aux besoins de l’entreprise.

---

## Objectifs du projet
1. **Faciliter la prise de décision** grâce à un tableau de bord centralisé regroupant des données actualisées chaque jour.  
2. **Automatiser l’analyse des indicateurs clés** sur les ventes, les finances, la logistique et les ressources humaines.  
3. **Améliorer la gestion de l’entreprise** grâce à des visualisations claires et des insights pertinents.

---

## Indicateurs clés de performance (KPI)

### 1. **Ventes**
- Chiffre d’affaires par année.  
- Comparaison et taux de variation des ventes par rapport au même mois de l’année précédente.  
- CA par catégorie de produits.  
- Les produits les plus et moins rentables.  
- Pourcentage d’atteinte de l’objectif annuel.  
- KPI sur les statuts des commandes.

### 2. **Finances**
- Délais de paiement, encours et impayés.  
- Exploration des risques d’impayés : tableau complet par client.  
- Les marges.  
- Les stocks.  

### 3. **Logistique**
- Taux de livraison.  
- Ratio du stock pour 2023.  

### 4. **Ressources humaines**
- Identification mensuelle des 2 meilleurs vendeurs ayant réalisé le plus de chiffre d’affaires.  
- Chiffre d’affaires par employé chaque mois.  
- Répartition géographique des clients par rapport aux bureaux.

---

## Ressources utilisées
- **Base de données existante de l’entreprise**, contenant :
  - Employés.  
  - Produits.  
  - Commandes.  
  - Autres informations pertinentes.  
- **Power BI** pour la création du tableau de bord interactif et l’automatisation des rapports.  
- **DAX (Data Analysis Expressions)** pour la création de mesures dynamiques et le calcul des KPI.  
- **SQL** pour l’extraction et la préparation des données nécessaires à partir de la base.  

---

## Résultats attendus
1. Un tableau de bord qui s’actualise automatiquement avec les nouvelles données chaque jour.  
2. Des insights exploitables dans les domaines des ventes, des finances, de la logistique et des ressources humaines.  
3. Une interface intuitive permettant au directeur de naviguer facilement entre les différents indicateurs.

---

## Structure du projet

### 1. Préparation des données
- Extraction des données pertinentes à partir de la base.  
- Nettoyage et transformation des données.  

### 2. Création des KPI
- Calcul des indicateurs obligatoires.  
- Ajout d’indicateurs personnalisés.  

### 3. Développement du tableau de bord
- Visualisation des données avec Power BI.  
- Mise en place de filtres interactifs (par année, mois, produit, etc.).  

### 4. Tests et déploiement
- Vérification de la cohérence des données.  
- Déploiement du tableau de bord pour un usage quotidien.  

---


## Comment utiliser le tableau de bord ?
1. Clonez ce dépôt sur votre machine locale.  
2. Importez le fichier `.pbix` (tableau de bord Power BI) dans Power BI Desktop.  
3. Assurez-vous que votre source de données est correctement connectée à la base de données de l’entreprise.  
4. Actualisez le tableau de bord pour charger les données les plus récentes.  
5. Explorez les visualisations et ajustez les filtres pour une analyse plus détaillée.  

---

## Aperçu du tableau de bord

Voici un aperçu de notre tableau de bord interactif :

La visualisation suivante montre une vue d'ensemble des indicateurs de performances de Ventes:
![Vue d'ensemble des indicateurs de performances de Ventes](https://github.com/Anna-TalykovaPolosmak/Projet_1/blob/main/Vente.png)

La visualisation suivante montre une vue d'ensemble des indicateurs de performances de Finance:
![Vue d'ensemble des indicateurs de performances de Finance](https://github.com/Anna-TalykovaPolosmak/Projet_1/blob/main/Finance.png)
![Vue d'ensemble des indicateurs de performances de Finance](https://github.com/Anna-TalykovaPolosmak/Projet_1/blob/main/In_Finance.png)

La visualisation suivante montre une vue d'ensemble des indicateurs de performances de Logistique:
![Vue d'ensemble des indicateurs de performances de Logistique](https://github.com/Anna-TalykovaPolosmak/Projet_1/blob/main/In_Logistique.png)
![Vue d'ensemble des indicateurs de performances de Logistique](https://github.com/Anna-TalykovaPolosmak/Projet_1/blob/main/Logistique.png)
La visualisation suivante montre une vue d'ensemble des indicateurs de performances de RH:
![Vue d'ensemble des indicateurs de performances de RH](https://github.com/Anna-TalykovaPolosmak/Projet_1/blob/main/In_RH.png)
![Vue d'ensemble des indicateurs de performances de RH](https://github.com/Anna-TalykovaPolosmak/Projet_1/blob/main/RH.png)

---

### Requêtes SQL utilisées pour le tableau de bord

code SQL dans le document code SQL

---

## Petite introduction
# Tableau de bord interactif - "Toys and Models"

## Description du projet

Ce dashboard a été conçu pour fournir une vue d'ensemble complète des performances commerciales de l'entreprise **Toys and Models**. L'objectif est de permettre au directeur de suivre les performances de l'entreprise à travers des indicateurs clés, afin de prendre des décisions éclairées et d'ajuster les stratégies en fonction des résultats.

### Aperçu du dashboard

Dans la partie supérieure du tableau de bord, nous avons les principaux KPI de l'entreprise. Ces indicateurs nous offrent une vue rapide de l’activité et du rendement de l’entreprise.

1. **Chiffre d'affaires par année**  
   L’évolution du chiffre d'affaires par année est représentée par des colonnes. Ces pourcentages représentent l'évolution des ventes par rapport à la même période de l'année précédente. En 2023, nous avons enregistré une croissance de **30,82 %** par rapport à 2022, avec un chiffre d'affaires de **4,22 millions de dollars**. Pour 2024, jusqu’à maintenant, nous avons généré **1 million de dollars**, avec un potentiel de croissance pour le reste de l'année.

2. **Chiffre d'affaires mensuel et comparaison**  
   À droite, un graphique du chiffre d'affaires mensuel permet de voir les variations saisonnières et les mois où les ventes étaient particulièrement élevées, comme novembre et décembre. Cette vue nous aide à anticiper les périodes de forte demande, telles que Noël et le Nouvel An, et à ajuster notre stratégie en conséquence.

3. **Chiffre d'affaires par catégorie de produit**  
   Le chiffre d'affaires est décomposé par catégorie de produit. Cette information nous aide à identifier quelles catégories de produits sont les plus rentables et où nous pourrions concentrer nos efforts de marketing.

4. **Performance annuelle par rapport au plan**  
   En bas à gauche, nous voyons un indicateur de performance : notre chiffre d'affaires actuel est de **610 000 dollars**, soit **10 %** de notre objectif annuel de **6 millions de dollars**. Cet indicateur nous montre l’avancement par rapport au plan et aide à évaluer si nous sommes sur la bonne voie pour atteindre nos objectifs de l’année.

5. **Analyse des produits les plus populaires**  
   Cette vue nous permet de voir quels produits sont les plus populaires et de mieux comprendre les préférences des clients.

6. **Problématique des produits les moins rentables**  
   Nous avons identifié une problématique liée aux produits les moins rentables. Ces produits génèrent un chiffre d'affaires relativement faible par rapport à d'autres produits plus rentables. Cette situation peut être due à plusieurs facteurs, tels que la demande limitée, des coûts de production élevés ou des marges bénéficiaires faibles. 

   **Solutions proposées :**
   - Analyser plus en détail la demande et les coûts de production de ces produits.
   - Ajuster la stratégie de marketing pour promouvoir les produits plus rentables.

7. **Problématique des produits non livrés**  
   Un autre point à souligner est lié aux produits non livrés. Bien que **95,84 %** des commandes aient été livrées, les autres sont en statut "Annulé", "Résolu" ou "En attente". Cette situation nécessite notre attention et demande une collaboration entre différents départements pour être résolue.



