---
marp: true
theme: default
markdown.marp.enableHtml: true
paginate: true
---

<style>

section {
  background-color: white;
  color: black;
}


h1 {
  color: DarkBlue;
}

h2 {
  color: DarkBlue;
}

h3 {
  color: DarkBlue;
}

h4 {
  color: DarkBlue;
}

h5 {
  color: DarkBlue;
}

h6 {
  color: DarkBlue;
  font-size: 30px;
  font-weight:normal;
}


img[alt~="center"] {
  display: block;
  margin: 0 auto;
}
blockquote {
  background: #ffedcc;
  border-left: 10px solid #d1bf9d;
  margin: 1.5em 10px;
  padding: 0.5em 10px;
}
blockquote:before{
  content: unset;
}

      
blockquote:after{
  content: unset;
}
</style>


<!-- _class: lead -->



![width:200](img/su.png) &nbsp;&nbsp;&nbsp; $\qquad$ $\qquad$ ![width:350](img/obtic.png) $\qquad$ $\qquad$ ![width:200](img/scai.png)
<br> 

## &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Transkribus, Kraken, eScriptorium

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Ljudmila Petkovic**<br><br>

###### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Paris, le 18 novembre 2021




---

## Corpus

_Registre du Comité d'administration du Théâtre français de S. M. l'Empereur et Roi._

* Rédigé par Nicolas Bernard, commissaire du théâtre
* Paris, le 16 janvier 1813
* Texte manuscrit

* **Document** : collection d'images formant un ensemble
* Échantillon de 10 pages

---


## I&nbsp;&nbsp;&nbsp; Transkribus

### 1. Pré-traitement des données 

---

## Pré-traitement des données


* **Sélectionner les pages à pré-traiter** (de bonne qualité)
  * Exclure les pages vides, non pertinentes, le dos de livre etc.

* **Découper les scans PDF**
  * afin de ne transcrire que le véritable contenu textuel d'une page
  * sinon, le moteur d'OCR / HTR va générer des symboles inutiles
  * Impact de la couverture du document, des traces de l'écriture de la page précédante / suivante, des taches etc. sur la qualité de transcription


--- 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![width:350](img/découpage.png)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![width:290](img/découpé.png)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Figure 1a : PDF original.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Figure 1b : PDF découpé.  

---

## Pré-traitement des données

* Charger toutes les pages, pour garder les références (page de titre) 
* Normalisation du contrast **sans** binarisation lors du chargement des images du document ([Michael _et al_, 2018](https://readcoop.eu/wp-content/uploads/2018/12/D7.9_HTR_NN_final.pdf)) 
  * ≠ Kraken — binarisation comme une étape indépendante

---

## I&nbsp;&nbsp;&nbsp; Transkribus

### 2. Choix du modèle de transcription
#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2.1 New France 17th-18th Centuries

---


## Choix du modèle de transcription

Plusieurs paramètres :
* Langue : française
* Alphabet : latin
* Type d'écriture : [_coulée_](https://books.google.fr/books?id=lcHRgDFtBSYC&pg=PA110&lpg=PA110&dq=ronde”,+“bâtarde”+and+“coulée&source=bl&ots=HjaRrULe19&sig=ACfU3U1qwQZuF15hXKxv1DXqcAzFIJueMg&hl=en&sa=X&ved=2ahUKEwi4oZmeoIf0AhWqyIUKHYQPA5kQ6AF6BAgCEAM#v=onepage&q=ronde”%2C%20“bâtarde”%20and%20“coulée&f=false) + [_ronde_](https://books.google.fr/books?id=lcHRgDFtBSYC&pg=PA110&lpg=PA110&dq=ronde”,+“bâtarde”+and+“coulée&source=bl&ots=HjaRrULe19&sig=ACfU3U1qwQZuF15hXKxv1DXqcAzFIJueMg&hl=en&sa=X&ved=2ahUKEwi4oZmeoIf0AhWqyIUKHYQPA5kQ6AF6BAgCEAM#v=onepage&q=ronde”%2C%20“bâtarde”%20and%20“coulée&f=false)
* Type de documents : administratif, ~ordonnances, chancellerie
* Époque : début du XIX$^e$ s.
* Moteur de reconnaissance de caractères : HTR+ 
* CER (taux d'erreur de caractère, angl. _character error rate_)

---

## Choix du modèle de transcription

Modèles d'HTR accessibles au public (_cf._ le site de Transkribus) : 
* [French — General Model](https://readcoop.eu/model/french-general-model/) (8.5% CER)
* [Charter Scripts (German, Latin, French)](https://readcoop.eu/model/charter-scripts-german-latin-french/) (6.32% CER)
* [French and Latin Chancery documents](https://readcoop.eu/model/french-and-latin-chancery-documents/) (5.33% CER)
* [French Handwriting 19$^{th}$ century](https://readcoop.eu/model/french-handwriting-19th-century/) (7.73% CER) 
* [French Livre Rouge](https://readcoop.eu/model/french-livre-rouge/) (8% CER)
* [New France 17$^{th}$-18$^{th}$ centuries](https://readcoop.eu/model/new-france-17th-18th-centuries/) (4.12% CER) 
* [Ordonnances des Intendants](https://readcoop.eu/model/ordonnances-des-intendants/) (4.18% CER)

---

## New France 17$^{th}$-18$^{th}$ centuries
|         |            | 
|:-------------:|-----| 
| ![width:700](img/new_france.png) Source : [Projet « Nouvelle-France numérique »](http://nouvellefrancenumerique.info)    | • Combinaison d'écritures françaises (_ronde_, _bâtarde_ et _coulée_) <br> • 1 600 pages (296 403 mots) de correspondance et de registres des administrateurs coloniaux de la Nouvelle-France du XVII$^e$/XVIII$^e$  s.<br> • CER de 4.12% (données de validation)<br> • Pas adapté aux écrits des notaires ou des greffiers |

---

## I&nbsp;&nbsp;&nbsp; Transkribus

### 3. Lancement de l'HTR 

---

## Lancement de l'HTR
* Sélectionner les pages découpées au préalable pour l'HTR

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![width:300](img/overview.png)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![width:380](img/overview_modèle.png)

---

## Lancement de l'HTR

![width:750 center](img/modèle.png)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Le modèle « New France » dans Transkribus.

---

## Lancement de l'HTR

* La simplification des polygones réduit la complexité des segments de ligne, en économisant de la bande passante et de l'espace de stockage
![width:350 center](img/polygon_simpli.png)


---


## I&nbsp;&nbsp;&nbsp; Transkribus

### 4. Résultats de l'HTR 

---

## Résultats de l'HTR

* Durée de transcription : environ 3h pour 480 pages

![width:600 center](img/transcription.png)


---


## II&nbsp;&nbsp;&nbsp; Kraken

### 1. Choix du modèle de transcription

---
## Choix du modèle de transcription

* Modèles d'HTR accessibles au public (_cf._ les [nouveaux](https://gitlab.inria.fr/dh-projects/kraken-models) et les [anciens](https://gitlab.inria.fr/dh-projects/kraken-models/-/tree/master/segmentation%20models/archived))
* Les résultats de transcription ne sont pas tout à fait satisfaisants 
* Les modèles obsolètes manifestent un problème d'initialisation du package `nnpack`

---
## `riant_ftmrs15_12.mlmodel` (avec binarisation)
* Ancien modèle
* Génère meilleurs résultats par rapport aux nouveaux modèles de kraken
```
Régistre du Comité d'Administration
d'ou Tonéatre Français de S. M. Emvereur et Roi
2
Paris ce 16 Jauvier 1d
d'après l'inviration deMr Benard suupténant, les foutetions de Commipsaire
Anpérias M. M. FSeury Tahue Nicnos damors demuer &amp; Lacave de nomciprent
a heures dans laSaile des Séances du Contite d adninntration 
d Bernard notitie du arrete deMr Le surentendans desoictaite
oortans l'arganisation d'un du Comite d'Aduntration à d'autie d
conité de Lechere confomeuient au denret inpérias d abre d d
'arretes dous airie doncu
Dganigation  de Frenrier Chambellau de S. M. d'Ernvereur et Roi ouventeudant de
Vix Comile  Svertactes, du les articles 30 &amp; 49 du Décres unvérenl du1 5. 8bres 1812
d'Achunestration, portaux orgouisation du Théatre Français, Arrite cíque Suit
drtefer
mane me Pourt, nommés meuibres du Comité d'Aduinistration M. M. Feury, Taluie
d
Michot Damars Denret Lacaue
dt, 2e
```



---

## `riant_ftmrs15_12.mlmodel` (sans binarisation)
* le début du texte est déplacé (`[...] Registre du Comite d'Administration [...]`)

```
inpérial, M. M. Feury, Tahuu, Michos dumas, desier &amp;Lacave se recrifent
Le Prerrier Chambellau deS. M. l'Empereur et Roi surinteudant des
d'Adhninistration. portaur orgouisation du Théatre Francais, Arrête cequi suit.
Flesdes Raucourt &amp; Mars sout adjouites au Comité pour laPocuation
dis Coutité de spectartes, du l'Article 68 du Décret inpérial du15, 8bre portant orgouisation
Registre du Comite d'Administration
du Cnéatre français deS. M. l'Empereur et Roi,
Organisation
Paris ce 16 Janvier 1813.~
d'après l'invitation duNr Bernard recptinant lesfouctions de Commisaire
à 2 heures dans laSalle desséances du Conrité d'Adminsstration-
Mr Beruardnotifie deux arrétés deMr lesurintendant desspectarles
portaut l'organisation, l'un du Comité d'Adiniuntration &amp;'autre du
Comité de Lecture, conformément au décret inpérial du15 8bre 1 812-
Ces arrêtés sour arrisiconcur.
Svertacles, du les articles 30 &a 49 du décres inpérial du15 8bre 1812
Sous nommés meurbres duComité d'Aduinistration M. M. Feury, Talure
le Commipaire inpérial est charge del'exécution
```
---

## III&nbsp;&nbsp;&nbsp; eScriptorium

### 1. Introduction

---

## Introduction

* Infrastructure web gratuite et à code source ouvert 
* Spécialisée pour l'HTR des documents anciens
* Développée par PSL | INRIA
* Basée sur les techniques de l'apprentissage machine ([encog](https://en.wikipedia.org/wiki/Encog))
* Cadre de programmation fourni par l'application eScript
* Connexion au [serveur](https://escriptorium.fr) ou installation en local / Docker
* _Cf._ le [tutoriel](https://lectaurep.hypotheses.org/documentation/prendre-en-main-escriptorium) en français
---



## III&nbsp;&nbsp;&nbsp; eScriptorium

### 2. Préliminaires

---

## Préliminaires

**Connexion au serveur** 

* [Instance eScriptorium](http://145.238.157.11/login/) en ligne
* Nom d'utilisateur : `guest`
* Mot de passe : `GuestAccount2021!` 
* Tableau de bord pour la gestion des documents créés par et partagés avec un compte


---

## Préliminaires

* Création d'un nouveau document
* Chargement des images
>La binarisation n'est plus une étape obligatoire et pourrait même diminuer la qualité [des images à transcrire]
* Segmentation automatique : `blla.mlmodel` par défaut



---

## Segmentation

* `blla.mlmodel` (par défaut)

![width:700 center](img/seg.png)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Les lignes (violet) et les zones (vert).

---

## Transcription (sans binarisation)

```
Registre du Comite d'Administration
du Tnéatre Français deS. M. l'Empereur et Roi,
Paris ce 16 Janvier 1813.~
d'après l'invitation deNr Bernard recptinant lesfouctions de Commisaire
innpérial, M. M. Fleury, Tahuu, Michot dumas, desprer &amp;Lacaue se recrifsent
à 2heures dans laSalle desséances du Contité d'Administration-
Me Deruardnotifie deux arrétés &amp; r leSurintendant desspectaites
portaut l'organisation, l'un du Comité d'Adiniuntration &amp;l'autre du
Comrité de Lecture, confornsément au décret inpérial du15 8bre 1 812-
Ces arrêtés sour ainsiconcur.
Organisation
Le Preurier Chambellau deS. M. l'Eupereur et Roi Surinteudant des
du Comite
Svertactes, du les articles 30 a 49 du décres iipérial du15 8bre 1812
20
d'Aohinistration. poitaut orgouisation du Théatre Francais, Arrete cequi suit.
Art. 1er
Sous nommés meubres duComité d'Aduinistration M. M. Feury, Talmre
Michot, Damas, Denrer, Lacane.
Art. 2e
```
---

## IV&nbsp;&nbsp;&nbsp; Évaluation
...

---
...
* Préparer les données de vérite-terrain (angl. _ground truth_, _GT_)
* Documents de référence corrigés manuellement (.txt, PAGE XML, ALTO XML, hOCR, FineReader-10 XML)
* ocrevalUAtion ([dépôt GitHub](https://github.com/impactcentre/ocrevalUAtion))

---

## V&nbsp;&nbsp;&nbsp; Conclusion