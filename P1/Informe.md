# Práctica 1: Manejo de dispositivos de red
## Jaime Simeón Palomar Blumenthal - alu0101228587@ull.edu.es
## Jorge Ruiz Padilla - alu0101330037@ull.edu.es
##

### **Índice**

1. [Configuración básica del Router](#router)
2. [Configuración básica del Switch](#switch)


### **Configuración básica del Router** <a name="router">

En primer lugar, conectaremos el Router a la red eléctrica, mediante el cable de configuración al puerto USB trasero de nuestro PC, y con un cable de red RJ45 a nuestro puerto de red.

Luego, desde la terminal, accederemos a la consola del Router mediante `screen /dev/ttyUSB0 115200`. Nos pedirá usuario y contraseña (Usuario: "admin" sin contraseña).

```
MikroTik v6.39.2 (stable)
Login: admin
Password: 


  MMM      MMM       KKK                          TTTTTTTTTTT      KKK
  MMMM    MMMM       KKK                          TTTTTTTTTTT      KKK
  MMM MMMM MMM  III  KKK  KKK  RRRRRR     OOOOOO      TTT     III  KKK  KKK
  MMM  MM  MMM  III  KKKKK     RRR  RRR  OOO  OOO     TTT     III  KKKKK
  MMM      MMM  III  KKK KKK   RRRRRR    OOO  OOO     TTT     III  KKK KKK
  MMM      MMM  III  KKK  KKK  RRR  RRR   OOOOOO      TTT     III  KKK  KKK

  MikroTik RouterOS 6.39.2 (c) 1999-2017       http://www.mikrotik.com/

[?]             Gives the list of available commands
command [?]     Gives help on the command and list of arguments

[Tab]           Completes the command/word. If the input is ambiguous,
                a second [Tab] gives possible options

/               Move up to base level
..              Move up one level
/command        Use command at the base level
```

Tras iniciar sesión, nos mostrará los comandos básicos y nos dispondremos a verificar que hemos conectado bien el Router al PC con el puerto 10.

```
[admin@MikroTik] > ip route print
Flags: X - disabled, A - active, D - dynamic, C - connect, S - static, r - rip, b - bgp, o - ospf, m - mme, B - blackhole, U - unreachable, P - prohibit 
 #      DST-ADDRESS        PREF-SRC        GATEWAY            DISTANCE
 0 ADC  192.168.88.0/24    192.168.88.1    ether10                   0
[admin@MikroTik] > ip route          
[admin@MikroTik] /ip route> /ping 192.168.88.2
  SEQ HOST                                     SIZE TTL TIME  STATUS                                                                                                                                      
    0 192.168.88.2                               56  64 0ms  
    1 192.168.88.2                               56  64 0ms  
    2 192.168.88.2                               56  64 0ms  
    3 192.168.88.2                               56  64 0ms  
    4 192.168.88.2                               56  64 0ms  
    5 192.168.88.2                               56  64 0ms  
    6 192.168.88.2                               56  64 0ms  
    7 192.168.88.2                               56  64 0ms  
    8 192.168.88.2                               56  64 0ms  
    9 192.168.88.2                               56  64 0ms  
   10 192.168.88.2                               56  64 0ms  
   11 192.168.88.2                               56  64 0ms  
    sent=12 received=12 packet-loss=0% min-rtt=0ms avg-rtt=0ms max-rtt=0ms
```

En primer lugar, hemos impreso por pantalla todas las rutas, verificando que, en efecto, el puerto `eth10` tiene como IP la `192.168.88.1` y está conectado a la red `192.168.88.0/24`.

**NOTA:** _Previamente hemos configurado este puerto para que tenga la IP deseada, y para que se conectase a la red indicada. Además, hemos configurado la dirección IP del PC para que fuese 192.168.88.2._

Luego, simplemente hacemos un ping para verificar que el PC y el Router están conectados correctamente.

Finalmente, nos dispondremos a acceder por telnet a la consola del router, en lugar de hacer a través del cable de conexión ya que no es del todo fiable. Para ello, desde la terminal de Unix ejecutaremos `telnet 192.168.88.1`, siendo la dirección IP la del puerto al que estemos conectados.

Tras jugar un poco con los comandos, pasamos a trastear con la configuración del Switch.


### **Configuración básica del Switch** <a name="switch">

En primer lugar, conectaremos el Switch a la corriente y luego a nuestro PC mediante el cable de configuración.