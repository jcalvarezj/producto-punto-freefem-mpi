# Producto Punto en FreeFem++ con MPI
Proyecto de ejemplo para emplear cómputo paralelo o distribuido con MPI en FreeFem++. Se adjuntan [a.txt](a.txt) y [b.txt](b.txt) de ejemplo (generados por la script [generadorVector.edp](generadorVector.edp) para realizar el producto de a y b).

## Requisitos
FreeFem++ configurado con MPICH. Opcional, un clúster MPICH

## Ejecución
Se requiere primero generar dos archivos que contienen los vectores a multiplicar. Esto se hace ejecutando [generadorVector.edp](generadorVector.edp):

```
FreeFem++-nw generadorVector.edp <numero>

Tal que el tamaño de los vectores generados sea de 4*<numero>
Se puede añadir la opción -v 0 para no mostrar en consola el código ejecutado
```

Una vez generados los archivos [a.txt](a.txt) y [b.txt](b.txt), se procede a ejecutar alguno de los códigos para realizar la multiplicación. Por ejemplo, para ejecutar el caso serial, emplear:

```
FreeFem++-nw productoPuntoSerial.edp
```

O para el caso en paralelo en una sola máquina, con 4 procesos:

```
mpirun --np 4 FreeFem++-mpi productoPuntoSync.edp
```

O para un clúster, con 4 procesos, y archivo de hosts "machinefile" ubicado en ~:

```
mpirun --np 4 --hostfile ~/machinefile FreeFem++-mpi productoPuntoSync.edp
```

En caso de presentarse advertencia de OpenFabrics (openib), se puede añadir la opción

```
-mca btl ^openib
```
