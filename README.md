# CC_Pipeline
Controle continu 

PARTIE 1 :

  1.  Quelles sont les ressources Terraform manquantes ? 
      Les ressources:  destination_S3_Bucket.tf et kinesis_datastream.tf

  2.  Modifications :
  Il a fallu rajouter le fichier : destination_S3_Bucket.tf   et modifier donc la ligne -- bucket = "analytics-destination-wxcft6aya123456" --, (j'ai rajouté 123456)
  ensuite, rajouter le fichier kinesis_datastream.tf et modifier le nom   -- name        = "datastream_ingestion"--
  annsi que la resource --resource "aws_kinesis_stream" "datastream_ingestion" --
  
  3. Test réussi de la pipeline (Images)

  4. Expliquez ce que fait cette application:
  L'application sert à écrire dans des flux de Amazon Kinesis Data Streams à l'aide de Kinesis Agent.
  
  
  5. A quoi sert la partie « user_data » dans le fichier « ec2.tf » ?
   La partie user_data sert à installer les différentes composantes dans le VM EC2 nécéssaires à l’exécution de l’application.
    
  6. Quel est le rôle de l’agent Kinesis sur la VM EC2 ?
  L'agent Kinesis permet d'envoyer des journaux depuis Amazon Elastic Compute Cloud (Amazon EC2) vers Amazon Kinesis.
  
  
 
 PARTIE 2 :
 
 1. Quelle est l’architecture de données de ce « data pipeline » ?
 Ingestion : Types de source : Logs site web / Outils : AWS Kinesis Data Streams / Type d'ingestion :Flux (streaming). 
 Notre pipeline récupère des logs générés par le script python chargé avec kinesis dataStream qui va lire les logs et les mettre dans la pipeline pour nous permettre de les traiter dans kinesis data anayltics.

 Stockage : Les objets de notre pipeline vont être stockés dans une bucket S3 de AWS avec le service kinesis firehose qui va mettre les objets dans la bucket. Outil : AWS S3 avec le service kinesis firehose.
 
 Transformation : Traitement (nettoyage et normalisation), analyse et compréhension des données / Outil AWS Kinesis Data Analytics.
 
 Exposition  : Accès au résultat de la transformation des données / Outil : Requetes SQL.
Après avoir traiter les données,on peut soit les exposer à des systèmes externes ou alors les stocker dans S3 via kinesis firehose.
 
 2. Schéma d’architecture (image)


 PARTIE 3 :

4. Comment appelle t on ce type de requête SQL ?

 On les appelle : requêtes SQL à fenêtres.
 
5. Une fenêtre délimite un groupe de données dans un flux, c pour ca que ca a un délai.

 
 
 
 
 
 
 
 
 
 
 
