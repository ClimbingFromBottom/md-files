# Hash

## La somme de contrôle (Hash)

La version basique d’un tel mécanisme est appelée “somme de contrôle”.

Le but d’une somme de contrôle est en quelque sorte d’être “l’empreinte” d’une donnée (attention, cette “empreinte” n’est pas une signature et ne garantit pas pour autant l’identité). Un exemple très simplifié serait de compter le nombre de lettres dans un message et de rajouter ce nombre à la fin dudit message. De cette manière, un destinataire peut immédiatement vérifier que le message n’a pas été coupé par erreur.

Un mécanisme de ce type, bien qu’un peu plus complexe, est utilisé pour vérifier votre numéro de compte IBAN. Les deux derniers chiffres sont en effet une somme de contrôle (selon un algorithme un peu compliqué à résumer) des chiffres précédents. Un mécanisme similaire est appliqué aux cartes de crédit. Cela signifie que si vous entrez un mauvais chiffre par erreur lors d’un paiement, votre banque en ligne le détectera immédiatement. Bien entendu, ces systèmes sont simples et ne permettent que de détecter des erreurs involontaires.


## Les algorithmes de hashage

C’est pour cela qu’ont été développés les algorithmes de “hashage”, littéralement qui mixent, mélangent les données. Les plus connus sont aujourd’hui la famille de fonctions SHA-2 et SHA-3.

Le principe d’un algorithme de hashage est de générer, pour n’importe quelle information de n’importe quelle taille, une empreinte unique. Voici par exemple le hash SHA-2 256 bits d’un fichier sur mon ordinateur :

> 9eb4ef548e36a589a46ef00395f3e2f722f5466438c9385976ab188bec59fa2d


## 4 propriétés fondamentales

Cette empreinte, ou plutôt ce hash, possède plusieurs propriétés particulièrement intéressantes.

**Premièrement, elle est “déterministe”**. Cela signifie que si je prends le même fichier, j’aurai toujours une seule et même empreinte unique.

**En deuxième lieu, elle est “chaotique”**. Ça veut dire que si je change même très légèrement la donnée initiale, l’empreinte sera complètement différente. Voici par exemple le hash du même fichier avec un simple espace rajouté à la fin:

> 260f4c3c44574df5c73dd2d1216e88d0c4137da3d1394d661875232bf4c50d0a

**Troisièmement, le hash est à sens unique**. Si on peut toujours déterminer le même hash à partir du fichier, il est strictement impossible de retrouver le fichier à partir du hash. La seule solution est d’essayer tous les fichiers possibles. Dans certains cas, c’est cependant possible (par exemple si on a le hash d’un mot de passe dont on sait que la longueur est limitée, il est relativement simple de tester toutes les combinaisons).

![Principe du hashing & du chiffrement](https://raw.githubusercontent.com/ClimbingFromBottom/md-files/main/images/hash/hashing.png)
Pour plus d'informations, suivez le lien sur le [chiffrement] et son importance dans la cryptographie(./cryptographie.md).   


**Quatrième propriété et non des moindres** : un bon hash ne permet pas les collisions. Cela signifie que deux fichiers différents ne peuvent pas avoir le même hash. Le hash est donc unique, c’est une sorte d’empreinte digitale unique du fichier. Lorsque des chercheurs découvrent une collision, on dit que l’algorithme de hash est “cassé”. Il ne faut plus lui faire confiance et ne plus l’utiliser (c’est par exemple le cas de SHA-1 et de MD5. Ces fonctions ne doivent donc plus être utilisées).

Pour des raisons pratiques, un bon algorithme de hash sera également très rapide et donnera toujours une empreinte de taille fixée.


## La finitude du hashage

Votre réaction sera certainement de considérer que puisque la taille d’un hash est fixée et qu’il existe un nombre infini de fichiers possibles, alors forcément, il doit exister des fichiers avec le même hash.

C’est vrai théoriquement mais relativisons. SHA-256 permet 2 exposant 256 hash possibles. Cela signifie que si 10 milliards d’êtres humains possédaient chacun un super ordinateurs capables de produire 1 milliard de fichiers avec leur hash à chaque seconde, il faudrait encore attendre l’âge de l’univers avant d’avoir une chance raisonnable d’obtenir une collision. Autrement dit, on peut considérer une collision comme impossible.


## Conclusion

En résumé, **le hash est l’équivalent du numéro de carte d’identité d’un fichier ou d’une donnée**. Comme tout est donnée et que la cryptographie est la science visant à sécuriser l’échange de données, le hash est un outil de base, indispensable. Il s’agit d’une fondation essentielle à la plupart des systèmes cryptographiques.

Mais comme nous l’avons vu, un bon hash requiert des propriétés très strictes : **déterministe, chaotique, à sens unique et résistante aux collisions**. Un mauvais hash peut miner tout un édifice cryptographique : si l’attaquant peut trouver des collisions, il pourra introduire n’importe quel message dans le système !

C’est la raison pour laquelle il existe peu d’algorithmes de hashage très populaires et que ceux-ci sont d’une grande complexité interne.

Mais nul besoin de plonger dans la complexité. Si vous avez retenu et compris les quatre grandes propriétés, vous êtes armés pour mieux comprendre la cryptographie.

Le Petit Cryptographe est une initiative de l’UCL Crypto Group soutenu par le FEDER dans le cadre du projet CryptoMedia/UserMedia.
