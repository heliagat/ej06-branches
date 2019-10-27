# TALLER "Ya es hora de Git"

Començar a fer una migració d'un sistema de control de versions anticuat a Git.

Es recomanda utilitzar **Git TFS** 

https://github.com/git-tfs/git-tfs

**Preparar la migració**:

* revisar l'estructura del repositori

  * Branques innecessàries

    * Identifcar les branques
      * Master
      * Dev
      * Versions

  * ¿Necessitat de la historia?

    * Sanejar

      * Netejar shelves

      * Deixar repositori estable

        * No deixar codi sense commit

        

  **Clone**

  https://github.com/git-tfs/git-tfs/blob/master/doc/commands/clone.md

  git tfs clone http://tfs:8080/tfs/DefaultCollection $/Project1 -from={0}--branches==all

  

  **Consells**

  * Treballar sobre la mateixa màquina on tinguem el nostre TFS
  * Realitzar quan no es treballa sobre el repositori
  * --debug per rebre un log més definit si quelcom falla

  

  **Complicacions - perquè hi ha poca documentació a Inet**

  

  **TF40030

  El magatzem de dades local s'està utilitzant actualment en altre aplicació.

  * És degut a que la versió de 2015 es pot localitzar a local i servidor
  * https://github.com/jmmortega/git-tfs/tree/bug/TF400030_Error

  

  **Identificació de changeset**

  * El procés en determinades ocasions pot demanar-nos en un canvi que indiquem d'on sorgeix.
  * Hem de cercar a la història el canvi adient que estigui relacionat amb la rama en concret

  **No totes les branques es descarreguen**

  * Un nou repositori, anar branca a branca no descarregada
  * git tfs clone http://tfs:8080/tfs/DefaultCollection $/Project1/NombreRama --debug --resumable -- Branch=none
  * En repositori original, un cop tenim la branca principal clonada
  * git checkout commitHashBrancaCreada NomBranca
  * Creem remote local
  * git init -bare
  * Afegim el remot al repositori original i al de la branca afectada
  * git remote add origin DirectoriOnEsVaIniciliatzar
  * Fem un push al directori principal en local
  * Realitzem pull des del repositori original
  * git pull origin -s recursive -X theirs

**TIPS**

* Estudiar totes les branques que tenim en la versió original control per identificar allò innecessari
* Realitzar còpies de seguretat cada cop que realitzem un nou pas.

**Revisar la documentació del TFS**

* Revisar llibres que hi són dins de la propia documentació
* Descarregar la versió v0.30 que és la més actual

Dins de les variables de sistema de Windows podem integrar l'aplicació en el Path per més comoditat

Es treballarà totalment en shell

Intentar realitzar aquestes tasques en cap de setmana o periodes que sapiguem que cap usuari hi accedirà al projecte.

