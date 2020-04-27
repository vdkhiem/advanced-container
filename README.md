# How to run Advanced-Container
1.Download advanced artifact (E.g.Natasha.AdvancedLive.2020.2.0.3857.zip) and place in App folder.

2.Run start.ps1 with parameter -build_number (E.g. 2020.2.0.3857). Please run it in powershell.

Example: .\start.ps1 -build_number 2020.2.0.3857

# Reconnect Advanced containers (app, mysql) after restart windows 2019
   docker network create --driver nat advanced-net //re-create docker network
   docker network connect advanced-net advanced-app-container 
   docker network connect advanced-net advanced-mysql-container 
   docker start advanced-app-container
   docker start advanced-mysql-container

   docker container exec -it advanced-app-container powershell
   (Get-Content -path C:\advanced\web.config -Raw) -replace 'Server=172.22.254.154','Server=172.20.161.184'

# Volume host default location
C:\ProgramData\docker\volumes\