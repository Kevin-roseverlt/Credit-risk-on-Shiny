# Credit-risk-on-Shiny
Questionnaire interactif de prédiction du risque crédit, basé sur un arbre de classification (rpart) et une application R Shiny avec visualisation du chemin de décision.

# Questionnaire interactif de risque crédit

Application R qui prédit si un client est **risque** ou **non_risque** à partir
d'un arbre de classification, en posant uniquement les questions correspondant
au chemin suivi dans l'arbre.

## Objectifs
- Construire un arbre de classification sur une base de 1000 clients (variable cible : `profil`).
- Transformer cet arbre en questionnaire dynamique.
- Afficher le résultat : classe prédite, effectifs et probabilités de la feuille atteinte.

## Méthode
1. **Construction de l'arbre** avec `rpart` (critère de Gini), complexité choisie
   par validation croisée (`cp = 0.014667`, 8 splits).
2. **Conversion** de l'arbre avec `partykit` pour naviguer nœud par nœud.
3. **Application Shiny** : questionnaire à gauche, arbre interactif (`visNetwork`) à droite,
   chemin parcouru mis en couleur à chaque réponse.

## Technologies
R, rpart, rpart.plot, partykit, shiny, visNetwork

## Structure du projet
- `Questionnaire.Rmd` : analyse, construction de l'arbre et application Shiny
- `credit risque base app.csv` : données d'apprentissage

## Utilisation
1. Installer les packages : `install.packages(c("rpart", "rpart.plot", "partykit", "shiny", "visNetwork"))`
2. Ouvrir `Questionnaire.Rmd` dans RStudio et exécuter les chunks dans l'ordre.
3. Lancer `shinyApp(ui = ui, server = server)`.

## Limites
- Les probabilités viennent des effectifs d'apprentissage de chaque feuille
  (pas d'échantillon test séparé).
- Le choix du `cp` suit la règle du 1-SE, qui est indicative et non un test statistique.

## Auteur
Kevin Roseverlt
