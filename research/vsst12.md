---
layout: default
---


### Une approche prétopologique pour la 
catégorisation des données micro-blogging <a target="_blank" href="/research/articles/vsst12.pdf" class="pdf-button"><span>pdf</span></a>


#### Karim Sayadi, Marc Bui, Vigile Hoareau, Soufian Ben Amor

### Abstract 

Dans ce papier, nous traitons la question de la détection des thèmes pour de grand corpus de données textuelles non structurées, et plus spécifiquement des données de micro-blogging. Dans ce travail intitulé Topological Analysis of Dynamic Semantic Space (TADySS), nous effectuons un couplage entre la construction d'un espace sémantique à partir d'une base de tweets, fournie par le réseau social de micro-blogging Twitter, et une approche prétopologique que nous avons développée pour suivre l'évolution des thèmes au cours du temps. Nous partons d'un ensemble d'informations non structurées sous une forme brute, et adoptons un processus cyclique pour catégoriser l'information. L'espace sémantique des tweets est généré à partir de l'indexation de l'ensemble des tweets avec la bibliothèque Lucene. Le corpus numérique traité à titre illustratif est d'une taille de 12Go et est constitué de plusieurs fichiers représentant plusieurs millions d'éléments. Ces fichiers issus de la base de données des tweets sont bruités et comportent de nombreuses informations inutiles pour la catégorisation. Nous appliquons donc un parser que nous  avons développé spéficiquement afin d'extraire  les données utiles. Nous procédons ensuite à l'indexation et à la construction de l'espace sémantique  à l'aide de l'algorithme Random Indexing qui est implémenté à l'aide du package semantic vectors).La proximité sémantique entre les tweets repose sur le calcul du cosinus entre les deux vecteurs représentant chaque tweet dans l'espace sémantique, l'appartenance d'un tweet donné à une catégorie étant, quant à  elle, déterminée en calculant la similarité entre le tweet considéré et les représentants de chaque catégorie. Le processus est constitué par une boucle de traitements réalisant des allers-retours entre l'index et l'espace sémantique jusqu'à ce que l'ensemble de départ soit divisé en plusieurs ensembles représentant chacun un thème.L'algorithme prétopologique développé, présente un intérêt pour de nombreuses applications. Parmi les plus intéressantes, nous pouvons citer la détection de l'émergence d'événements importants dans l'actualité, ou la détection des communautés virtuelles d'individus associées aux thèmes de discussions. 

### Citation 

#### BibTeX 

```
@inproceedings{vsst12,
	Author = {Karim Sayadi and Marc Bui and Vigile Hoareau and Soufian Ben Amor},
	Booktitle = {Séminiare V.S.S.T.’2012 VEILLE STRATEGIQUE SCIENTIFIQUE & TECHNOLOGIQUE, Ajaccio},
	Pages = {1--7},
	Title = {Une approche prétopologique pour la catégorisation des données micro-blogging},
	Year = {2012}}
```