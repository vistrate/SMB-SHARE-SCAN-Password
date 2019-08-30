# SMB-SHARE-SCAN-Password
Outils de scan de mot de mot de passe sur un partage réseau SMB

Analyse avec regex:
- contenu du fichier
- extension du fichier / Répertoire / nom

INPUT :
- 

OUTPUT:
Ressort pour extension du fichier:
	- hôte
	- date de création
	- propriétaire du fichier
	- nom du fichier
	- emplacement du fichier
	- taille du fichier
	- dernier utilisateur à l'avoir modifié
	
Ressort pour contenu du fichier:
	- idem qu'avant
	- on recher un élément probant (l'afficher)
	- emplacement du fichier	
	- numéro de la ligne
	- regex du fichier
	- si possible vérifier s'il y a un mot de passe de présent
	sur certains fichiers
  
  usage: main.exe [-h] [-u [USER]] [-p [PASSWORD]] [-ip [IP [IP ...]]] [-f [F]]
                [-v] [-c] [-regexfilename [REGEXFILENAME [REGEXFILENAME ...]]]
                [-regexoffice] [-regextxt]
                [-regexcontent [REGEXCONTENT [REGEXCONTENT ...]]]
                [-maxdepth [MAXDEPTH]] [-output [OUTPUT]] [-searchlastwriter]
                [-ntlmv1] [-portsmb [{139,445}]] [-domainname [DOMAINNAME]]
                [-clientmachinename [CLIENTMACHINENAME]]

optional arguments:
  -h, --help            show this help message and exit
  -u [USER], --user [USER]
                        Login d'un utilisateur
  -p [PASSWORD], --password [PASSWORD]
                        Mot de passe d'un utilisateur
  -ip [IP [IP ...]]     Adresse IP, Plage d'IP, hostname et sous-réseau. Il
                        est possible d'utiliser des ranges sur les 3 derniers
                        octets. Exemple : 10.0.0.1-2 -> 10.0.0.1 , 10.0.0.2 ou
                        une liste de plusieurs arguments à la suite Exemple:
                        10.0.0.1 localhost 10.0.0.0/24
  -f [F]                Chemin d'un fichier contenant des adresses
                        IP/Hostnames/Networks et le compte SMB associé (login
                        / mot de passes). Si des entrées sont mis en ligne de
                        commande. Par contre s'il n'y a pas d'entrées en ligne
                        de commande, le fichier peut suffire. Des adresses IP,
                        des plages d'ip, des subnets et des hostnames peuvent
                        être mis dedans dans la première colonne. Puis la
                        seconde colonne contient le login, et la troisième
                        colonne le mot de passe associée. Le fichier doit être
                        au format csv avec un ; comme séparateur. Exemple : -f
                        'toto.csv' Format d'un fichier en entrée contenant les
                        hôtes et login/mot de passe : ************************
                        ******************************* * Liste des
                        IP/Hostnames/Networks * Login/Mot de passe* **********
                        *********************************************
                        10.10.0.1 * toto / admin  john
                        / smith 10.0.0.0/24 * toto / admin 192.168.0.1-55 *
                        titi / 12345 ..............
  -v, --verbose         Permet de suivre l'avancement du scan
  -c, --scancontent     Scanne aussi le contenu du fichier à la recherche de
                        motif
  -regexfilename [REGEXFILENAME [REGEXFILENAME ...]]
                        Prends une liste de regex sur les noms de fichiers
  -regexoffice          Utiliser la regex sur les fichiers d'extension office
                        : xls, xlsm, xml, xlsx, doc, docx, ppt, pptx, pptm
  -regextxt             Utiliser la regex sur les fichiers d'extension texte :
                        txt, init, conf
  -regexcontent [REGEXCONTENT [REGEXCONTENT ...]]
                        Prends une liste de regex sur les contenus des
                        fichiers
  -maxdepth [MAXDEPTH]  Définit la profondeur maximale du scan
  -output [OUTPUT], -o [OUTPUT]
                        Chemin du fichier de sortie
  -searchlastwriter     Indique si le scan recherche aussi le dernier
                        utilisateur a avoir écrit dans le fichier
  -ntlmv1               Indique si ntlm version 1 doit être utilisée
  -portsmb [{139,445}]  Indique le numéro de port SMB (139 ou 445)
  -domainname [DOMAINNAME]
                        Indique le nom de domaine a utiliser.
  -clientmachinename [CLIENTMACHINENAME]
                        Indique le nom de machine cliente
