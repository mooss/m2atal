Nous avons subi un certain nombres de problèmes en M2 ATAL sur l'année 2018-2019.
Ces problèmes étaient au final assez évitables mais nous n'avions pas toutes les cartes en mains dès le début pour y faire face.
Pour éviter que ça se répète, voici quelques conseils et remarques.
En sachant que vous n'allez pas subir les même problèmes que nous, donc il va vous falloir innover de ce point de vue.

# Concernant tout le monde

## Petit guide de ~~communication~~ survie en milieu étudiant

1. Quand un problème est constaté (par exemple surcharge de travail), confronter (gentiment) l'intervenant.
2. Si vous n'arrivez pas à engager une discussion autour du problème, n'insistez pas, contactez l'intéressé par mail.
3. Si ça ne donne rien, parlez en au responsable de formation.

Selon les cas, l'étape 2. peut être court-circuitée.
Les mails semblent mieux fonctionner, peut-être parce que le destinataire a plus le temps d'ingérer et de comprendre le message.

Gardez à l'esprit que les responsables de formation n'ont pas de pouvoir de décision particulier sur les autres intervenants.
Typiquement, si les intervenants refusent d'admettre un problème, c'est juste parce qu'ils ne le voient pas.
C'est donc à vous de leur faire voir.

# Spécifique à Nantes

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
