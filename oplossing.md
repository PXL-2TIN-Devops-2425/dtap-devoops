Vul onderstaande aan met de antwoorden op de vragen uit de readme.md file. Wil je de oplossingen file van opmaak voorzien? Gebruik dan [deze link](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) om informatie te krijgen over
opmaak met Markdown.


# test.jenkinsfile

Stage cleanup: we kijken of de image reeds bestaat, als deze aanwezig is verwijderen we de image. Hetzelfde voor de container.
![stage-cleanup](images/stage-cleanup.png)

Stage Install dependencies: we installeren de dependencies, npm.
![stage-install-dependencies](images/install-dependencies.png)

Stage Build artifact: we bouwen de image met docker.build
![stage-build](images/build-artifact.png)

Stage Push artifact: met behulp van de credentials van dockerhub pushen we de image naar de dockerhub van Fabian.
![stage-push-artifact](images/push-artifact.png)

Stage deployment: hier doen we een docker pull om de latest image van dockerhub binnen te halen. Hierna wordt er een container gestart.
![stage-deployment](images/deployment.png)


a) Om ervoor te zorgen dat Jenkins geen sudo nodig heeft om docker commando's uit te voeren, gebruik je volgend commando: 
![commando jenkins sudo rechten geven](images/oplossinga.png)

# production.jenkinsfile

Stage deploy prod: we gebruiken SSH-Agent om een verbinding op te zetten met de production server om de latest image van dockerhub binnen te halen.
![stage-deploy](images/deploy-prod.png)

Stage start prod: we gebruiken SSH-Agent om een verbinding op te zetten met de production server om een docker container te starten op de laatste image die in de vorige stage werd binnengehaald.
![stage-start](images/start-prod.png)

Stage test prod: in deze stage testen we of de applicatie werkt door een curl te doen naar het IP adres van de production server.
![stage-test](images/test-prod.png)

Cleanup: we gebruiken SSH-Agent om een verbinding op te zetten met de production server om hierna te kijken of de image reeds bestaat, als deze aanwezig is verwijderen we de image. Hetzelfde voor de container.
![stage-cleanup](images/cleanup-prod.png)
