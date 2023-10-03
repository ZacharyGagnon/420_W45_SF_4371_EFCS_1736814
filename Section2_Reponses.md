## Section 2 : Questionnaire

Vous devez répondre aux questions suivantes. Vos réponses seront incluses dans votre dépôt GitHub (voir la section remises).

### Concept 1 – Administration système – 16 points

1- Dans logical volume manager, expliquer la différence entre les volumes physiques, le groupe de volume et les volumes logiques. (3 points)  

Réponse : Les volume physique sont les collection de partion du disque qui sont sur le disque physique. les volume logique sont la pour donner a l'utilisateur le controle sur un volume physique. le groupe de volume est ce qu'il entre les volume physique et le volume logique qui peut comprendre plusieur volume logique et physique.


2- Nommez les trois types de connexion à distance présentés dans le cours et expliquez leurs raisons d’être. (3 points)  

Réponse : SSH: qui nous permet d'acceder a nos server de facon secure et qui est le successeur de telnet nous permettant de ouvrir un terminale et de faire des commade.

FTP: nous permettant de tranfere des fichier, les modifer et les supprimer entre notre ordinateur et un autre ordinateur sur le meme reseau.

SCP: nous sert a copier des fichier et repertoire de facon secure entre en utilisant SSH.

Les trois prochaines questions font références à l'image suivante :  

 
3- Pourquoi le deuxième champ du résultat de la commande est-il marqué d’un X ?
 (1 point)

Réponse : il indique que le mot de passe n'est pas dans le fichier passwd mais dans le fichier shadow


4- Donnez la raison d’être du dernier champ. (1 point)

Réponse : ces le shell de defaut de l'utilisateur qui vas etre utliser lorsque l'utilisateur est connecter


5- Est-ce qu’une autre valeur peut exister pour ce dernier champ ? Si oui, précisez. (1 point)

Réponse : oui puisque bash n'est pas le seul shell qui peut etre utiliser par le systeme comme par exemple zsh qu'ont pourrait mettre a place de bash ce qui fait que lorsque l'utilisateur vas ce connecter le systeme vas utiliser zsh


Les quatres prochaines questions font références à l'image suivante :  

 
6- Quelle information vous donne la ligne se terminant par un point ? (1 point) 

Réponse : il nous dis le repertoire ou ont ce trouve en ce moment


7- Quelle information vous donne la ligne se terminant par deux points ? (1 point) 

Réponse : ces le repertoire de niveau inferieur de celui que nous somme en ce moment 


8- Quels sont les droits sur le fichier toto.txt ? (3 points)

Réponse : read write pour l'utilisateur, read pour le groupe et read pour tous.



9- Quelle commande (en forme octale), allez-vous utiliser pour modifier les droits sur le fichier toto.txt pour que ceux-ci soient maintenant les suivants : (2 points)  
 
Réponse : chmod 755 toto.txt


### Concept 2 – Docker – 17 points

Soit le fichier « Dockerfile » suivant :  

|#  | Instruction|
|---|---|
|1	 |FROM mcr.microsoft.com/dotnet/core/sdk:3.0 AS build|
|2	 |WORKDIR /app|
|3	 |COPY *.sln .|
|4	 |COPY aspnetapp/*.csproj ./aspnetapp/|
|5	 |RUN dotnet restore/|
|6	 |COPY aspnetapp/. ./aspnetapp/|
|7	 |WORKDIR /app/aspnetapp|
|8	 |RUN dotnet publish -c Release -o out|
|9	 ||
|10 |FROM mcr.microsoft.com/dotnet/core/aspnet:3.0 AS runtime|
|11 |WORKDIR /app|
|12 |COPY --from=build /app/aspnetapp/out ./|
|13	 |ENTRYPOINT ["dotnet", "aspnetapp.dll"]|

10- Donnez l’explication de chaque ligne du fichier (3 points)

|#  | Instruction|
|---|---|
|1|Definni l'image de base utiliser par le docker|	
|2|definni le working directory dans le docker|	
|3|copy les fichier de solution .sln du host vers le docker|	
|4|copy les fichier .csproj du dossier aspnetapp de l'host vers le dossir aspnetapp du docker|	
|5|restore les nuget package du projet dependament du .csproj copier plus tot|	
|6|copy le dossier aspnetapp de l'host vers le dossier aspnetapp du docker|	
|7|definni le working directory dans le docker etant maintenant aspnetapp|	
|8|build et publishe l'application avec la configuration Release dans le dossier out|	
|9|rien|	
|10|cree une autre image a partir qui permet de partir l'application|	
|11|definni le working directory dans la nouvelle image|	
|12|copy ce que le le build de la premiere image a mis dans le out|	
|13|definni le point d'entre du docker qui dit que quand il ouvre il devrait executer le aspnetapp.dll|	

11- Dans un Dockerfile, expliquez la différence entre « ENTRYPOINT » et « CMD ». (1 point)

Réponse : sont pratiquement pareil a part que le cmd donne l'argument par defaut a une commade et ne peut en avoir qu'une seul tandis que entrypoint donne la commande par defaut et ces argument et ont peut en avoir plusieur.

12- À quoi servent les volumes dans Docker ? Expliquez ce qui peut se passer sans. (2 points)

Réponse : les volume servent a la persistance des donne puique sans eux les donne reste dans le docker et le docker est ferme tout les donne sont perdu aussi donc ce que fait les volume ces prendre les donner du docker pour les mettre sur la machine host


13- Quels sont les différents types de volumes dans Docker ? Expliquez l’utilisation des deux types utilisés dans le cours. (2 points)

Réponse : les volume bind mount qui permette de montter un chemin du conteneur a un chemin de l'hote et les volume normale qui cree un un emplacement en dehors du systeme de fichier du docker qui garde les donne independament du docker.


14- Quels sont les différents types de réseau de base dans Docker ? Expliquez le fonctionnement de chacun des types. En quoi le choix d’un réseau influence-t-il la sécurité ? (4 points)

Réponse : le reseau par defaut est le bridge network qui connect les docker a reseau nomme bridge par defaut qui permet a tout les docker sur le meme bridge de communiquer ensemble mais pas aux autre docker sur un autre bridge et il peuvent touts communiquer avec le reseau de l'hote via NAT. Le host network utlise le network du host directement sans le NAT ce qui fait que le container aura de meilleur performance. Le custom network nous permet de cree notre propre reseau pour le docker ce qui nous permet l'utlisation d'un DNS qui rend le docker securiser.


15- Quel est l’intérêt d’utiliser Docker-Compose ? Qu’-est ce que ça permet de faire ? Qu’elle ait la différence avec Dockerfile ? Dans quel type d’environnement ça peut être utilisé ? (5 points)

Réponse : docker-compose nous permet de creer nos propre  docker personnaliser de plus utiliser docker-compose nous permet de facilement monte des docker et de les utiliser. donc lorsque un docker-compose est fait il reste la pret etre utiliser en une seule commande rapide. la difference avec dockerfile est que ont ne peut pas monte un docker avec une seule commande avec seulement un dockerfile puisque ces une image donc un docker-compose utilise un dockerfile. et cela peut etre tres utile dans un environment de travaille ou ont utilise souvent des docker et que ce sont les meme a cahque fois. 


### Concept 3 – Les services – 12 points

16- Expliquez la différence entre un serveur et un service. (2 points)

Réponse : un serveur est une machine physique ou virtuel qui est specialiser pour recevoir des demnade et donne des service qui sont generalement des programme specific qui sont offert aux utilisateur donc une utilisateur communique avec les serveur qui offre des service a celui-ci 


17- Dans le serveur Web httpd (Apache), donnez quatre (4) conteneurs (conteneur Apache et non Docker) pouvant accueillir les directives de configuration. (4 points)

Réponse : le conteneur global, le conteneur de l'hote virtuel, le conteneur de dossier et le conteneur de fichier.


18- À quoi sert la notion d’hôte virtuel dans les serveurs Web. (2 points)

Réponse : sert avoir plusieur conteneur qui reponde aux demande du meme nom de serveur donc quand plusieur personne recherche www.google.com elles sont diriger sur plusieur conteneur different. 


19- Serveur Nginx, dans quel bloc doit être placée la directive listen ? Qu’elle est sa fonction ? (2 points)

Réponse : la directive doit etre placer dans le bloc server et sert a dire aux nginx sur quel port ecouter exemple listen 80;


20- À quoi sert la directive try\_files dans Nginx ? (2 points)

Réponse : elle sert a cree une liste the fichier ou d'url que le proxy devrait essayer quand il veut recupere des resource.


### Concept 4 – L’automatisation – 5 points

21- À quel endroit intervient l’automatisation d’un processus DevOps ? (3 points)

Réponse : lors de la production


22- Pourquoi les développeurs ont-ils besoin d’automatisation ? (2 points)

Réponse : puique les chose manuel prennent plus de temp et donc plus d'argent de plus l'automatisation n'est pas sujette a l'erreur humaine et est facilement testable
