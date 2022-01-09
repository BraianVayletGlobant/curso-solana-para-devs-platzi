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

La blockchain de **Ethereum** utiliza una mecanismo de consenso que se llama **proof of stake (PoS)** Este es un mecanismo no se utiliza un programa para ejecutar las transacciones que tiene tanta carga computacional ya que proof of stake es más determinista que probabilístico. Y esto significa que la red es la que escoge cuáles son los nodos que van a validar las transacciones de acuerdo a la participación en monedas que tenga cada uno de estos nodos. Esta red utiliza algo que se llama Casper y es que en caso de que algún nodo quiera ir en contra de la red pierde todas las monedas.

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

