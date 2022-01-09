# Solana para developers

## [whitepaper](https://solana.com/solana-whitepaper.pdf)

## [Web](https://solana.com/es)

Creador de Solana: **Anatoly Yakovenko** (trabajo en dropbox y qualcomm)

En este momento Solana es la **blockchain mas rapida del mercado** por que tiene **50000 transacciones por segundo** y depende del hardware utilizado podríamos hablar hasta de 150 mil tps

La red de solana principal cuenta con **200 Nodos** y produce **un bloque cada 4 segundos**

### Problema del Trilema 

![trilema](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/trilema.png)

**Vitalik** dice que **solo se pueden tener dos de esas tres cosas por que tenemos muchas limitaciones por el hardware por la seguridad**

### Proof of Work (PoW)

La blockchain de **bitcoin** utiliza un mecanismo de consenso que se llama **proof of work (PoW)** Este mecanismo le permite tener una muy buena seguridad debido a su alta descentralización sin embargo la escalabilidad no es buena debido a que las transacciones de bitcoin son muy lentas.

![PoW](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/PoW.png)

> Resumen PoW:
>
> - 👍 Seguridad
> - 👍 Descentralización
> - 👎 Escalabilidad

### Proof of Stake (PoS)

La blockchain de **Ethereum** utiliza una mecanismo de consenso que se llama **proof of stake (PoS)** Este es un mecanismo no se utiliza un programa para ejecutar las transacciones que tiene tanta carga computacional ya que el proof of stake es más determinista que probabilístico. Y esto significa que la red es la que escoge cuáles son los nodos que van a validar las transacciones de acuerdo a la participación en monedas que tenga cada uno de estos nodos. Esta red utiliza algo que se llama Casper y es que en caso de que algún nodo quiera ir en contra de la red pierde todas las monedas.

![PoS](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/PoS.png)

> Resumen PoS con Casper:
>
> - 👍 Seguridad
> - 👎 Descentralización
> - 👍 Escalabilidad

### Proof of History (PoH)

Para estos problemas aparece **solana** con una **variación de Proof of stake** que le pusieron el nombre de **proof of history** Esto soluciona un problema de sincronización de la red con el fin de hacerla mucho más rápida.

Proof of history es una solución de sincronización dentro de la red.
PoH es una función de retardo verificable implementada como una función hash secuencial. [link](https://es.wikipedia.org/wiki/Proof_of_History)

En resumen, la solución que trae Solana con el PoH es una sincronización a los retardos de la red.

![PoH](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/PoH.png)

> Resumen PoH:
>
> - 👍 Seguridad
> - 👍 Descentralización
> - 👍 Escalabilidad

### Tower BFT

Solana usa:

![PoS-TDMA](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/PoS-TDMA.png)

- Proof of stake como método de consenso.
- Se sincroniza la información por medio de TDMA, el ancho de banda de la blockchain es dividido entre los participantes.
- Un nodo tiene la capacidad de calcular el estado de toda la red.
- Un nodo

### Turbine

Turbine es el formato de comunicación solana.

Consta de contar la nueva info a tus vecinos, y estos vecinos a sus vecinos.

Se evitan los ataques de eclipse, se envía información cifrada sobre cuál es el siguiente vecindario y evita prever cuál será el siguiente paso. Sólo tomando toda la red se podría modificar los datos.

El líder divide el bloque en paquetes de hasta 64 kb de tamaño. Para un bloque de 12 mb, el líder produce 2000 paquetes de 64 kb y transmite cada paquete a un validador diferente.

![turbine1](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/turbine1.png)
![turbine2](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/turbine2.png)
![turbine3](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/turbine3.png)

Si cada vecindario está compuesto por 200 nodos, una red de 3 niveles, comenzando con un solo líder en la raíz, puede llegar a 40000 validadores en 2 saltos.

O aproximadamente 200 milisegundos asumiendo que cada enlace de red es de 100 ms en promedio.

### Gulf Stream

**Mempool (bytes):** Tamaño agregado en bytes de las transacciones que esperan ser confirmadas. Depende de la oferta y demanda del bloque que estén conectados transaccionado en ese momento. Los validadores de **Solana** pueden gestionar un tamaño de mempool de 100k. O sea que con un rendimiento de red de 50k TPS (transacciones por segundo), se ejecuta un mempool de 100k transacciones en cuestión de segundos.

Como se ve una transacción en Solana:

![tensol](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/TTL.png)

**Gossip protocol:** Basado en un concepto muy básico para distribuir y propagar información a través de una red. En este protocolo, para que un nodo distribuya una información, sólo debe emparejarse con otros nodos de forma aleatoria. Una vez ocurre esto sólo debe intercambiar la información recibida con dichos nodos, quienes a su vez distribuirán la información con otros nodos a los que también están emparejados. Formando una cadena de distribución para propagar la información por toda la red de forma oportuna y eficaz.

**Gulf Stream:** Es un protocolo de almacenamiento en caché de las transacciones de la red. Es el encargado de recibir la transacción y mandarla a todos los nodos, priorizando a los nodos generadores. Permite a todos los nodos de la red acceder a la información necesaria para la recreación de los bloques, lo que ayuda a los validadores a confirmar las transacciones antes de que se finalice el siguiente bloque, reduciendo los tiempos de confirmación y permite un volumen de transacciones sustancial.

### Sealevel

**SeaLevel** Es el procesamiento en paralelo de decenas de miles de contratos inteligentes que se pueden ejecutar en paralelo al mismo tiempo usando las GPU de contratos inteligentes.

![evm](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/evm.png)

en la **EVM de Ethereum** Por ejemplo, estos runtime ejecutan un solo subproceso que solo puede modificar un estado a la vez. En cambio en **Solana** Se pueden ejecutar muchos de estos procesos al mismo tiempo en background.

**Programas y Cuentas**:

- En solana todos los programas son cuentas
- Tanto los programas como las información asociada a ellos están registrados en cuentas.
- Cuando se despliega un programa en solana se obtiene un PublicKey de ese programa y para registrar información esta se registra en cuentas, estas cuentas son propiedad del programa asociado.
- Todas las cuentas poseen una PublicKey, un saldo, datos y un propietario.

![programas-cuentas](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/programas-cuentas.png)

- Los programas solo pueden cambiar los datos de las cuentas que poseen y solo pueden debitar cuentas de su propiedad.
- Cualquier programa puede leer y acreditar en cualquier cuenta.
- La cesión de la propiedad de una cuenta sólo puede ocurrir una vez en la vida de la cuenta.
- Metaplex: Protocol and application framework for decentralized NFT minting, storefronts, and sales. (github)
- **System programs**: De forma predeterminada, todas las cuentas inician como propiedad del system program.
  - Es el único programa que puede asignar la propiedad de la cuenta.
  - Único programa que puede asignar datos inicializados en cero.
- **Carga de programas customizados**:

![carga-custom](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/carga-custom.png)

- **Transacciones**: Transacciones -> Programa -> Instrucciones del programa -> cuentas.

![transacciones](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/transacciones.png)

-> Funcionamiento en tiempo de ejecución: El **cliente (dApp)** se comunica con el programa por medio de un proceso de **serialización** donde Solana y los contratos **des-serializan** esa información para ejecutar las transacciones del programa.

![tiempo-ejecucion](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/ejecucion.png)

-> Solana hace uso de la **arquitectura CUDA** la cual se basa en una matriz escalable de multiprocesadores de transmisión multiproceso (hardware).