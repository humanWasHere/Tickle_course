# Tickle (TCL) language education
Documentation about the scripting language Tickle (TCL)
## Introduction
Tcl (Tool Command Language) est un langage de script puissant et flexible, souvent utilisé pour le développement rapide d'applications, l'automatisation de tâches, et le prototypage. Tcl est connu pour sa simplicité et sa capacité à être intégré dans d'autres applications.

## Variables
### Définir une variable
```tcl
set ma_variable 0
```
### Définir une variable exécutable
```tcl
set ma_exec_variable [ma_fonction argument_1]
```
### Définir une autre variable
```tcl
set ma_variable 0
```
### Variables globales
Pour accéder à une variable globale à l'intérieur d'une procédure :
```tcl
set x 10

proc maProcedure {} {
    global x
    set x 20
}

maProcedure
puts $x  ;# Affiche 20
```
## Fonctions
### Définir une fonction
```tcl
proc ma_fonction { argument_1 argument_2 } {
    # Corps de la fonction
}
```
### Appeler une fonction
```tcl
set resultat [ma_fonction arg1 arg2]
```
### Exemple de fonction
```tcl
proc addition {a b} {
    return [expr {$a + $b}]
}

set resultat [addition 3 5]
puts "Le résultat est $resultat"
```
## Conditions
### If, elseif, else
```tcl
if {$direction == "X+"} {
    return [expr $X0_dbu + $PAS]
} elseif ($direction == "X-"} {
    return [expr $X0_dbu - $PAS]
} elseif {$direction == "Y+"} {
    return [expr $Y0_dbu + $PAS]
} elseif {$direction == "Y-"} {
    return [expr $Y0_dbu - $PAS]
}
```
### Switch
```tcl
switch $direction {
    "X+" {return [expr $X0_dbu + $PAS]}
    "X-" {return [expr $X0_dbu - $PAS]}
    "Y+" {return [expr $Y0_dbu + $PAS]}
    "Y-" {return [expr $Y0_dbu - $PAS]}
    default {puts "Direction inconnue"}
}
```
## Boucles
### While
```tcl
while {$argument_1 == 0} {
    # Corps de la boucle
}
```
### For
```tcl
for {set i 0} {$i < 10} {incr i} {
    puts "i vaut $i"
}
```
### Foreach
```tcl
set liste {1 2 3 4 5}
foreach element $liste {
    puts "Élément: $element"
}
```
## Listes
### Créer une liste
```tcl
set ma_liste [list 1 2 3 4 5]
```
### Accéder à un élément de la liste
```tcl
set premier_element [lindex $ma_liste 0]
puts "Premier élément: $premier_element"
```
### Ajouter un élément à la liste
```tcl
lappend ma_liste 6
```
### Longueur de la liste
```tcl
set longueur [llength $ma_liste]
puts "Longueur de la liste: $longueur"
```
## Dictionnaires
### Créer un dictionnaire
```tcl
set mon_dict [dict create cle1 valeur1 cle2 valeur2]
```
### Accéder à une valeur
```tcl
set valeur [dict get $mon_dict cle1]
puts "Valeur de cle1: $valeur"
```
### Ajouter ou modifier une entrée
```tcl
dict set mon_dict cle3 valeur3
```
### Supprimer une entrée
```tcl
dict unset mon_dict cle2
```
## Fichiers
### Lire un fichier
```tcl
set fichier [open "mon_fichier.txt" r]
set contenu [read $fichier]
close $fichier
puts $contenu
```
### Écrire dans un fichier
```tcl
set fichier [open "mon_fichier.txt" w]
puts $fichier "Ceci est une ligne de texte."
close $fichier
```
## Gestion des erreurs
### Utiliser catch pour gérer les erreurs
```tcl
if {[catch {commande_potentiellement_erronée} resultat]} {
    puts "Une erreur s'est produite: $resultat"
} else {
    puts "Commande réussie: $resultat"
}
```
## Autre
### Eval
La commande eval en Tcl est utilisée pour évaluer une liste de commandes Tcl. Elle permet d'exécuter des commandes dynamiques, c'est-à-dire des commandes qui sont construites ou modifiées au moment de l'exécution.
```tcl
eval {commande1 commande2 ...}
```
```tcl
set cmd {puts "Hello, World!"}
eval $cmd
```
### Manipulation d'objet
#### Création d'objet
```tcl
layout create $Mon_layout FEED_ME_GDS -dt_expand -preservePaths
```
#### Copier un objet
```tcl
eval layout copy $Mon_layout $my_handle $top 0 1000 [concat $Xmin $Ymin $Xmax $Ymax] 1
```
#### Supprimer un objet
```tcl
layout delete $my_handle
```
#### Vérifier l'existance d'un objet
```tcl
set check [$my_handle exists layer $layer_de_travail]
```
## Conclusion
Ce document fournit une introduction de base à la syntaxe et aux structures de contrôle du langage Tcl. Pour plus d'informations, consultez [la documentation officielle de Tcl](https://www.tcl.tk/doc/).
