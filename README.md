
## ${\color{#f79646}\text{Systèmes d’exploitation Séance 1}}$

## ${\color{#8db3e2}\text{Plan de Cours :}}$

- Systèmes d’exploitation UNIX
- Processus et Ressources
- Synchronisation
- Ordonnancement
- Gestion de mémoire

### ${\color{#8db3e2}\text{Rappel de la différence entre Flash NAND et Flash NOR}}$

<img width="1033" height="612" alt="image" src="https://github.com/user-attachments/assets/62c9fc9d-2bc4-4679-a07c-88da70e43792" />

---

### ${\color{#8db3e2}\text{L'ordinateur contient}}$

- **Le processeur (CPU) :** Le cerveau qui exécute les instructions.
- **La mémoire vive (RAM) :** La mémoire temporaire rapide pour les tâches en cours.
- **Le disque dur / SSD :** Le stockage permanent des fichiers et du système d'exploitation.
- **La carte mère :** La carte principale qui relie tous les composants entre eux.
- **L'alimentation (PSU) :** Le bloc qui fournit l'électricité à tout le système.
- **La carte graphique (GPU) :** Le composant dédié à l'affichage et au traitement des images.
- **Les périphériques d'entrée** (clavier, souris, microphone, scanner) envoient des données à l'ordinateur, tandis que les **périphériques de sortie** (écran, haut-parleurs, imprimante) les reçoivent pour les afficher ou les émettre.
- **Les interfaces de connexion réseau (NIC / WiFi) :** Cartes et puces permettant la communication via câble Ethernet ou WiFi.
- **L'horloge système (Clock) :** Synchronise et cadence le fonctionnement de tous les composants.

---

### ${\color{#95b3d7}\text{La structure en couches d'un système informatique}}$

![alt text](https://github.com/user-attachments/assets/55358471-22a3-4fe8-9b92-b49f90f174e5)
#### ${\color{#95b3d7}\text{Le Système d'Exploitation (SE / OS)}}$

${\color{#f79646}\textbf{Définition :}}$  
Le système d'exploitation est un ensemble de programmes qui agit comme un **intermédiaire entre l'utilisateur (ou les programmes applicatifs) et le matériel de l'ordinateur (périphériques, processeur, mémoire)**. Son rôle principal est de gérer les ressources matérielles et de fournir un environnement simple pour exécuter les applications.

##### ${\color{#00b0f0}\textbf{Note :}}$

**L'Horloge système (Clock) :** Génère des impulsions régulières (événements périodiques) utilisées par le SE pour :

- Mesurer et imposer le **quantum de temps** (partage du processeur entre les processus).
- Mettre à jour **l'heure système**.
- Gérer les **délais et temporisations (timers)**.

---

### ${\color{#95b3d7}\text{Le Rôle de la Machine Virtuelle (Système d'Exploitation)}}$

Le rôle principal du système d'exploitation, en tant que **machine virtuelle**, est de **masquer la complexité matérielle** (les détails de bas niveau) et de fournir aux utilisateurs et aux applications une interface simplifiée et abstraite.  
Il accomplit cette tâche en prenant en charge :

- **La gestion des fichiers :** Masque la structure physique du stockage.
- **La gestion des périphériques :** Abstrait le fonctionnement des composants d'entrée/sortie.
- **La gestion du temps et de l'horloge :** Gère la synchronisation et l'attribution des quantums de temps.
- **L'interprétation des commandes :** Fournit un environnement d'exécution pour les instructions utilisateur.

---

### ${\color{#95b3d7}\text{Les Services d'un Système d'Exploitation}}$

- **Aide à la création d'applications :** Fournit des outils (éditeurs, débogueurs, bibliothèques) pour faciliter le développement des programmes.
- **Exécution des programmes :** Charge les programmes en mémoire vive, gère leur exécution et termine leur processus proprement.
- **Accès contrôlé aux périphériques d'E/S (Entrées/Sorties) :** Masque les détails matériels et gère les lectures/écritures sur les périphériques.
- **Accès contrôlé aux fichiers :** Gère la création, la lecture, la modification, la suppression et les autorisations d'accès aux fichiers.
- **Accès contrôlé au système informatique (Sécurité) :** Protège les ressources contre les accès non autorisés et gère les droits des utilisateurs.
- **Détection et gestion des erreurs :** Détecte les pannes matérielles ou logicielles et réagit sans faire planter tout le système.
- **Comptabilité de l'utilisation des ressources :** Mesure le temps CPU, la mémoire utilisée et l'espace disque consommés par chaque utilisateur ou processus.

---

### ${\color{#95b3d7}\text{La gestion des ressources}}$

> **« Le système d'exploitation permet l'ordonnancement et le contrôle de l'allocation des ressources (processeur, mémoire et périphériques d'E/S) entre les différents programmes qui y font appel. »**

---

### ${\color{#95b3d7}\text{Les Objectifs Principaux d'un Système d'Exploitation}}$

- ${\color{#00b0f0}\textbf{Efficacité :}}$ Optimiser l'utilisation des ressources matérielles (processeur, mémoire) pour obtenir les meilleures performances possibles.
- ${\color{#00b0f0}\textbf{Cohérence :}}$ Maintenir la stabilité du système et la fiabilité des données en gérant les accès simultanés sans conflit.
- ${\color{#00b0f0}\textbf{Équité :}}$ Partager les ressources de manière juste entre les différents utilisateurs et programmes, sans qu'un processus ne bloque les autres.
- ${\color{#00b0f0}\textbf{Protection :}}$ Sécuriser le système en empêchant les accès non autorisés et en isolant les programmes pour qu'une erreur dans l'un n'affecte pas l'ensemble de la machine.

---

### ${\color{#95b3d7}\text{Les Fonctions Principales du Système d'Exploitation}}$

- ${\color{#00b0f0}\textbf{Gestion des processus :}}$ Allocation du processeur (CPU) aux différents programmes en cours d'exécution.
- ${\color{#00b0f0}\textbf{Gestion des objets externes (Système de fichiers) :}}$ Organisation, création, lecture et stockage principal des fichiers.
- ${\color{#00b0f0}\textbf{Gestion des entrées / sorties (E/S) :}}$ Contrôle du flux de données entre l'ordinateur et les périphériques.
- ${\color{#00b0f0}\textbf{Gestion des périphériques via les pilotes (Drivers) :}}$ Permet d'accéder aux matériels grâce à des logiciels d'interface spécifiques.
- ${\color{#00b0f0}\textbf{Gestion de la mémoire :}}$ Organisation de la mémoire vive (RAM) à l'aide de mécanismes comme la **segmentation** et la **pagination**.
- ${\color{#00b0f0}\textbf{Gestion de la concurrence :}}$ Synchronisation de l'accès aux ressources partagées pour éviter les conflits entre processus.
- ${\color{#00b0f0}\textbf{Gestion de la protection et de la sécurité :}}$ Vérification et respect des droits d'accès aux ressources du système.
- ${\color{#00b0f0}\textbf{Gestion des accès au réseau :}}$ Prise en charge de l'échange de données et de la communication avec d'autres machines à distance.

---

### ${\color{#95b3d7}\text{Les Caractéristiques d'un Système d'Exploitation}}$

- ${\color{#245bdb}\textbf{Monoutilisateur / Multiutilisateur :}}$ Un seul utilisateur à la fois vs. plusieurs utilisateurs simultanés.
- ${\color{#245bdb}\textbf{Préemptif / Non préemptif :}}$ Le système peut interrompre un processus en cours vs. le processus garde le processeur jusqu'à libération volontaire.
- ${\color{#245bdb}\textbf{Monotâche / Multitâche :}}$ Exécution d'un seul programme à la fois vs. exécution de plusieurs programmes en parallèle.
- ${\color{#245bdb}\textbf{Mémoire avec ou sans protection :}}$ Protection de l'espace mémoire entre les processus vs. absence de cloisonnement.
- ${\color{#245bdb}\textbf{Avec ou sans Swap :}}$ Utilisation du disque (espace de swap) comme mémoire virtuelle vs. utilisation exclusive de la RAM.
- ${\color{#245bdb}\textbf{Système de fichiers (File System) :}}$ Prise en charge et gestion du stockage, des fichiers et des droits d'accès sur le disque.

---

### ${\color{#95b3d7}\text{Mémoire RAM privée (Private RAM)}}$

> **« La mémoire RAM privée est la partie de la mémoire vive affectée de manière exclusive à un processus spécifique, inaccessible aux autres processus. »**

---

## ${\color{#95b3d7}\text{1. Vue d'ensemble des systèmes de fichiers (Windows vs Linux)}}$

| **Caractéristique** | **Windows** | **Linux** |
|:---|:---|:---|
| **Système de fichiers** | NTFS | EXT4 |
| **Nom complet** | New Technology File System | Fourth Extended File System |
| **Journalisation** | Journalisation avancée | Journalisation performante |
| **Sécurité** | Permissions et ACL | Permissions Unix et ACL |
| **Compatibilité** | Prise en charge des grands volumes | Rétrocompatibilité avec certaines fonctionnalités d'EXT2/EXT3 |
| **Allocation des données** | Gestion des clusters | Allocation par blocs et extents |
| **Utilisation principale** | Systèmes Windows | Systèmes Linux |

## ${\color{#95b3d7}\text{2. Structure d'Allocation : Secteurs vs Clusters (Blocs)}}$

Un **secteur** est la plus petite unité physique de stockage sur un disque durement formaté.  
Un **cluster** (ou bloc sous Linux) est la plus petite unité logique d'allocation gérée par le système d'exploitation.

- **Secteur physique standard :** $512\text{ octets} = 0,5\text{ Ko}$ (ou $4096\text{ octets} = 4\text{ Ko}$ sur les disques Advanced Format 4Kn).
- **Cluster par défaut (standard) :** $4\text{ Ko} = 8\text{ secteurs physiques } (8 \times 0,5\text{ Ko})$.
- **Taille maximale usuelle d'un cluster :** $32\text{ Ko} = 64\text{ secteurs physiques } (64 \times 0,5\text{ Ko})$.

## ${\color{#95b3d7}\text{3. Relations, tailles et limites}}$

- **Secteur physique :** taille standard de 512 octets, pouvant atteindre 4 Ko.
- **Cluster (NTFS / EXT4) :** unité d'allocation des données, généralement de 4 Ko.
- **Nombre de secteurs par cluster :** Taille du cluster / Taille du secteur. Exemple : 4 Ko = 8 secteurs de 512 octets.
- **Taille maximale d'un fichier :**
  - **NTFS :** jusqu'à plusieurs pétaoctets selon les spécifications.
  - **EXT4 :** jusqu'à environ 16 Tio.
- **Taille maximale d'un volume :**
  - **NTFS :** dépend de la taille des clusters et de la configuration.
  - **EXT4 :** jusqu'à 1 Eio théorique.

---

## ${\color{#95b3d7}\text{4. Calculs d'Allocation et Exemple Pratique}}$

##### ${\color{#7030a0}\text{Formules clés :}}$

$$\text{Taille du Cluster (Ko)} = \text{Nombre de Secteurs} \times 0,5\text{ Ko}$$

$$\text{Nombre de Secteurs} = \frac{\text{Taille du Cluster}}{0,5\text{ Ko}}$$

##### ${\color{#7030a0}\text{Exemple de calcul pour la taille maximale usuelle :}}$

$$\text{Taille Max Cluster} = 64 \times 0,5\text{ Ko} = 32\text{ Ko}$$

##### ${\color{#f79646}\text{Impact du Clustering (Espace perdu / Slack Space) :}}$

- Si un fichier fait $1\text{ Ko}$ et est stocké dans un cluster de $4\text{ Ko}$, le système réserve $4\text{ Ko}$ sur le disque.
- **Espace utilisé :** $1\text{ Ko}$
- **Espace perdu (Slack Space) :** $4\text{ Ko} - 1\text{ Ko} = 3\text{ Ko}$

---

### ${\color{#95b3d7}\text{Le Système de Gestion de Fichiers (SGF)}}$

- ${\color{#00b0f0}\textbf{Rôle d'organisation et d'optimisation :}}$ Assure l'organisation, la structuration et l'implémentation des données sur le disque de manière optimale.
- ${\color{#00b0f0}\textbf{Gestion de l'espace disque :}}$ Permet au système d'exploitation d'allouer, d'utiliser et de gérer l'espace disque pour stocker, lire, modifier et supprimer des fichiers.
- ${\color{#00b0f0}\textbf{Unité de stockage de base (Clusters) :}}$ S'appuie sur la gestion des blocs ou clusters (l'ensemble de plusieurs secteurs physiques) comme unité minimale d'allocation de données.
- ${\color{#00b0f0}\textbf{Abstraction et nommage :}}$ Offre une arborescence (dossiers/fichiers) pour que l'utilisateur manipule des noms de fichiers sans se soucier des adresses physiques sur le disque.
- ${\color{#00b0f0}\textbf{Contrôle d'accès et sécurité :}}$ Gère les autorisations et les droits d'accès (lecture, écriture, exécution) sur les fichiers pour chaque utilisateur.

---

### ${\color{#95b3d7}\text{Le Cluster (Unité d'allocation d'espace disque)}}$

- ${\color{#00b0f0}\textbf{Définition de base :}}$ Le cluster (ou bloc) représente la plus petite unité d'allocation de stockage qu'un système d'exploitation peut attribuer à un fichier.
- ${\color{#00b0f0}\textbf{Composition :}}$ Un cluster est constitué d'un ou plusieurs secteurs physiques (généralement jusqu'à 64 secteurs) de 512 octets (ou 4 096 octets pour les disques Advanced Format).
- ${\color{#00b0f0}\textbf{Taille d'un cluster :}}$ La taille d'un cluster varie généralement entre 512 octets et 32 Ko, pouvant aller jusqu'à 64 Ko (voire plus selon le système de fichiers).
- ${\color{#00b0f0}\textbf{Allocation par nombre entier :}}$ Un fichier est toujours stocké sur un nombre entier de clusters. Un cluster ne peut pas être partagé entre deux fichiers différents.
- ${\color{#00b0f0}\textbf{Taille minimale occupée :}}$ Même un fichier de très petite taille (ex. 1 octet) occupe au minimum un cluster entier sur le disque.
- ${\color{#00b0f0}\textbf{Facteurs déterminants :}}$ La taille d'un cluster dépend du système d'exploitation, du système de fichiers choisi (NTFS, EXT4, FAT32) et de la taille de la partition gérée.
- ${\color{#00b0f0}\textbf{Impact sur la table d'allocation :}}$ La taille des clusters détermine le nombre d'entrées (adresses) que le système d'exploitation doit gérer dans sa table de fichiers.
- ${\color{#00b0f0}\textbf{Espace perdu (Fragmentation interne) :}}$ Plus la taille des clusters est grande, plus la perte d'espace disque est importante (phénomène de *Slack Space* / fragmentation interne), surtout lorsque le système gère de nombreux petits fichiers.

---

## ${\color{#f79646}\text{Systèmes d’exploitation Séance 2}}$

### ${\color{#95b3d7}\text{Classification des systèmes d'exploitation}}$

#### ${\color{#b2a2c7}\text{Selon les caractéristiques des machines}}$

- **Mono-tâche / Multi-tâches**
- **Mono-utilisateur / Multi-utilisateurs**

#### ${\color{#b2a2c7}\text{Selon leur fonctionnement}}$

- **Système centralisé :** les ressources et les traitements sont gérés par une seule machine.
- **Système réparti (Distributed System) :** les ressources et les traitements sont répartis entre plusieurs machines.

### ${\color{#95b3d7}\text{Familles UNIX et Linux}}$

- **Famille UNIX :** FreeBSD, Solaris.
- **Famille Linux :** Debian, Ubuntu, Kali Linux, Arch Linux.

### ${\color{#95b3d7}\text{Système Centralisé vs. Système Réparti}}$

#### ${\color{#b2a2c7}\text{Système Centralisé :}}$

- **Présence locale :** L'ensemble du système d'exploitation est entièrement présent sur la machine considérée.
- **Gestion des ressources :** Le système ne gère directement que les ressources physiques (CPU, mémoire, disque) de la machine sur laquelle il est installé.
- **Machines reliées :** Si les machines sont reliées en réseau, elles fonctionnent comme des entités autonomes gérant chacune leurs propres ressources sous un système centralisé local.

#### ${\color{#b2a2c7}\text{Système Réparti (Distribué) :}}$

- **Distribution des abstractions :** Les différentes abstractions du système (processus, mémoire, système de fichiers) sont réparties sur un ensemble de machines interconnectées (sites ou nœuds).
- **Illusion d'une machine unique (Abstraction) :** Le système réparti agit comme une **machine virtuelle monoprocesseur** géante, masquant la complexité du réseau à l'utilisateur (transparence de localisation).
- **Partage et coopération :** Permet la gestion globale et l'utilisation transparente des ressources partagées à travers tout le réseau.
- **Transparence de localisation :** L'utilisation d'une ressource n'est pas liée à sa position physique ; l'utilisateur lance un programme sans connaître le nom de la machine qui l'exécute.
- **Exploitation du parallélisme :** Répartit les calculs sur plusieurs machines d'un domaine pour maximiser les performances.
- **Gestion des pannes et résilience :** Apporte des solutions aux défaillances matérielles en basculant la charge sur d'autres machines du réseau.

### ${\color{#95b3d7}\text{Selon la capacité d'évolution (Ouverture du système)}}$

- ${\color{#548dd4}\textbf{Système fermé (ou propriétaire) :}}$
  - Système dont le code source est privé et non modifiable par les utilisateurs.
  - **Extensibilité réduite :** Lorsqu'on veut ajouter de nouvelles fonctionnalités à un système fermé, il faut remettre en cause sa conception initiale et refaire une réécriture/architecture complète du système.
  - **Interopérabilité limitée :** Pas ou peu d'échanges en parallèle avec d'autres systèmes de types différents.
- ${\color{#548dd4}\textbf{Système ouvert :}}$
  - Système basé sur des standards ouverts (ex : UNIX/Linux, POSIX) facilitant son évolution, son extensibilité et la portabilité des applications sur différentes architectures.

### ${\color{#95b3d7}\text{Selon l'architecture matérielle}}$

- ${\color{#548dd4}\textbf{Architecture monoprocesseur :}}$
  - Gère un seul processeur. Fonctionne en mode temps partagé, multiprogrammation et avec mémoire protégée.
- ${\color{#548dd4}\textbf{Architecture multiprocesseur (Parallélisme) :}}$
  - Gère plusieurs processeurs travaillant en parallèle pour exécuter des tâches simultanément.
- ${\color{#548dd4}\textbf{Système réparti (ou distribué) :}}$
  - Exécute des tâches sur un ensemble de machines interconnectées à travers un réseau.

### ${\color{#95b3d7}\text{Cas d'UNIX et des systèmes ouverts}}$

- **Origine et évolution :** UNIX est devenu le modèle de référence pour les systèmes ouverts grâce à sa modularité et au respect de normes d'interopérabilité.
- **Compatibilité :** Contrairement aux anciens systèmes fermés qui ne permettaient pas d'échanger avec d'autres systèmes différents, les systèmes ouverts permettent la communication et l'échange de données entre architectures hétérogènes.

### ${\color{#95b3d7}\text{Les Systèmes Ouverts}}$

- ${\color{#548dd4}\textbf{Extensibilité accrue :}}$
  - Possibilité d'ajouter de nouvelles fonctionnalités et abstractions sans repenser le système initial.
  - Capacité d'évolution à chaud : ajout de modules sans devoir arrêter la machine.
- ${\color{#548dd4}\textbf{Architecture modulaire :}}$
  - Conception souvent basée sur un modèle **Client-Serveur** interne (ex : micro-noyaux).
- ${\color{#548dd4}\textbf{Communication et interopérabilité :}}$
  - Nécessite des modules spécialisés pour assurer la communication et l'échange fluide entre systèmes différents.

### ${\color{#95b3d7}\text{Architectures Monoprocesseur (Temps Partagé / Multiprogrammation)}}$

- ${\color{#548dd4}\textbf{Gestion d'une ressource unique :}}$
  - Présence d'un seul processeur physique (CPU).
  - Mise en place de mécanismes d'ordonnancement pour offrir un **pseudo-parallélisme** à l'utilisateur.
- ${\color{#548dd4}\textbf{Commutation rapide (Context Switching) :}}$
  - Le système passe très rapidement d'un processus à un autre.
  - Cette vitesse de commutation donne l'**illusion d'un parallélisme** (exécution simultanée) alors que les tâches sont exécutées en réalité en alternance.

### ${\color{#95b3d7}\text{Architectures Multiprocesseur (Parallélisme Réel)}}$

- ${\color{#548dd4}\textbf{Diversité matérielle :}}$
  - Existe sous plusieurs formes et classifications (mémoire partagée, mémoire distribuée, etc.).
- ${\color{#548dd4}\textbf{Modèle SIMD (Single Instruction, Multiple Data) :}}$
  - Tous les processeurs exécutent la **même instruction** au même moment.
  - Chaque processeur applique cette instruction sur des **données différentes** (ex : traitements vectoriels, processeurs graphiques GPU).

### ${\color{#95b3d7}\text{Caractéristiques Principales d'UNIX / POSIX}}$

- ${\color{#548dd4}\textbf{Multitâche (Multitasking) :}}$
  - Un même utilisateur peut exécuter plusieurs processus ou travaux simultanément.
- ${\color{#548dd4}\textbf{Interactivité et modes d'exécution :}}$
  - Dialogue en temps réel avec le système.
  - Prise en charge des tâches en arrière-plan (*background*) et des traitements en différé (*batch* / tâches planifiées).
- ${\color{#548dd4}\textbf{Organisation arborescente :}}$
  - Système de fichiers hiérarchisé sous forme d'arbre à partir d'une racine unique (`/`).
- ${\color{#548dd4}\textbf{Sécurité et protection :}}$
  - Authentification des utilisateurs (identifiant et mot de passe).
  - Gestion stricte des permissions sur les fichiers (lecture `r`, écriture `w`, exécution `x`) et privilèges d'administration attribués au super-utilisateur (`root`).
- ${\color{#548dd4}\textbf{Entrées/Sorties simplifiées (principe « Tout est fichier ») :}}$
  - Les périphériques matériels sont représentés par des fichiers spéciaux (situés dans `/dev`) et manipulés comme des fichiers ordinaires.
- ${\color{#548dd4}\textbf{Interface de commande (Le Shell) :}}$
  - Utilisation d'un interpréteur de commandes (ex : `bash`, `sh`) servant d'interface entre l'utilisateur et le système.

### ${\color{#95b3d7}\text{Architecture en Couches du Système}}$

$$\text{Matériel (Hardware)} \longrightarrow \text{Noyau (Kernel)} \longrightarrow \text{Shell / Applications} \longrightarrow \text{Utilisateur}$$

---

### ${\color{#95b3d7}\text{Rôle du Noyau (Kernel)}}$

- ${\color{#548dd4}\textbf{Cœur du système :}}$
  - Composant central et indispensable assurant l'interface directe avec le matériel.
- ${\color{#548dd4}\textbf{Fonctions de base :}}$
  - Gestion de la mémoire et de l'espace d'adressage.
  - Ordonnancement du processeur (allocation des temps CPU aux processus).
  - Traitement des interruptions et communication avec les périphériques matériels.

### ${\color{#95b3d7}\text{Architecture et Rôle du Noyau (Kernel)}}$

- ${\color{#548dd4}\textbf{Principales fonctions du noyau :}}$
  - **Gestion des ressources :** Allocation de la mémoire vive et temps processeur.
  - **Gestion des processus :** Création, exécution et ordonnancement des tâches.
  - **Gestion du système de fichiers :** Organisation et stockage des données sur le disque.
  - **Gestion des Entrées/Sorties (E/S) :** Communication avec les périphériques matériels.
- ${\color{#548dd4}\textbf{Interface Noyau-Utilisateur :}}$
  - L'utilisateur ne communique pas directement avec le noyau, mais passe par l'intermédiaire du **Shell**.

### ${\color{#95b3d7}\text{Le Shell et Utilitaires}}$

- ${\color{#548dd4}\textbf{Définition :}}$
  - Interpréteur de commandes pour les systèmes de type UNIX.
  - Sert à la fois d'interface de commande interactive et de langage de programmation (scripts shell).
- ${\color{#548dd4}\textbf{Utilitaires du système :}}$
  - Outils d'interfaçage fournissant des fonctionnalités de programmation, de gestion et de communication.
- ${\color{#548dd4}\textbf{Principaux Shells :}}$
  - **`sh` :** Bourne Shell
  - **`bash` :** Bourne Again Shell
  - **`csh` :** C Shell

### ${\color{#95b3d7}\text{Classification des Fichiers sous UNIX}}$

- ${\color{#548dd4}\textbf{Fichiers ordinaires :}}$
  - Contiennent des données sous forme de texte ou de binaires (ex : code source, exécutables, documents).
- ${\color{#548dd4}\textbf{Répertoires (Catalogues) :}}$
  - Fichiers spéciaux contenant la liste et les noms d'autres fichiers ou sous-répertoires.
- ${\color{#548dd4}\textbf{Fichiers spéciaux (Périphériques) :}}$
  - Fichiers associés directement aux périphériques matériels (ex : disques, terminaux, imprimantes).
- ${\color{#548dd4}\textbf{Liens symboliques :}}$
  - Fichiers contenant un pointeur (raccourci) vers un autre fichier ou répertoire.

### ${\color{#95b3d7}\text{Les Liens sous UNIX}}$ (`ln`)

- **Lien physique (*Hard Link*) :**
  - Crée un nouveau nom pointant directement vers le même i-nœud (même emplacement physique sur le disque).
- **Lien symbolique (*Symbolic Link*) :**
  - Fichier de référence qui pointe vers un autre fichier ou répertoire par son chemin (similaire à un raccourci).

### ${\color{#95b3d7}\text{Système de Fichiers et Navigation}}$

- **Répertoire de connexion (*Home Directory*) :**
  - À la connexion, l'utilisateur est automatiquement positionné dans son répertoire personnel (ex : `/home/user1` ou le bureau).
- **Déplacement dans l'arborescence :**
  - On utilise la commande `cd <nom_repertoire>` pour naviguer de manière hiérarchique à travers les dossiers.

### ${\color{#95b3d7}\text{Organisation de l'Arborescence du Système de Fichiers}}$ (`/`)

Le système de fichiers UNIX est structuré en une arborescence unique partant de la racine (`/`), contenant les répertoires principaux suivants :

- **`/bin` :** Contient les exécutables et commandes essentielles du système (accessibles à tous les utilisateurs).
- **`/sbin` :** Contient les commandes de base réservées à l'administration du système (réservées au super-utilisateur `root`).
- **`/usr` :** Contient les programmes, applications et fichiers secondaires/supplémentaires pour les utilisateurs.
- **`/lib` :** Contient les bibliothèques partagées (*libraries*) nécessaires aux exécutables du système.
- **`/dev` :** Contient les fichiers spéciaux représentant les périphériques matériels (ex : disques, terminaux, claviers, imprimantes).
- **`/tmp` :** Espace de stockage temporaire pour les fichiers éphémères.
- **`/home` :** Contient les répertoires personnels des différents utilisateurs (ex : `/home/al`).
- **`/etc` :** Contient les fichiers de configuration globale du système.

---

# ${\color{#95b3d7}\text{Chemins d'Accès, Navigation et Commande}}$ `ls`

## ${\color{#92d050}\text{Les Chemins d'Accès}}$

- **Nom de répertoire / fichier :**
  - Peut être **absolu** ou **relatif**.
- **Chemin absolu :**
  - Spécifie tout le chemin depuis la racine `/`.
  - *Remarque :* Un chemin absolu commence toujours par un `/`.
- **Chemin relatif :**
  - Spécifié par rapport au répertoire courant (actuel).
- **Caractère spécial `.` :**
  - Le caractère `.` désigne le répertoire courant.

## ${\color{#92d050}\text{Commandes de Déplacement (Navigation)}}$

- **`pwd`** (*Print Working Directory*) :
  - Affiche le nom et le chemin complet du répertoire courant.
- **`cd`** (*Change Directory*) :
  - Retourne automatiquement au répertoire de connexion de l'utilisateur (*Home Directory*).
- **`cd ..`** :
  - Monte d'un niveau dans la hiérarchie des répertoires (répertoire parent).
- **`cd ../..`** :
  - Monte de deux niveaux dans l'arborescence.

## ${\color{#92d050}\text{Affichage du Contenu d'un Répertoire}}$ (`ls`)

- **Syntaxe de base :**
  - `ls [option] <nom_repertoire>`
- **Option `-l` :**
  - Permet d'obtenir l'ensemble des informations et attributs détaillés de chaque fichier du répertoire.
- **Types de fichiers (premier caractère affiché par `ls -l`) :**
  - **`-`** : Fichier ordinaire.
  - **`d`** : Répertoire (*directory*).
  - **`b` ou `c`** : Fichiers spéciaux (*block* ou *character*).

### ${\color{#95b3d7}\text{Informations Détaillées sur les Fichiers}}$ (`ls -l`)

- ${\color{#548dd4}\textbf{Attributs affichés :}}$
  - Droits d'accès.
  - Nom du propriétaire.
  - Nombre de liens.
  - Taille du fichier.
  - Date de création / modification.
- ${\color{#548dd4}\textbf{Options de la commande}}$ `ls` :
  - **`ls -R` :** Affiche le contenu des fichiers et des répertoires de manière récursive (dans toute l'arborescence).
  - **`ls /` :** Affiche le contenu du répertoire racine du système.

### ${\color{#95b3d7}\text{Montage et Démontage des Systèmes de Fichiers}}$

- ${\color{#548dd4}\textbf{Commandes}}$ `mount` et `umount` :
  - Permettent de monter et de démonter un système de fichiers dans l'arborescence globale.
  - Le montage consiste à intégrer un périphérique de stockage (ex : clé USB, disque dur, partition) à un point de montage de l'arborescence existante.

### ${\color{#95b3d7}\text{Commandes de Gestion des Répertoires}}$

- ${\color{#548dd4}\textbf{Création d'un répertoire :}}$
  - `mkdir <nom_repertoire>` : Permet de créer un nouveau dossier.
- ${\color{#548dd4}\textbf{Suppression de répertoires :}}$
  - `rmdir <nom_repertoire>` : Supprime un répertoire s'il est vide.
  - `rm -r <nom_repertoire>` : Supprime de force un répertoire et tout son contenu de manière récursive.

### ${\color{#95b3d7}\text{Commandes de Gestion des Fichiers}}$

- ${\color{#548dd4}\textbf{Création d'un fichier vide :}}$
  - `touch <nom_fichier>` : Crée un fichier vide ou met à jour sa date de modification.
- ${\color{#548dd4}\textbf{Affichage du contenu :}}$
  - `cat <nom_fichier>` : Affiche le contenu textuel d'un fichier à l'écran.

---

## ${\color{#95b3d7}\text{Chemins d'Accès, Navigation et Affichage}}$

#### ${\color{#92d050}\text{Les Chemins d'Accès}}$

- **Nom de répertoire :** Peut être absolu ou relatif.
- **Chemin absolu :** Spécifie tout le chemin depuis la racine `/`.
  - *Remarque :* Un chemin absolu commence toujours par un `/`.
- **Chemin relatif :** Spécifié par rapport au répertoire courant (actuel).
- **Caractère spécial :** Le caractère `.` désigne le répertoire courant.

#### ${\color{#92d050}\text{Exemples de Commandes de Déplacement}}$

- **`pwd` :** Affiche le nom du répertoire courant.
- **`cd` :** Retourne au répertoire de connexion (*home directory*).
- **`cd ..` :** Monte d'un niveau dans la hiérarchie des répertoires.
- **`cd ../..` :** Monte de plusieurs niveaux dans l'arborescence.

#### ${\color{#92d050}\text{Affichage du Contenu d'un Répertoire}}$ (`ls`)

- **Syntaxe de base :** `ls [option] <nom_repertoire>`
- **Option `-l` :** Permet d'obtenir l'ensemble des informations détaillées relatives à chaque fichier du répertoire.
- **Signification des types de fichiers affichés :**
  - **`-` :** Fichier ordinaire.
  - **`d` :** Répertoire (*directory*).
  - **`b` ou `c` :** Fichiers spéciaux (périphériques).

---

## ${\color{#95b3d7}\text{Protection et Permissions des Fichiers}}$ (`chmod`)

#### ${\color{#92d050}\text{Introduction aux Permissions}}$

- L'accès aux fichiers est déterminé par **trois bits de permission** : Lecture (`r`), Écriture (`w`), Exécution (`x`).
- Ces permissions sont applicables à **trois classes d'utilisateurs** :
  - **Propriétaire (*User* - `u`)**
  - **Groupe (*Group* - `g`)**
  - **Autres (*Others* - `o`)** (ou tous : `a`)

#### ${\color{#92d050}\text{Mode Symbolique}}$ (`chmod`)

- **Syntaxe :** `chmod <qui><opération><permission> <fichier>`
- **Classes (`<qui>`) :**
  - `u` : Propriétaire (*User*)
  - `g` : Groupe
  - `o` : Autres (*Others*)
  - `a` : Tous (*All*)
- **Opérations (`<opération>`) :**
  - `+` : Ajouter une permission.
  - `-` : Retirer une permission.
- **Permissions (`<permission>`) :**
  - `r` : Lecture (*Read*)
  - `w` : Écriture (*Write*)
  - `x` : Exécution (*eXecute*)
- **Exemple :** `chmod g+w tp.c` (ajoute la permission d'écriture au groupe sur le fichier `tp.c`).

#### ${\color{#92d050}\text{Mode Octal / Numérique}}$ (`chmod`)

- **Valeurs numériques des permissions :**
  - `4` : Lecture (*Read*)
  - `2` : Écriture (*Write*)
  - `1` : Exécution (*eXecute*)
- **Principe :** On additionne les valeurs pour chaque classe (Propriétaire, Groupe, Autres).
- **Exemple :** `chmod 740 tp`
  - **`7` ($4+2+1$) :** Le propriétaire a tous les droits (Lecture, Écriture, Exécution).
  - **`4` ($4+0+0$) :** Le groupe a uniquement le droit de lecture.
  - **`0` ($0+0+0$) :** Les autres n'ont aucun accès (*inaccessible aux autres*).

---

## ${\color{#95b3d7}\text{La Commande}}$ `umask` ${\color{#95b3d7}\text{et Masque de Permissions par Défaut}}$

- ${\color{#f79646}\textbf{Principe :}}$ Contrairement à `chmod` qui modifie les permissions d'un fichier existant, `umask` définit les permissions par défaut appliquées lors de la création d'un nouveau fichier ou répertoire.
- **Valeurs de base par défaut :**
  - **`666`** pour les fichiers ordinaires.
  - **`777`** pour les répertoires.
- ${\color{#f79646}\textbf{Calcul :}}$ Les permissions finales sont obtenues en soustrayant la valeur du masque `umask` des valeurs de base par défaut.
- **Exemple avec `umask 022` :**
  - Fichiers : `666 - 022 = 644` (Propriétaire : lecture/écriture `rw-`, Groupe : lecture `r--`, Autres : lecture `r--`).

---

## ${\color{#95b3d7}\text{Gestion des Propriétaires et Utilisateurs}}$ (`chown`, `chgrp`, `whoami`, `id`)

- **`chown` :** Permet de changer le propriétaire d'un fichier.
- **`chgrp` :** Permet de changer le groupe associé à un fichier.
- **`whoami` :** Permet d'afficher le nom de l'utilisateur connecté.
- **`id` :** Affiche les identifiants réels et effectifs de l'utilisateur (UID, GID et groupes d'appartenance).

---

## ${\color{#95b3d7}\text{Types d'Entrées/Sorties Standard (E/S)}}$

- ${\color{#f79646}\textbf{Entrée standard (Standard Input - stdin) :}}$ Flux de données entrant dans le programme (généralement le clavier).
- ${\color{#f79646}\textbf{Sortie standard (Standard Output - stdout) :}}$ Flux de données sortant du programme (généralement l'écran).
- ${\color{#f79646}\textbf{Sortie d'erreur (Standard Error - stderr) :}}$ Flux réservé aux messages d'erreur du système ou des applications.

## ${\color{#95b3d7}\text{Redirection des E/S}}$

- **`>` :** Redirige la sortie standard vers un fichier (écrase le contenu existant du fichier s'il existe déjà).
- **`>>` :** Redirige et ajoute (*append*) la sortie standard à la fin d'un fichier (sans écraser le contenu existant).
- **`<` :** Redirige l'entrée standard pour qu'elle provienne d'un fichier au lieu du clavier.
- ${\color{#f79646}\textbf{Exemple avec}}$ `cat` :
  - `cat < fichier` : Redirige le contenu du fichier vers l'entrée standard de la commande `cat`.

## ${\color{#95b3d7}\text{Tubes de Communication (Pipes)}}$ `|`

- **Définition :** Permet de relier la sortie standard d'une première commande directement à l'entrée standard d'une commande suivante.
- **Syntaxe :** `commande1 | commande2`
