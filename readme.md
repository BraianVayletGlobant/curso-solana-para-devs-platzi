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

## Componentes de Solana

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

### Pipelining

Unidad de procesamiento de transacciones para la optimización de la validación.

Dentro de la red de Solana hay diferentes hardware que se tienen que encargar de un proceso en especifico

Ejemplo: Si tienes una fabrica que tienes muchos hardware que se encargan de construir un auto. Lo ideal es que todas vayan trabajando a la vez y no que a una le toque esperar que otra termine para empezar el trabjo que le toca hacer a ella

Este mismo proceso lo hace solana con un proceso que se llama canalización.

![canalizacion](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/canalizacion.png)

Todo el hardware disponible, kernel, cpu y gpu, es usado el 100% a través de la canalización, cada parte tiene una tarea en el pipeline de validación.

Este proceso se realiza de la siguiente manera, mientras el kernel realiza una captura de datos (fetch) este va a la GPU la cual se encarga de verificar y firmar esas transacciones (sign verify) y las envia a la CPU para que se almacenen (baking) y posteriormente se escriban en el kernel. Este proceso es continuo.

### Cloudbreak

Es una base de datos de escalado de cuentas horizontal. Algunas de sus predecesores usan **levelDb**.

**LevelDB** se utiliza como base de datos de backend para IndexedDB de Google Chrome y es uno de los backends compatibles con Riak. Además, Bitcoin Core y go-ethereum almacenan los metadatos de la cadena de bloques utilizando una base de datos LevelDB. Esta tiene un inconveniente y es que la base de datos no puede hacer uso de lecturas y escrituras simultaneas, por esta razón tiene un **máximo de 5000 TPS (transacciones por segundo)**

Los SSD modernos admiten 32 subprocesos simultáneos, por lo que pueden admitir 370000 lecturas por segundo aproximadamente 185mil tps sin embargo organizar la base de datos en cuentas de manera que sea posible lecturas y escrituras simultaneas entre estos 32 subprocesos es un desafío.

Hasta este punto en las blockchain tradicionales se ha generado un cuello de botella a pesar de que la GPU y la SSD tengan un mayor rendimiento la CPU no lo tiene.

![cuello](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/cuello.png)

Por esta razón Solana no hace uso de una base de datos tradicional para resolver el problema al contrario utiliza los siguientes procedimientos:

``` cmd
1. Archivos Mapeados en memoria
2. Utiliza operaciones secuenciales en vez de aleatorias
  a. El índice de cuentas y bifurcaciones se almacena en RAM
  b. Las cuentas se almacenan en archivos asignados en memoria de hasta 4MB de tamaño
  c. Cada mapa de memoria solo almacena cuentas de una única bifurcación propuesta
  d. Los mapas se destruyen aleatoriamente en tantos SSD como estén disponibles
  e. Se utiliza semántica de copy on writes
  f. Las escrituras se agregan a un mapa de memoria aleatorio para la misma bifurcación.
  g. El índice se actualiza después de que se completa cada escritura.
```

![randomSSD](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/randomSSD.png)

Todos estos procesos permiten que las actualizaciones de la cuenta se copien en la escritura y se agregen a un SSD aleatorio escalando tanto serialmente como horizontalmente

Otra de las optimizaciones que hace Solana es tener un **recolector de basura** que básicamente lo que hace es eliminar las bifurcaciones que llevan mucho tiempo atrasadas, Bifurcaciones que ya no tienen confirmaciones sobre sus transacciones.

En conclusión **solana no usa una base de datos**. Solana hace uso de las SSD disponibles en el sistema para poder registrar la información de dos maneras una es los archivos mapeados en memoria y la segunda es las operaciones secuenciales en vez de aleatorias.

### Archivers

**Archive**: es el almacenamiento del libro mayor distribuido.

Está basado en los conceptos de **FileCoin** y del **Proof of Replication**.

![PoRep1](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/PoRep1.png)

Solana lo que hace es enviar la información a muchos nodos de la red, y para evitar problemas con que la información se pierda hay un verificador que cada cierto tiempo hace que estos nodos envíen pruebas de que si tienen almacenada la información por medio de criptografía.

![PoRep2](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/PoRep2.png)

Los clientes firman un hash de PoH en un periodo regular La firma es utilizada como fuente de aleatoriedad para elegir una porción especifica del libro mayor La firma se emplea para crear una clave CBC simétrica y el cliente codifica la porción del libro mayor con la clave

Solana utiliza este Poreps debido a que si se utiliza Solana en su capacidad máxima podría llegar a producir hasta 4 Petabytes de información al año si esto se almacenara en nodos serian muy pocos los nodos que podrían almacenar toda esta información por lo tanto la red seria mas centralizada.

### Accounts

![accounts](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/accounts.png)

- Una cuenta se puede marcar como sólo lectura para que sea mucho más rápido su acceso.
- Una cuenta ejecutable debe ser marcada para tal fin. ¡No se te olvide!
- Al desplegar un programa, las cuentas que este genera serán de su propiedad, y es el único que puede accederlas y mofidicarlas.
- Las cuentas pagan alquiler por el uso del sistema. Se puede pagar por adelantado o dejar cierto monto en la cuenta y que se descuente más a mes.

## Interaccion con la red

### Clusters

![accounts](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/accounts.png)

Clusters disponibles para la comunidad:

- **Devnet**: espacio para desarrollar, jugar y apredender, y se pueden solicitar ‘airdrops’ gratuitos y poder interactuar con la red.
- **Testnet**: aunque es gratuito, se considera un ambiente de staging, con programas un poco más estable, antes de pasarlos a la red principal.
- **Mainnet beta**: red de producción.

Al crear una cuenta, ésta está disponible en todas las redes, y tengo que tener cuidado de seleccionar la red mientras estoy trabajando.

### Clientes

![clients](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/clients.png)

Para interactuar con la red de Solana existen estos medios o clientes:

- Llamadas [JSON RPC API](https://docs.solana.com/developing/clients/jsonrpc-api) contra un nodo de Solana.
- Librería [Solana-Web3.js](https://docs.solana.com/developing/clients/javascript-api) que cuenta con toda la lógica en JavaScript para interactuar con los nodos, similar al web3.js de Ethereum.
- Librerías **Rust API**, crates de Rust para interactuar con los nodos.
  - [Solana-program](https://docs.rs/solana-program/latest/solana_program/)
  - [Solana-SDK](https://docs.rs/solana-sdk/latest/solana_sdk/)
  - [Solana-client](https://docs.rs/solana-client/latest/solana_client/)
  - [Solana-clap-utils](https://docs.rs/solana-clap-utils/latest/solana_clap_utils/)

### Flujo de trabajo de desarrollo

![flujo](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/flujo.png)

![flujo2](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/flujo2.png)
