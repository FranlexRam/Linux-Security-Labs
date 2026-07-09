1 y 2. Servidor web, bloquear y permitir puerto 8080
Iniciar el servidor: En una terminal, ejecuta: php -S 127.0.0.1:8080. (Déjalo abierto ahí).

Bloquear: En otra terminal: sudo iptables -A INPUT -p tcp --dport 8080 -j DROP

Permitir: Primero, elimina el bloqueo: sudo iptables -D INPUT 1. Luego, acepta: sudo iptables -A INPUT -p tcp --dport 8080 -j ACCEPT.

3 y 4. Bloquear y permitir IP específica
Bloquear: sudo iptables -A INPUT -s 192.168.1.100 -j DROP

Permitir: sudo iptables -D INPUT -s 192.168.1.100 -j DROP (esto borra la regla de bloqueo). Luego: sudo iptables -A INPUT -s 192.168.1.100 -j ACCEPT.

5 y 6. Basado en protocolo (Ejemplo: ICMP/Ping)
Bloquear: sudo iptables -A INPUT -p icmp -j DROP

Permitir: sudo iptables -D INPUT -p icmp -j DROP (Borra la regla). Luego: sudo iptables -A INPUT -p icmp -j ACCEPT.


7 y 8. Crear y reenviar a una cadena
Crear cadena: sudo iptables -N MI_CADENA

Reenviar: sudo iptables -A INPUT -p tcp --dport 8080 -j MI_CADENA (Ahora, cualquier tráfico al 8080 será enviado a MI_CADENA para ver qué hacemos con él).

9 y 10. Eliminar y Listar
Listar: sudo iptables -L INPUT --line-numbers (Esto te da los números que necesitas para borrar).

Eliminar: sudo iptables -D INPUT [número] (Reemplaza [número] por el que viste en la lista).


<img width="770" height="871" alt="5-Permitir trafico de una IP especifica" src="https://github.com/user-attachments/assets/ad83c04f-fe75-4780-bd51-3e91c2151afb" />
<img width="770" height="871" alt="4-Bloquear trafico de una IP especifica" src="https://github.com/user-attachments/assets/b0511712-f4f1-463d-8b99-0ff19dbb466f" />
<img width="770" height="871" alt="3-Permitir trafico entrante" src="https://github.com/user-attachments/assets/df787995-6ac6-4b21-a722-5718fe07061d" />
<img width="770" height="871" alt="2-Bloquear trafico entrante" src="https://github.com/user-attachments/assets/25a5bbff-cda8-43df-8626-35657fb42ab9" />
<img width="739" height="352" alt="1-Listar reglas existentes" src="https://github.com/user-attachments/assets/d88ad8bb-6fe2-4531-8d6f-895682aa20bc" />
