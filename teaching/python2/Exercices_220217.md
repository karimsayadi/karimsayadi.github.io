---
layout: default
---

## Exercice 1

Dans cet exercice, nous allons créer un fichier csv qui contiendra deux colonnes. La première est relative au nom du fichier et la deuxième à son identifiant. Nous allons dans une première étape parcourir l'ensemble des fichiers dans un dossier et dans une seconde étape récupérer l'identifiant à partir du nom des fichiers parcouru. 

* Le programme python contient une seule fonction qui prend en entrée le chemin du dossier contenant le fichier et donne en sortie un fichier csv avec deux colonnes. Nous allons utilser les modules os, csv, re et les fonctions open() et write().

* Nous importons d'abord les modules dont nous avons besoin. 


```python
import sys, os
import re
from os import listdir
from os.path import isfile, join
```

* Nous créeons ensuite notre fonction que nous appellerons *fromFileToCSV*. Cette fonction prend deux arguements : le chemin vers le dossier et le nom du fichier csv. La signature de la fonction est comme suit, `fromFileToCSV(folderpath, csvfilename)`


```python
def fromFileToCSV (folderpath,csvfilename) :
    files = [f for f in listdir(folderpath) if isfile(join(folderpath, f))]
    random.shuffle(files)

    for filepath in files:
        if filepath.endswith(".png"):
            label = re.findall("^(\d+)_",filepath)
            csvLine = filepath+","+str(label[0])
            print csvLine
            with open(folderpath+csvfilename, "a") as myfile:
                myfile.write(csvLine)
                myfile.write("\n")
```

* La variable `files` est une liste qui le nom de tous les fichiers sous le chemin stocker dans la variable `folderpath`. 
* Nous utilisons `random.shuffle(files)` pour mélanger aléatoirement la position de chaque nom de fichiers dans la liste `files`. 
* Nous parcourons la liste `files` avec un boucle `for` et pour chaque fichier avec l'extention `.png` nous récupérons dans la variable `label` le premier caractére numérique qui est présent dans le nom du fichier `filepath`. 
* Nous initialisons la variable `csvLine` avec le nom du fichier et le caractére numérique récupéré avec l'expression réculière `"^(\d+)_"`.
* Nous ouvrons un fichier csv fourni en argument à la fonction et écrivant la ligne cotenu dans `csvLine`.


```python
if __name__ == '__main__':
    if len(sys.argv) == 3:
        fromFileToCSV(sys.argv[1],sys.argv[2])
```

## Exercice 2

Dans cet exercice, nous allons construire un corpus ou une collection de documents à partir d'un fichier texte. Ce fichier contient plusieurs lignes qui correspondent à des tweets. D'abord, et après avoir ouvert le fichier, pour chaque ligne dans ce dernier nous allons créer un nouveau fichier. Cette étape nous donnera un dossier contenant un nombre de fichiers égal au nombre de ligne dans le fichier d'origine. Ensuite, et suivant une certaine proportion que nous allons fournir comme paramètre d'entrée nous allons diviser l'ensemble de fichiers en trois dossiers. 

* Le programme contenient deux fonctions : la première prendra en entrée le fichier d'origine et donnera en sortie un dossier avec un nombre de fichiers égales au nombre de lignes dans le fichier d'origine. La deuxième fonction prendra comme entrée le chemin relatif ou absolu du dossier fraîchement créé ainsi que trois proportions. C'est-à-dire que la deuxième fonction donnera en sortie trois dossiers avec par exemple 20% des fichiers seront copié dans le premier dossier, 30% des fichiers seront copié dans le deuxième dossier et 50% des fichiers seront copiés dans le troisième dossier.


```python
import sys, os 
import shutil
import re
import random
from os import listdir
from os.path import isfile, join
```


```python
def file_to_files (original_file_path):

    if not os.path.exists("lines_folder"):
        os.makedirs("lines_folder")
    file_counter = 0
    my_file = open(original_file_path)
    for line in my_file.readlines():
        file_counter += 1
        my_new_file = open("lines_folder/"+str(file_counter)+'_processed_tweet.txt', 'a')
        my_new_file.write(line)
        my_new_file.close()
    my_file.close()

    return "lines_folder/"
```

\begin{equation*}
proportions\_fichiers = \frac{pourcentage}{100} \times nombre\_total\_des\_fichiers
\end{equation*}


```python
def from_folder_to_folders (original_folder_path, percentageFolder1, percentageFolder2, percentageFolder3):
    """
    Shuffle the files in original_folder_path to have different files in each of the three folders
    """

    files = [f for f in listdir(original_folder_path) if isfile(join(original_folder_path,f))]
    random.shuffle(files)

    nbFilesFolder1 = int((float(percentageFolder1)/100)*len(files))
    nbFilesFolder2 = int((float(percentageFolder2)/100)*len(files))
    nbFilesFolder3 = int((float(percentageFolder3)/100)*len(files))


    if not os.path.exists(original_folder_path+"Folder1"):
        os.makedirs(original_folder_path+"Folder1")
    if not os.path.exists(original_folder_path+"Folder2"):
        os.makedirs(original_folder_path+"Folder2")
    if not os.path.exists(original_folder_path+"Folder3"):
        os.makedirs(original_folder_path+"Folder3")

    for j,filepath in enumerate(files):
        sourceFolder = os.path.join(original_folder_path,filepath)
        if (j > nbFilesFolder1 and j < nbFilesFolder1+nbFilesFolder2):
            print "copying the files to folder 2"
            if filepath.endswith(".txt"):
                shutil.copy2(sourceFolder,original_folder_path+"Folder2/")
        elif (j > nbFilesFolder1+nbFilesFolder2 and j < len(files)):
            print "copying the files to folder 3"
            if filepath.endswith(".txt"):
                shutil.copy2(sourceFolder,original_folder_path+"Folder3/")
        else:
            print "copytin the files to folder 1"
            if filepath.endswith(".txt"):
                shutil.copy2(sourceFolder, original_folder_path+"Folder1/")
```


```python
def main():
    from_folder_to_folders(file_to_files("data/preprocessedP.txt"), 50, 30, 20)

if __name__ == '__main__':
    main()
```
