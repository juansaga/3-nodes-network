Prerequisitos:

    - node js

    - npm

    - docker desktop

    - wsl2 (windows subsistem for linux), en el siguiente link se puede ver como se instala: 

    
        https://learn.microsoft.com/en-us/windows/wsl/install

        Cuando escoja la distribución seleccione la mas alta de Ubuntu: Ubuntu-20.04

    Debe configurar Docker Desktop con wsl2:
        
        Entrar a settings, luego click en resources, wsl integration, selecciona la opción Enable integration with my default WSL distro y activa la distribución wsl que escogió cuando instaló wsl, reinicia docker desktop y listo.


Ejecutar el comando en la terminal wsl, desde la carpeta donde se ha descargado el proyecto:


    chmod +x loadFabric.sh


    sudo ./loadFabric.sh


    cd pharma-ledger-network/scripts

    sed -i -e 's/\r$//' createChannel.sh

    sed -i -e 's/\r$//' deploySmartContract.sh

    sed -i -e 's/\r$//' invokeContract.sh

    sed -i -e 's/\r$//' utils.sh

    cd ..

    export PATH=${PWD}/../bin:$PATH

    export FABRIC_CFG_PATH=$PWD/../config/

    sed -i -e 's/\r$//' net-pln.sh
     
    Antes de ejecutar el siguiente comando debe tener abierto Docker Desktop

    sudo ./net-pln.sh up

    sudo ./net-pln.sh createChannel

    cd organizations/manufacturer/contract 

    Abra una nueva terminal (Para esta no utilice wsl)

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

    cd ../../..

    Retornar a la terminal wsl

    sudo ./net-pln.sh deploySmartContract

Abrir 3 terminales extra (que no sean wsl) y ejecutar en cada una lo siguiente:


    cd organizations/manufacturer/application
    node app.js

    cd organizations/pharmacy/application
    node app.js

    cd organizations/wholesaler/application
    node app.js

Ahora puede ir a los puertos 30000, 30001 y 30002. Cada uno es un nodo de la red.

Para hacer transacciones en la pestaña a la izquierda de cada página hay una opción que dice "add user to wallet" allí registre primero el usuario (puede ser su nombre).

Ahora puede comenzar a realizar transacciones en la red blockchain y consultarlas.