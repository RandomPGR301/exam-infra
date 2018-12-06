# PGR301 - DevOps - Eksamen
Eksamensoppgaven finnes her: [PGR301-Eksamen](https://github.com/PGR301-2018/oppgave-eksamen)

# Instruksjoner
    1. Fork de inleverte repositoriene, og lag deploy keys for disse.
    2. Endre pipeline.yml, og setter inn sine repositories under "source".
    3. Døp om filen credentials_example.yml til credentials.yml og legg inn dine egne hemmeligheter.
    4. I credentials.yml kan man også legge inn statuscake_api_key og logzio_token om man ønsker det.

    5. Fra repo/concourse kjører man så docker-compose up
    6. og så: fly --target tutorial login --concourse-url http://127.0.0.1:8080 -u admin -p admin
    7 Fra /repo kjører man så fly -t tutorial sp  -p heroku-example -c concourse/pipeline.yml -l credentials.yml
	8 Når pipeline er opprettet, copier link fra 'you can view your pipeline here:' og logg inn.
	9 Herfra kjører man først 'infra' jobben.
	10 Før man kjører deploy-app, må man logge inn på heroku og oppdatere config-var for GRAPHITE_HOST variabelen
	11 Kjør så deploy-app jobben.
	
[logz.io](https://logz.io)
[Statuscake](https://www.statuscake.com/)

# Oppgaver som er løst
Forutenom basis er følgende forsøkt levert på en tilfredstillende måte:
1. Applikasjonslogger
2. Overvåkning, varsling og Metrics

Oppgave nr.2 - Overvåkning, varsling og Metrics er jeg ikke veldig fornøyd med - men rammeverket er på plass.

# Kjente feil
I løpet av denne eksamen har jeg hatt store utfordringer med Spring-boot. 
Om man forsøker å kjøre enten applikasjonen eller testene lokalt, vil man merke at de feiler annenhver gang - konsekvent. 
Så om noe feiler når man kjører/tester lokalt, og man får stacktrace som sier noe om 'error in logback-configuration', 
prøv å kjør applikasjonen/testene pånytt med en gang - og vips så funker det igjen. Om dette er et problem med mitt lokale 
miljø (kanskje pga m2-cache eller noe) eller spring-boot oppsettet mitt har jeg ikke lykkes med å finne ut av, 
men ut fra hva jeg kan se så er ikke dette et problem for pipeline og heroku.

