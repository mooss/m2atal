# Connection ssh sur les serveurs du Mans

## Sur un réseau non bloqué

L'identifiant du mans est de la forme s123456.
```sh
ssh identifiant@transit.univ-lemans.fr
ssh skinner
```

Ou en une ligne (nécessite cependant de taper deux fois le mdp) :
```sh
ssh -A -t -l identifiant_univ_lemans transit.univ-lemans.fr ssh -A skinner
```

## Sur le réseau de la fac

Pour passer à travers le réseau de la fac, établir un tunnel ssh entre bastion et transit puis se connecter en l'utilisant :
```sh
ssh -f -N -L:port_local:transit.univ-lemans.fr:22 identifiant_univ_nantes@bastion.etu.univ-nantes.fr
ssh -A -t identifiant_lemans@localhost -p port_local ssh -A -t skinner ssh -A gpue1
```

Où
 - port_local est un port TCP libre supérieur à 1024 (basiquement un numéro quelquonque entre 1024 et 65535)
 - identifiant\_univ\_nantes est le numéro d'étudiant de nantes, de la forme E123456L

Possible en une ligne, en sachant qu'il n'est pas nécessaire de réétablir le tunnel ssh s'il est déjà en place et que tenter de réétablir un tunnel peut faire planter la connexion :
```sh
ssh -f -N -L:port_local:transit.univ-lemans.fr:22 identifiant_univ_nantes@bastion.etu.univ-nantes.fr && ssh -A -t identifiant_lemans@localhost -p port_local ssh -A -t skinner ssh -A gpue1
```

En utilisant cette commande, il faut donc entrer une fois le mot de passe univ nantes et deux fois le mot de passe univ lemans.
