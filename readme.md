# Solana para developers

## [whitepaper](https://solana.com/solana-whitepaper.pdf)

### Clase 2

Creador de Solana: **Anatoly Yakovenko** (trabajo en dropbox y qualcomm)

En este momento Solana es la **blockchain mas rapida del mercado** por que tiene **50000 transacciones por segundo** y depende del hardware utilizado podríamos hablar hasta de 150mil tps

La red de solana principal cuenta con **200 Nodos** y produce **un bloque cada 4 segundos**

#### Problema del Trilema (triangulo escalabilidad, seguridad y descentralizacion)

                ESCALABILIDAD
      SEGURIDAD               DESCENTRALIZACION

**Vitalik** dice que **solo se pueden tener dos de esas tres cosas por que tenemos muchas limitaciones por el hardware por la seguridad**

La blockhain de **bitcoin** utiliza un mecanismo de consenso que se llama **proof of work (PoW)** este mecanismo le permite tener una muy buena seguridad debido a su alta descentralización sin embargo la escalabilidad no es buena debido a que las transacciones de bitcoin son muy lentas.

![PoW](https://raw.githubusercontent.com/BraianVaylet/curso-solana-para-devs-platzi/main/assets/PoW.png)

> Resumen PoW:
>
> - 👍 Seguridad
> - 👍 Descentralizacion
> - 👎 Escalabilidad

La blockchain de **Ethereum** utiliza una mecanismo de consenso que se llama **proof of stake (PoS)** este es un mecanismo no se utiliza un programa para ejecutar las transacciones que tiene tanta carga computacional ya que proof of stake es mas determinístico que probabilístico. Y esto significa que la red es la que escoge cuales son los nodos que van a validar las transacciones de acuerdo a la participación en monedas que tenga cada uno de estos nodos. Esta red utiliza algo que se llama Casper y es que en caso de que algún nodo quiera ir en contra de la red pierde todas las monedas.

> Resumen PoS con Casper:
>
> - 👍 Seguridad
> - 👎 Descentralizacion
> - 👍 Escalabilidad

Para estos problemas aparece solana con una variación de Proof of stake que le pusieron el nombre de proof of history este soluciona un problema de sincronización de la red con el fin de hacerla mucho mas rápida. 
