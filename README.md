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
![Vue d'ensemble des indicateurs de performances de Ventes](C:/Users/annat/OneDrive/Документы/GitHub/Projet_1/Vente.png)

La visualisation suivante montre une vue d'ensemble des indicateurs de performances de Finance:
![Vue d'ensemble des indicateurs de performances de Finance](C:/Users/annat/OneDrive/Документы/GitHub/Projet_1/Finance.png)

La visualisation suivante montre une vue d'ensemble des indicateurs de performances de Logistique:
![Vue d'ensemble des indicateurs de performances de Logistique](C:/Users/annat/OneDrive/Документы/GitHub/Projet_1/Logistique.png)

La visualisation suivante montre une vue d'ensemble des indicateurs de performances de RH:
![Vue d'ensemble des indicateurs de performances de RH](C:/Users/annat/OneDrive/Документы/GitHub/Projet_1/RH.png)

---

### Requêtes SQL utilisées pour le tableau de bord

#### 1. **Requêtes SQL sur les Ventes**:

```sql
CREATE OR REPLACE VIEW Total AS (
    SELECT month(orderDate) AS mois, 
           year(orderDate) AS ans, 
           orderDate, 
           productLine, 
           productName, 
           customerNumber, 
           quantityOrdered, 
           status, 
           priceEach, 
           comments, 
           SUM(quantityOrdered * priceEach) AS CA_Total
    FROM orders, orderdetails, products
    WHERE (orders.orderNumber = orderdetails.orderNumber 
           AND orderdetails.productCode = products.productCode) 
    GROUP BY mois, ans, orderDate, productLine, productName, customerNumber, quantityOrdered, status, priceEach, comments
);
SELECT * FROM Total;

```sql
create or replace view Total AS (
                              SELECT month(orderDate) AS mois, year(orderDate) AS ans, orderDate, productLine, productName, customerNumber, quantityOrdered, status, priceEach, comments, SUM(quantityOrdered*priceEach) AS CA_Total
                              FROM orders, orderdetails, products
                              WHERE (orders.orderNumber= orderdetails.orderNumber AND orderdetails.productCode=products.productCode) 
                              Group by mois, ans, orderDate, productLine, productName, customerNumber, quantityOrdered,status, priceEach, comments
                              );
SELECT *
 from Total;

```sql
create or replace view vendus_3 AS (
                              SELECT month(orderDate) AS mois, year(orderDate) AS ans, orderDate, productLine, productName, customerNumber, quantityOrdered, status, priceEach, SUM(quantityOrdered*priceEach) AS CA
                              FROM orders, orderdetails, products
                              WHERE (orders.orderNumber= orderdetails.orderNumber AND orderdetails.productCode=products.productCode) AND status = "Shipped" 
                              Group by mois, ans, orderDate, productLine, productName, customerNumber, quantityOrdered, priceEach
                              ); 
SELECT *
 from vendus_3 ;

#### 2. **Requêtes SQL sur la Finance**:
```sql
SELECT date_format(orderdate, "%Y-%m-01") as year_month_,
SUM(quantityOrdered * priceEach) AS CA_enregistre,
    SUM(CASE
	WHEN status='Shipped' THEN quantityOrdered * priceEach
	ELSE 0
	END) AS CA_shipped,
	SUM(CASE
	WHEN status!='Shipped' THEN quantityOrdered * priceEach
	ELSE 0
	END) AS CA_non_shipped,
    ROUND((SUM(CASE
        WHEN status != 'Shipped' THEN quantityOrdered * priceEach
        ELSE 0
    END) / SUM(quantityOrdered * priceEach) * 100),2) AS pourcentage
    FROM orderdetails od
    JOIN orders ON orders.orderNumber = od.orderNumber
    GROUP BY year_month_
    ;
```sql
SELECT date_format(orderdate, "%Y-%m-01") as year_month_,
     SUM(quantityOrdered) AS qty_commandes_par_annee
    
    FROM orderdetails od
    JOIN orders ON orders.orderNumber = od.orderNumber
    GROUP BY year_month_;
```sql
WITH ca_produit AS(
	SELECT productCode,
        SUM(quantityOrdered*priceEach) AS CA_par_produit,
         SUM(quantityOrdered*buyprice) AS cout_par_produit,
        SUM(quantityOrdered) AS quantités_vendues_par_produit
	FROM orderdetails
    join products using(productcode)
	GROUP BY productCode
)
SELECT ca_produit.productCode AS code_produit, productLine,
		productName AS nom_du_produit,
        ca_produit.CA_par_produit,
        ca_produit.quantités_vendues_par_produit,
        ca_produit.CA_par_produit/ca_produit.quantités_vendues_par_produit AS prix_de_vente_moyen_par_produit,
        buyPrice,
        (ca_produit.CA_par_produit/ca_produit.quantités_vendues_par_produit)-buyPrice AS marge_moyenne_par_produit,
    
        
        ROUND(100*(((ca_produit.CA_par_produit/ca_produit.quantités_vendues_par_produit)-buyPrice)/buyPrice),2) AS taux_marge_moyenne,
        MSRP,
        ROUND(MSRP-(ca_produit.CA_par_produit/ca_produit.quantités_vendues_par_produit),2) AS remises,
		ROUND(100*((MSRP-(ca_produit.CA_par_produit/ca_produit.quantités_vendues_par_produit))/MSRP),2) AS taux_remises_MSRP,
        cout_par_produit,
        ca_par_produit - cout_par_produit as benef_par_prod
FROM products as p
JOIN ca_produit ON ca_produit.productCode = p.productCode
GROUP BY ca_produit.productCode,ca_produit.CA_par_produit,p.buyPrice
ORDER BY taux_remises_MSRP DESC;

#### 3. **Requêtes SQL sur la logistique**:

```sql
WITH country_employee AS (
	SELECT lastname, firstname,officeCode, jobtitle, city, country, employeeNumber
    FROM employees
    INNER JOIN offices USING (officecode)
),
	ca_2023 AS (
	SELECT customerName, city, country,salesRepEmployeeNumber, sum(quantityOrdered*priceEach) AS ca
	FROM customers
	JOIN orders USING(customerNumber)
	JOIN orderdetails USING(orderNumber)
	GROUP BY  customerName, city, country,salesRepEmployeeNumber
	ORDER BY customerName
)
SELECT country_employee.lastname,
	   country_employee.firstname,
       country_employee.officeCode,
       country_employee.jobtitle,
       country_employee.city,
       country_employee.country,
 ca_2023.ca
FROM country_employee
INNER JOIN ca_2023 ON country_employee.employeeNumber=ca_2023.salesRepEmployeeNumber
ORDER BY ca DESC, country_employee.country;

```sql
SELECT orderNumber, orderDate, shippedDate, `status`,  comments, count(`status`)
FROM `orders`
WHERE `status` != 'Shipped'
GROUP BY orderNumber, orderDate, shippedDate, `status`,  comments;

```sql
SELECT * from orders;

```sql
WITH stock2023 AS (
		SELECT  productName,productline,
				quantityInstock AS stock_act,
                round(quantityinstock * 365 / sum(quantityOrdered)*1.7 ) as ratio_stock,
				sum(CASE
                       when year(orderDate) = 2023 then quantityOrdered
                       else 0
                       end) as total_ordered_each_product2023
		FROM products
		LEFT JOIN orderdetails USING(productcode)
        LEFT JOIN orders USING (orderNumber)
        -- WHERE orderDate BETWEEN '2023-01-01' AND '2024-01-01'
        GROUP BY productName,quantityInstock,productline
      ),
      Inventory_value AS (
	SELECT productName,quantityInstock*buyprice AS value_stock
	FROM products
    )
SELECT
    stock2023.*,
    Inventory_value.value_stock
FROM stock2023
JOIN Inventory_value USING (productName)

#### 4. **Requêtes SQL sur le RH**:

```sql
with employees_chiffre_affaire as(
SELECT  concat(e.firstName, ' ', e.lastName) as nom,
        date_format(o.orderDate,"%Y-%m") as dates,
        d.officeCode, d.city, d.country,
		SUM(quantityOrdered*priceEach) AS Chiffre_Affaire,
rank() over(partition by date_format(o.orderDate,"%Y-%m") order by SUM(quantityOrdered*priceEach)) as rank_CA
FROM offices AS d
	JOIN employees AS e ON d.officeCode=e.officeCode
	JOIN customers AS c ON e.employeeNumber=c.salesRepEmployeeNumber
	join orders  AS o ON c.customerNumber=o.customerNumber
	JOIN orderdetails AS ord ON o.orderNumber=ord.orderNumber
where jobtitle like '%rep%'
group by e.firstName, e.lastName, d.officeCode, d.city, d.country, date_format(o.orderDate,"%Y-%m")
),
total_emp_offices as (
select officecode, count(distinct employeenumber) as total_vendeur_par_office from employees
left join offices using(officecode)
where jobtitle like '%rep%'
group by officecode)
select *, count(*) over(partition by dates) as total_vendeur_actif_mois
from employees_chiffre_affaire
join total_emp_offices USING(officecode);

```sql
with
customer_info as (
select  c.city, c.country, 'client' as category, SUM(quantityOrdered*priceEach) as chiffre_affaire
from customers as c
	JOIN orders  AS od ON c.customerNumber=od.customerNumber
	JOIN orderdetails AS ord ON od.orderNumber=ord.orderNumber
    group by c.city, c.country, category
),
 offices_info as (
select  o.city , o.country,'offices' as category, SUM(quantityOrdered*priceEach) as chiffre_affaire
from offices as o
	JOIN employees AS e ON o.officeCode=e.officeCode
	JOIN customers AS c ON e.employeeNumber=c.salesRepEmployeeNumber
	JOIN orders  AS od ON c.customerNumber=od.customerNumber
	JOIN orderdetails AS ord ON od.orderNumber=ord.orderNumber
    group by o.city, o.country, category
),
poid_bussness as (
select *
from offices_info
union
select *
from customer_info)
select *
from poid_bussness;


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



