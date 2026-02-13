@ Overview of all docuemntations projects

# Growth vs Value face aux variations des taux d’intérêt

Une approche économétrie & machine learning

# 1. Objectif du projet & Problématique

Ce projet étudie l’impact des taux d’intérêt sur la performance relative entre deux styles d’investissement : Growth et Value.
L’idée principale est de tester si les variations des taux d’intérêt, et pas seulement leur niveau, influencent la performance relative entre ces deux styles.

D’où notre question centrale :
Est-ce que les variations des taux d’intérêt expliquent et permettent de prédire la performance relative entre le Growth et le Value ?

Nous adoptons une double approche :

- une approche économétrique (OLS) pour expliquer la relation entre le spread Growth–Value et les taux,

- une approche de machine learning (Random Forest) pour tester le pouvoir prédictif de ces variables dans une logique d’arbitrage entre Growth et Value.

La variable clé étudiée est le spread, défini comme :

  Spread = Rendement Growth – Rendement Value

# 2. Données

Nous utilisons des données mensuelles sur la période 2014–2024 :

-VUG : ETF Vanguard représentatif du style Growth

-VTV : ETF Vanguard représentatif du style Value

-^FVX : Taux d’intérêt américain à 5 ans

Les données sont récupérées via la librairie Python yfinance.
À partir des prix, nous construisons :

-les rendements mensuels Growth et Value,

-le spread Growth – Value,

-le niveau du taux à 5 ans,

-la variation du taux (différence mensuelle),

-une mesure de volatilité du spread.

Les valeurs manquantes sont traitées par suppression ou remplacement par la médiane, conformément aux consignes du projet.

# 3. Analyse exploratoire

Une première analyse descriptive montre que :

-lors des périodes de forte hausse des taux (notamment autour de 2022), le spread devient souvent négatif, ce qui signifie une sous-performance du Growth par rapport au Value ;

-en séparant les périodes en deux régimes (taux en hausse vs taux en baisse), on observe que :

-le spread moyen est plutôt positif quand les taux baissent,

-et plutôt négatif quand les taux montent.

Cette analyse suggère que ce sont surtout les variations des taux qui jouent un rôle important dans la performance relative Growth vs Value.

# 4. Modélisation économétrique (OLS)

Nous estimons une régression linéaire du spread sur :

-le niveau du taux à 5 ans,

-la variation du taux à 5 ans.

Les résultats montrent que :

-le niveau du taux n’est pas statistiquement significatif,

-en revanche, la variation du taux a un coefficient négatif et significatif.

Cela signifie que ce sont principalement les hausses de taux qui pénalisent le Growth par rapport au Value, ce qui est cohérent avec la théorie financière de l’actualisation des cash-flows.

# 5. Approche Machine Learning & Stratégie

Nous utilisons un Random Forest Regressor pour prédire le spread du mois suivant à partir de :

-l’historique des rendements,

-le spread passé,

-la volatilité,

-le niveau et la variation des taux.

Les données sont séparées dans le temps entre :

-une période d’entraînement,

-et une période de test, afin d’éviter tout biais d’anticipation.

À partir des prédictions, nous construisons une stratégie simple :

-si le spread prédit est positif → investissement en Growth,

-sinon → investissement en Value.

Cette stratégie est comparée à deux benchmarks :

-Buy & Hold Growth,

-Buy & Hold Value.

Sur la période test, la stratégie :

-surperforme le Value en buy & hold,

-mais sous-performe le Growth en buy & hold.

L’analyse de l’importance des variables montre que la variation du taux fait partie des variables les plus importantes pour la prédiction, ce qui confirme son rôle central dans l’explication et la prévision du spread.

# 6. Interprétation et limites

Ce projet montre que :

-ce n’est pas tant le niveau des taux qui compte, mais surtout leurs variations,

-les chocs de taux ont un impact négatif sur la performance relative du Growth par rapport au Value.

Les principales limites sont :

-le nombre limité de variables macroéconomiques utilisées,

-l’absence de coûts de transaction dans la stratégie,

-et le fait que les rendements financiers restent par nature difficiles à prédire.

Des extensions possibles seraient d’ajouter d’autres variables macroéconomiques (inflation, croissance, spreads de crédit) ou de tester d’autres maturités de taux.

# 7. Structure du projet

data_processor.py : téléchargement, nettoyage et construction du dataset

econometric_analysis.py : estimation du modèle OLS et graphiques associés

ml_strategy.py : modèle Random Forest, backtest et visualisations

data/final_dataset.csv : dataset final utilisé pour les analyses
