Exercices C++17 — Programmation Orientée Objet

Ce dépôt contient les solutions de trois exercices en C++17 :

Passage par valeur et par référence
Classes et encapsulation (gestion de comptes bancaires)
Héritage et polymorphisme (gestion de véhicules)
Structure du projet
.
├── ex1.cpp      # Exercice 1 : passage par valeur / référence
├── ex2.cpp      # Exercice 2 : classe CompteBancaire
├── ex3.cpp      # Exercice 3 : Vehicule, Voiture, Camion
└── README.md
Prérequis
Un compilateur compatible C++17 (g++ 7+, clang++ 5+, ou MSVC 2017+)
Compilation et exécution
bash
g++ -std=c++17 -Wall -Wextra ex1.cpp -o ex1 && ./ex1
g++ -std=c++17 -Wall -Wextra ex2.cpp -o ex2 && ./ex2
g++ -std=c++17 -Wall -Wextra ex3.cpp -o ex3 && ./ex3

Sous Windows (PowerShell), remplacer ./ex1 par .\ex1.exe.

Exercice 1 — Passage par valeur et par référence

Objectif : comprendre la différence entre un paramètre passé par valeur et un paramètre passé par référence.

Code d'origine : modifier(int &a, int b)

Variable	Valeur initiale	Mode de passage	Valeur finale
x	10	référence (&)	15
y	20	valeur (copie)	20

Sortie : 15 20

Version corrigée : modifier(int &a, int &b) : les deux paramètres sont des références.

Sortie : 15 30

Notions clés :

Par valeur : la fonction travaille sur une copie, l'original n'est pas modifié.
Par référence : la fonction travaille sur un alias, l'original est modifié.
Le symbole & dans une déclaration de paramètre indique une référence. Ce n'est pas l'opérateur « adresse de ».
Exercice 2 — Classes et encapsulation

Objectif : modéliser un compte bancaire en respectant l'encapsulation.

Classe CompteBancaire

Attribut (privé)	Type	Description
numero	int	identifiant du compte
titulaire	string	nom du propriétaire
solde	double	montant disponible
Méthode (publique)	Rôle
constructeur paramétré	initialise numéro, titulaire et solde
deposer(double montant)	ajoute un montant positif au solde
retirer(double montant)	retire si le montant est positif et le solde suffisant
afficher() const	affiche les informations du compte

Programme principal : création de deux comptes, un dépôt, un retrait, puis affichage.

Sortie attendue :

Compte n° 1001 | Titulaire : Ahmed | Solde : 1250
Compte n° 1002 | Titulaire : Sara | Solde : 400

Notions clés :

Attributs private, accès contrôlé via des méthodes publiques.
Validation des données (montant positif, solde suffisant).
Méthodes qui ne modifient pas l'objet déclarées const.
Exercice 3 — Héritage et polymorphisme

Objectif : gérer différents types de véhicules via une classe mère et deux classes dérivées.

Hiérarchie des classes

Vehicule  (immatriculation, marque, vitesseMax)   [protected]
├── Voiture  (nombrePortes, typeCarburant)
└── Camion   (capaciteCharge, nombreEssieux)

Points importants :

afficherDetails() est virtual dans Vehicule et redéfinie avec override dans Voiture et Camion.
Les attributs de Vehicule sont protected : accessibles aux classes dérivées.
Le main() utilise un tableau Vehicule*[2] contenant une voiture et un camion : l'appel afficherDetails() est résolu dynamiquement (polymorphisme).
Les objets créés avec new sont libérés avec delete.

Pourquoi le destructeur de Vehicule est virtual ?

Sans virtual, delete sur un Vehicule* qui pointe vers un objet dérivé n'appelle que le destructeur de Vehicule (liaison statique). C'est un comportement indéfini, avec risque de fuites mémoire. Avec virtual, le destructeur de la classe dérivée est appelé en premier, puis celui de la classe mère.

Sortie attendue de la destruction :

Destruction de Voiture
Destruction de Vehicule
Destruction de Camion
Destruction de Vehicule
Consignes respectées
Langage : C++17
Principes de la POO : encapsulation, héritage, polymorphisme
Code clair, structuré et syntaxiquement correct

<img width="960" height="540" alt="image" src="https://github.com/user-attachments/assets/727c113d-1b6a-4768-9d63-46fa3cbea98d" />
<img width="960" height="540" alt="image" src="https://github.com/user-attachments/assets/31a95046-14d2-42ec-9f03-83ea0c9829f7" />
<img width="960" height="540" alt="image" src="https://github.com/user-attachments/assets/1798feda-6e02-46d9-949b-2cac880b7bd3" />
