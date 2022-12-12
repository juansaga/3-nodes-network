Prerequisitos:
    -node js
    - docker
    - wsl (windows subsistem for linux), en el siguiente link se puede ver como se instala: https://learn.microsoft.com/en-us/windows/wsl/install

Ejecutar el comando en la terminal wsl, desde la carpeta donde se ha descargado el proyecto:
    ./loadFabric.sh

Ejecutar el siguiente comando para ir a la carpeta de la red:
    cd pharma-ledger-network

Ejecutar el siguiente comando para levantar la red (docker desktop debe estar abierto):
    ./net-pln.sh up

Ejecutar el siguiente comando para crear el canal de la red:
    ./net-pln.sh createChannel

Ejecutar los siguientes comandos para la configuración del contrato inteligente:
    cd organizations/manufacturer/contract 
    npm install

    cd ../application
    npm install

    cd ../../pharmacy/contract
    npm install

    cd ../application
    npm install

    cd ../../wholesaler/contract
    npm install

    cd ../application
    npm install

Ejecutar el siguiente comando para desplegar el contrato:
    cd ../../..
    ./net-pln.sh deploySmartContract

Abrir 3 terminales extra y ejecutar en cada una lo siguiente:
    cd organizations/manufacturer/application
    node app.js

    cd organizations/pharmacy/application
    node app.js

    cd organizations/wholesaler/application
    node app.js

Ahora puede ir a los puertos 3000, 3001 y 3002. Cada uno es un nodo de la red.

Para hacer transacciones en la pestaña a la izquierda de cada página hay una opción que dice "add user to wallet" allí registre primero el usuario (puede ser su nombre).

Ahora puede comensar a realizar transacciones en la red blockchain y consultarlas.