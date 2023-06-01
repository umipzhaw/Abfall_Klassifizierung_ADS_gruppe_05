# Abfall_Klassifizierung_ADS_gruppe_05
Classification of waste images using Convolutional Neural Network.

Es gibt zwei Programme:
Direkt auf dem Pc:                 Projekt_ADS_Carbage_classification_umiker_suvi_no_docker_github.ipynb
Über isolierte Container (docker): Projekt_ADS_Carbage_classification_umiker_suvi_with_docker_github.ipynb


!!!!!Wichtig
In der Vorschau auf Github sind nur bei folgendem Programm alle Plot/Grafiken vollstädig geladen.
Projekt_ADS_Carbage_classification_umiker_suvi_no_docker_github.ipynb
!!!!!!!!


#1 Ersetze alle API-secrets
 - Im Programm "Projekt_ADS_Carbage_classification_umiker_suvi_with_docker_github.ipynb" & "Projekt_ADS_Carbage_classification_umiker_suvi_no_docker_github.ipynb"
 - Dockerfiles=conf
 - Google-API
 - Kaggle-API
 - Flicker-API
 
 #2 Installiere alle Bibliotheken
  - Findet man im Dockerfile
 
 #3 Ausführung Docker
  - Docker und Yml und Ordner Conf müssen im gleichen Programm wie "Projekt_ADS_Carbage_classification_umiker_suvi_with_docker_github.ipynb" sein
  - Befehl: docker-compose up
   
 #4 Programm laufen lasse
  - json-Files müssen im gleichen Verzeichnis wie das auszuführende Programm sein.
  
