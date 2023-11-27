# il subnetting

### il subnetting nasce perchè il numero di ip privati è finito, prendiamo per fare il subnetting il seguente indirizzo:
## 200.100.50.0

### per fare il subnetting prendi l'ultimo byte in binario

## 0 => 00000000

### mettiamo che l'azienda abbia bisogno di 8 sottoreti 
### 2^3 = 8 quindi abbiamo bisogno di 3 bit per fare 8 sottoreti
### in questo caso ogni rete può veicolare 2^5 -2 (il primo per la rete e l'ultimo per il broadcast) quindi 32 - 2 = 30


&nbsp;
&nbsp;

| decimale-binario     |     |     |     | 128         | 64          | 32          | 16           | 8            | 4            | 2            | 1            |            |
|----------------------|-----|-----|-----|-------------|-------------|-------------|--------------|--------------|--------------|--------------|--------------|------------|
| uso                  | net | net | net | net binario | net binario | net binario | host binario | host binario | host binario | host binario | host binario | bin to dec |
| rete (min)           | 200 | 100 | 50  | 0           | 0           | 0           | 0            | 0            | 0            | 0            | 0            | 0          |
| broadcast (max)      | 200 | 100 | 50  | 0           | 0           | 0           | 1            | 1            | 1            | 1            | 1            | 31         |
| rete possibile 2 min | 200 | 100 | 50  | 0           | 0           | 1           | 0            | 0            | 0            | 0            | 0            | 32         |
| rete possibile 2 max | 200 | 100 | 50  | 0           | 0           | 1           | 1            | 1            | 1            | 1            | 1            | 63         |
| rete possibile 3 min | 200 | 100 | 50  | 0           | 1           | 0           | 0            | 0            | 0            | 0            | 0            | 64         |
| rete possibile 3 max | 200 | 100 | 50  | 0           | 1           | 0           | 1            | 1            | 1            | 1            | 1            | 95         |
| rete possibile 4 min | 200 | 100 | 50  | 0           | 1           | 1           | 0            | 0            | 0            | 0            | 0            | 96         |
| rete possibile 4 max | 200 | 100 | 50  | 0           | 1           | 1           | 1            | 1            | 1            | 1            | 1            | 127        |
| rete possibile 5 min | 200 | 100 | 50  | 1           | 0           | 0           | 0            | 0            | 0            | 0            | 0            | 128        |
| rete possibile 5 max | 200 | 100 | 50  | 1           | 0           | 0           | 1            | 1            | 1            | 1            | 1            | 159        |
| rete possibile 6 min | 200 | 100 | 50  | 1           | 0           | 1           | 0            | 0            | 0            | 0            | 0            | 160        |
| rete possibile 6 max | 200 | 100 | 50  | 1           | 0           | 1           | 1            | 1            | 1            | 1            | 1            | 191        |
| rete possibile 7 min | 200 | 100 | 50  | 1           | 1           | 0           | 0            | 0            | 0            | 0            | 0            | 192        |
| rete possibile 7 max | 200 | 100 | 50  | 1           | 1           | 0           | 1            | 1            | 1            | 1            | 1            | 223        |
| rete possibile 8 min | 200 | 100 | 50  | 1           | 1           | 1           | 0            | 0            | 0            | 0            | 0            | 224        |
| rete possibile 8 max | 200 | 100 | 50  | 1           | 1           | 1           | 1            | 1            | 1            | 1            | 1            | 255        |


&nbsp;