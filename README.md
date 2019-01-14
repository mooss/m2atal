Nous avons subi un certain nombres de problèmes en M2 ATAL sur l'année 2018-2019.
Ces problèmes étaient au final assez évitables mais nous n'avions pas toutes les cartes en mains dès le début pour y faire face.
Pour éviter que ça se répète, voici quelques conseils et remarques.
En sachant que vous n'allez pas subir les même problèmes que nous, donc il va vous falloir innover de ce point de vue.

# Concernant tout le monde

## Petits trucs à savoir

 - Les intervenants ponctuels n'ont pas nécessairement à faire des évaluations. Si les trois enseignants de certaines matières tiennent chacun à vous faire faire un TP noté + une présentation d'article, vous allez pas vous en sortir. Ne laissez pas cette situation se produire.
 - Les intervenants réguliers n'ont pas à faire de projets en dehors de ceux explicitement prévu dans le cursus (apprentissage automatique en langue et fouille de texte en ce qui nous concerne). Les laissez pas vous dire qu'il vous font une faveur en vous donnant "seulement" un mini-projet.
 - La charge de travail **doit** être adaptée aux alternants. Pas tout le temps mais parfois quand même. Les petites choses s'ajoutent vite, soyez vigilants.
 
Vous l'avez compris, le mot d'ordre est ne vous laissez pas faire, ne vous laissez pas être dépassés par les évènements.

## Petit guide de communication en milieu étudiant

1. Quand un problème est constaté (par exemple surcharge de travail), confronter (gentiment) l'intervenant.
2. Si vous n'arrivez pas à engager une discussion autour du problème, n'insistez pas, contactez l'intéressé par mail.
3. Si ça ne donne rien, parlez en au responsable de formation.

Selon les cas, les étapes 1. et 2. peuvent être inversées, à vous de voir.
D'expérience personnelle, les mails fonctionnent bien mieux, peut-être parce qu'il est possible de bien penser à la formulation et que le récepteur a plus le temps d'ingérer et de comprendre le message.

Gardez à l'esprit que la fac ne possède pas une structure fondamentalement hiérarchique et que les responsables de formation n'ont pas de pouvoir de décision particulier sur les autres intervenants.
Il vous faut composer avec ça.
Gardez aussi à l'esprit que si les intervenants refusent d'admettre un problème, c'est juste parce qu'ils ne le voient pas.
C'est donc à vous de leur faire comprendre (c'est là que se sont trouvées beaucoup de nos difficultés).

# Spécifique à Nantes

Si vous avez passé un certain temps à la fac de Nantes, vous devez être au courant que l'administration est pas là pour vous faciliter la tâche.
Ça ne sera jamais aussi vrai que pour votre M2.

## Connection ssh sur les serveurs du Mans
Courte explication sur comment se connecter en ssh à skinner.
Pour plus de détail, voir [https://wiki.univ-nantes.fr/doku.php?id=etudiants:restreint:bastion_out]()

### Sur un réseau non bloqué

L'identifiant du mans est de la forme s123456.
```sh
ssh identifiant@transit.univ-lemans.fr
ssh skinner
```

Ou en une ligne (nécessite cependant de taper deux fois le mdp) :
```sh
ssh -A -t -l identifiant_univ_lemans transit.univ-lemans.fr ssh -A skinner
```

### Sur le réseau de la fac

Pour passer à travers le réseau de la fac, établir un tunnel ssh entre bastion et transit puis se connecter en l'utilisant :
```sh
ssh -f -N -L:port_local:transit.univ-lemans.fr:22 identifiant_univ_nantes@bastion.etu.univ-nantes.fr
ssh -A -t identifiant_lemans@localhost -p port_local ssh -A skinner
```

Où
 - port_local est un port TCP libre supérieur à 1024 (basiquement un numéro quelquonque entre 1024 et 65535)
 - identifiant\_univ\_nantes est le numéro d'étudiant de nantes, de la forme E123456L

Possible en une ligne, en sachant qu'il n'est pas nécessaire de réétablir le tunnel ssh s'il est déjà en place et que tenter de réétablir un tunnel peut faire planter la connexion :
```sh
ssh -f -N -L:port_local:transit.univ-lemans.fr:22 identifiant_univ_nantes@bastion.etu.univ-nantes.fr && ssh -A -t identifiant_lemans@localhost -p port_local ssh -A skinner
```

En utilisant cette commande, il faut donc entrer une fois le mot de passe univ nantes et deux fois le mot de passe univ lemans.

## Salles et emploi du temps
### Salles sans visio
Les salles de tp du CIE n'ayant pas de visio, il est typiquement préférable que chacun amène sa machine et que les tps aient lieu dans des salles avec visio.

Gardez tout de même l'oeil sur l'emploi du temps, puisque de temps en temps, sans raison apparente, des cours apparaissent dans des salles sans visio.

### Ouverture des salles
En plus des badges activés pour la salle U3, il est possible de désigner un étudiant référent, à même de récupérer un badge universel à l'accueil en échange de sa carte d'étudiant.
Pour mettre ça en place, voir avec le responsable de Nantes.
