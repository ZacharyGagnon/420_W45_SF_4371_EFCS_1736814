## Section 2 : Questionnaire

Vous devez répondre aux questions suivantes. Vos réponses seront incluses dans votre dépôt GitHub (voir la section remises).

### Concept 1 – Administration système – 16 points

1- Dans logical volume manager, expliquer la différence entre les volumes physiques, le groupe de volume et les volumes logiques. (3 points)  

Réponse : Les volume physique sont les collection de partion du disque qui sont sur le disque physique. les volume logique sont la pour donner a l'utilisateur le controle sur un volume physique. le groupe de volume est ce qu'il entre les volume physique et le volume logique qui peut comprendre plusieur volume logique et physique.


2- Nommez les trois types de connexion à distance présentés dans le cours et expliquez leurs raisons d’être. (3 points)  

Réponse : SSH: qui nous permet d'acceder a nos server de facon secure et qui est le successeur de telnet nous permettant de ouvrir un terminale et de faire des commade.

ssss

Les trois prochaines questions font références à l'image suivante :  

 
3- Pourquoi le deuxième champ du résultat de la commande est-il marqué d’un X ?
 (1 point)

Réponse : 


4- Donnez la raison d’être du dernier champ. (1 point)

Réponse : 


5- Est-ce qu’une autre valeur peut exister pour ce dernier champ ? Si oui, précisez. (1 point)

Réponse : 


Les quatres prochaines questions font références à l'image suivante :  

 
6- Quelle information vous donne la ligne se terminant par un point ? (1 point) 

Réponse : 


7- Quelle information vous donne la ligne se terminant par deux points ? (1 point) 

Réponse : 


8- Quels sont les droits sur le fichier toto.txt ? (3 points)

Réponse : 



9- Quelle commande (en forme octale), allez-vous utiliser pour modifier les droits sur le fichier toto.txt pour que ceux-ci soient maintenant les suivants : (2 points)  
 

Réponse : 


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
|1||	
|2||	
|3||	
|4||	
|5||	
|6||	
|7||	
|8||	
|9||	
|10||	
|11||	
|12||	
|13||	

11- Dans un Dockerfile, expliquez la différence entre « ENTRYPOINT » et « CMD ». (1 point)

Réponse :


12- À quoi servent les volumes dans Docker ? Expliquez ce qui peut se passer sans. (2 points)

Réponse :


13- Quels sont les différents types de volumes dans Docker ? Expliquez l’utilisation des deux types utilisés dans le cours. (2 points)

Réponse :


14- Quels sont les différents types de réseau de base dans Docker ? Expliquez le fonctionnement de chacun des types. En quoi le choix d’un réseau influence-t-il la sécurité ? (4 points)

Réponse :


15- Quel est l’intérêt d’utiliser Docker-Compose ? Qu’-est ce que ça permet de faire ? Qu’elle ait la différence avec Dockerfile ? Dans quel type d’environnement ça peut être utilisé ? (5 points)

Réponse :


### Concept 3 – Les services – 12 points

16- Expliquez la différence entre un serveur et un service. (2 points)

Réponse : 


17- Dans le serveur Web httpd (Apache), donnez quatre (4) conteneurs (conteneur Apache et non Docker) pouvant accueillir les directives de configuration. (4 points)

Réponse :


18- À quoi sert la notion d’hôte virtuel dans les serveurs Web. (2 points)

Réponse :


19- Serveur Nginx, dans quel bloc doit être placée la directive listen ? Qu’elle est sa fonction ? (2 points)

Réponse :


20- À quoi sert la directive try\_files dans Nginx ? (2 points)

Réponse :


### Concept 4 – L’automatisation – 5 points

21- À quel endroit intervient l’automatisation d’un processus DevOps ? (3 points)

Réponse :


22- Pourquoi les développeurs ont-ils besoin d’automatisation ? (2 points)

Réponse :
