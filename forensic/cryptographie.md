# Cryptographie - les bases

Historiquement, la cryptologie correspond à **la science du secret**, c'est-à-dire au chiffrement. Aujourd'hui, elle s’est élargie au fait de prouver qui est l'auteur d'un message et s'il a été modifié ou non, grâce aux signatures numériques et aux fonctions de hachage.

## Les grands principes

La cryptologie ne se limite plus aujourd’hui à assurer la **confidentialité** des secrets. Elle s’est élargie au fait d’assurer mathématiquement d’autres notions : assurer **l’authenticité** d’un message (qui a envoyé ce message ?) ou d'en assurer son **intégrité** (est-ce que le fichier a été modifié ?) ou encore sa **non-repudiation** (mécanisme qui permet d'enregistrer l'engagement d’une entité; de telle sorte que celle-ci ne puisse nier avoir accompli / pris ledit engagement.)

1. **L'intégrité**

La cryptologie permet justement de détecter si le message, ou l’information, a été involontairement modifié. Ainsi, une « fonction de hachage » permettra d’associer à un message, à un fichier ou à un répertoire, une empreinte unique calculable et vérifiable par tous. Cette empreinte est souvent matérialisée par une longue suite de chiffres et de lettres précédées du nom de l’algorithme utilisé, par exemple « SHA2» ou « SHA256 ».

Il ne faut pas confondre le chiffrement, qui permet d’assurer la confidentialité, c’est-à-dire que seules les personnes visées peuvent y avoir accès (voir « Pour assurer la confidentialité du message »), et le hachage qui permet de garantir que le message est intègre, c'est-à-dire qu’il n’a pas été modifié.

**Le hachage, pour quoi faire ?** 
> Pour sauvegarder vos photos sur votre espace d’hébergement (de type « cloud » par exemple) et  vérifier que votre téléchargement s’est bien déroulé ?
> Pour sychroniser vos dossiers et détecter ceux qu’il faut sauvegarder à nouveau et ceux qui n’ont pas été modifiés ?


2. **Authenticité**

Au même titre que pour un document administratif ou un contrat sur support papier, le mécanisme de la « signature » - numérique - permet de vérifier qu’un message a bien été envoyé par le détenteur d’une « clé publique ». Ce procédé cryptographique permet à toute personne de s’assurer de l’identité de l’auteur d’un document et permet en plus d’assurer que celui-ci n’a pas été modifié.

**La signature numérique, pour quoi faire ?**
> Vous voulez garantir être l’émetteur d’un courriel ?
> Vous voulez vous assurer qu’une information provient d’une source sûre ?

Pour pouvoir signer, Alice doit se munir d’une paire de clés :   

l’une, dite « publique », qui peut être accessible à tous et en particulier à Bob qui est le destinataire des messages qu’envoie Alice ;   
l’autre, dite « privée », qui ne doit être connue que d’Alice.   
En pratique, Alice génère sa signature avec sa clé privée qui n’est connue que d’elle. N’importe quelle personne ayant accès à la clé publique d’Alice, dont Bob, peut vérifier la signature sans échanger de secret.


3. **La confidentialité**
Le chiffrement d’un message permet de garantir que seuls l’émetteur et le(s) destinataire(s) légitime(s) d’un message en connaissent le contenu. Une fois chiffré, faute de connaitre la clé spécifique, un message devient inaccessible et illisible. Que ce soit par les humains ou les machines.

Il existe deux grandes familles de chiffrement : le **chiffrement symétrique** et le **chiffrement asymétrique**.

### Chiffrement Symetrique

Le chiffrement symétrique permet de chiffrer et de déchiffrer un contenu avec la même clé, appelée alors la **« clé secrète »**. Le chiffrement symétrique est particulièrement rapide mais nécessite que l’émetteur et le destinataire se mettent d’accord sur une clé secrète commune ou se la transmettent par un autre canal. Celui-ci doit être **choisi avec précautions**, sans quoi la clé pourrait être récupérée par les mauvaises personnes, ce qui n’assurerait plus la confidentialité du message. 

!Chiffrement symetrique](https://raw.githubusercontent.com/ClimbingFromBottom/md-files/main/images/cryptographie/chifrement_symetrique.png)

Parmis les algorithmes de chiffrement symétrique les plus utilisés, on retrouve :
- [DES](https://fr.wikipedia.org/wiki/Data_Encryption_Standard) (Data Encryption Standard)
- [3DES](https://fr.wikipedia.org/wiki/Triple_DES) (Triple DES)
- [AES](https://fr.wikipedia.org/wiki/Advanced_Encryption_Standard) (Advanced Encryption Standard)
- [RC4](https://fr.wikipedia.org/wiki/RC4) (Rivest Cipher 4)

### Chiffrement Asymetrique

La cryptographie asymétrique résoud ce problème d'échange de clés.

Elle se base sur le principe de deux clés : **publique** & **privée**   
La clé publique permet le chiffrement, tandis que la clé privée permet le déchiffrement.

Comme son nom l'indique, la clé publique est mise à la disposition pour quiconque désire chiffrer et envoyer un message. Ce dernier ne pourra être déchiffré qu'avec la clé privée, qui doit rester confidentielle.   

Dans ce cas où l’émetteur (Alice) utilise la clé publique du destinataire (Betty) pour chiffrer le message tandis que le destinataire (Betty) utilise sa clé privée pour déchiffrer le message envoyé par Alice.   

Parmi ses avantages, la clé publique peut être connue de tous et publiée. Mais attention : il est nécessaire que les émetteurs aient confiance en l’origine de la clé publique, qu’ils soient sûrs qu’il s’agit bien de celle du destinataire.

#### Exemple : chiffrement asymétrique

Prenons l'exemple d'Alice, qui souhaite recevoir un message chiffré de la part de Betty. Pour cela, Alice envoie à Betty un cadenas ouvert; dont seul Alice possède la clé du cadenas.    

![Alice envoie sa clé publique à Betty](https://raw.githubusercontent.com/ClimbingFromBottom/md-files/main/images/cryptographie/01_alice_envoie_sa_clef.png)

Autrement dit, Alice envoie sa **clé publique** à Betty. Et garde secrète sa clé privée qui lui servira à ouvrir le cadenas plus tard.

Betty écrit un message et place celui-ci dans une boite; Boite qu'elle ferme avec le cadenas qu'Alice lui a envoyé.   

**/!\ Remarque** : On a pas beosin de posséder la clé d'un cadenas pour le fermer.

![Betty chiffre un message](https://raw.githubusercontent.com/ClimbingFromBottom/md-files/main/images/cryptographie/02_bob_chiffre_le_msg.png)

Une fois qui Betty a fermée la boite, elle va l'envoyé à Alice. Le message ne craint rien, puisqu'il est dans une boite que personne ne peut ouvrir (grace au cadenas). 

![Betty envoie un message chiffré à Alice](https://raw.githubusercontent.com/ClimbingFromBottom/md-files/main/images/cryptographie/03_bob_envoie_msg_chiffre.png)

**/!\ Note:** Cette boite ne peut etre ouverte que par Alice, car elle seule possède la clé du cadenas.

Alice recoit la boite avec le cadenas contenant le message de Betty. Elle peut ouvrir cette boite grace à la clé qu'elle possede (**clé privée**) et ainsi, lire le message que contient la boite.

![Alice déchiffre le message](https://raw.githubusercontent.com/ClimbingFromBottom/md-files/main/images/cryptographie/04_alice_dechiffre_le_msg.png)

**/!\ Remarque** : Avec la cryptographie asymétrique, la seule chose qui circule sur le réseau est "un cadenas ouvert" puis "une boite avec un cadenas fermé". Si une personne mal intentionnée intercepte le cadenas ouvert, rien de grave puisque cela ne lui permettra jamais d'ouvrir le cadenas fermé.


### Casser un chiffrement

Il est possible de casser un chiffrement, il existe de nombreuses méthodes, en voici 3:

#### **La force brute** (ou "Brute Force", en Anglais)

Le [brute force](https://en.wikipedia.org/wiki/Brute-force_attack) est une attaque très simple dans son principe. Elle consiste à essayer toutes les combinaisons possibles jusqu'à trouver la bonne. Une méthode d'une redoutable efficacité à laquelle aucun algorithme ne peut résister.   

L'incertitude du succès d'une attaque par force brute réside dans le temps nécessaire pour trouver le sésame. Cette variable dépend à la fois de la longueur du mot de passe ou de la clé de chiffrement et de la puissance du matériel informatique. Une attaque par force brute peut nécessiter de quelques minutes à plusieurs années selon la complexité du code à déchiffrer.

Il existe des formes variées d'attaque par force brute :   

**Attaque par dictionnaire** : des outils automatisés s'appuient sur un fichier de dictionnaire de mots courants et de leurs variantes sous forme de dialecte, d'argot ou avec des fautes d'orthographe ; [Exemple avec rockyou.txt](https://www.kaggle.com/wjburns/common-password-list-rockyoutxt)   
**Attaques basée sur des règles** : utilisent des règles pour tester des variantes de mot de passe en se servant, par exemple, d'une partie du nom d'utilisateur ;   
**Attaques basées sur la puissance de calcul** : un ordinateur personnel est capable de tester des centaines de milliers de combinaisons par seconde ; lorsque cela n'est plus suffisant, les assaillants peuvent avoir recours à l'informatique distribuée en faisant travailler plusieurs machines de concert ; il arrive aussi que les pirates fassent appel à des botnet qu'ils louent le temps nécessaire.


#### **La cryptanalyse**

C'est un ensemble des techniques permettant de retrouver un message en clair à partir du message chiffré, sans connaitre la clé de déchiffrement initialement.

**L’analyse fréquentielle** (Exemple avec le chiffement de César)   
On s’appuie sur la **fréquence des répétitions des lettres** du message chiffré pour en déduire la clé. Par exemple, en français, le E est la lettre la plus fréquente. Dans un algorithme par substitution comme le chiffre de César, un caractère qui revient fréquemment est potentiellement un E, ce qui permet de déduire le décalage et de décoder le message. C’est une **méthode qui est inefficace contre les algorithmes modernes**.   


Pour en savoir plus sur cette attaque, cliquez [ici](https://fr.wikipedia.org/wiki/Analyse_fréquentielle).

**L’analyse par mot probable** (Exemple avec la machine Enigma)      
On suppose probable l’existence d’un mot dans le message et on travaille dessus. Cette méthode est connue pour avoir permis le déchiffrement de la machine **Enigma** qui chiffrait les communications allemandes pendant la 2ème guerre mondiale. Comme toutes les communications allemandes étaient chiffrées, notamment à destination des sous-marins, les chercheurs ont supposé qu’il y avait, dans ce flot, des bulletins météo qui contiennent des informations normalisées. A partir de là, ils ont pu en déduire le système de chiffrement et décoder une grande partie des communications secrètes allemandes.

Pour en savoir plus sur cette attaque, cliquez [ici](https://fr.wikipedia.org/wiki/Attaque_par_mot_probable).

**L’analyse par canal auxiliaire**   
On s’accroche. Le principe est d’exploiter des propriétés inattendues des algorithmes de chiffrement. Ainsi, en exploitant la consommation électrique, le bruit, le temps de calcul, la fréquence du processeur, etc, on peut déduire des informations potentiellement précieuses pour décoder un message.   

Pour en savoir plus sur l'attaque par canal auxiliaire, cliquez [ici](https://fr.wikipedia.org/wiki/Attaque_par_canal_auxiliaire).


#### **L’homme du milieu (ou MITM pour "Man In The Middle", en anglais)**

Le principe est simple, même si la réalisation peut s’avérer plus compliquée. **L’attaquant se positionne au milieu de la conversation**, sans que ceux-ci ne soient au courant bien entendu. Chaque correspondant échange avec l’attaquant, pensant communiquer avec son correspondant autorisé, transmettant les clés secrètes et les messages.
L’attaquant peut alors déchiffrer, voire modifier, les messages en toute discrétion.   

![Man In The Middle](https://raw.githubusercontent.com/ClimbingFromBottom/md-files/main/images/cryptographie/MITM.png)

Cette attaque met le doigt sur l’absolue nécessité de **transmettre les clés par un canal sûr**. Sans la clé, l’attaquant ne peut rien faire. 

Pour en savoir plus sur l'attaque MITM, cliquez [ici](https://fr.wikipedia.org/wiki/Attaque_de_l%27homme_du_milieu).



#### Vocabulaire, abus de languages et tout le tintouin
**crytptographie != cryptologie**   
Cryptographie :   
- La cryptographie est l’art de chiffrer un message à l'aide d'une clé   

Cryptologie :   
- La cryptologie est la branche des mathématiques conprenant la cryptographie et la cryptanalyse   

- l’art de décrypter s’appelle la cryptanalyse
- un système de chiffrement s’appelle un cryptosystème
- un cryptographe est une personne qui conçoit des cryptosystèmes
- un cryptanaliste est une personne qui tente de casser les cryptosystèmes


--------- 
#### Sources
[Source 1](https://www.tala-informatique.fr/wiki/images/e/eb/Cryptographie.pdf)
[Source 2](https://www.cnil.fr/fr/comprendre-les-grands-principes-de-la-cryptologie-et-du-chiffrement)
[Source 3](https://fr.wikipedia.org/wiki/Cryptographie)