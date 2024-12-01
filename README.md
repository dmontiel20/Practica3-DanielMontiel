# Practica3-DanielMontiel

Para empezar con la practica lo primero que he hecho es probar la pantalla LCD. Una vez visto como hacer las conexiones con la placa y conectar el potenciometro, he comenzado ha probar la salida de la pantalla con un simple contador. Una vez confirmado su funcionamiento he empezado ha probar el sensor de ultrasonidos. Tras ver su funcionamiento es necesario poder convertir la informacion que nos transmite a la que nosotros nos interesa. Este sensor nos da el tiempo que tarda un sonido en chocar con un objeto y volver. Por lo tanto es necesario saber la velocidad del sonido y una conversion a centimetros que es la unidad en la que trabajaremos. Me daba problemas porque el sensor a veces da valores demasiados elevados y se quedaban impresas en la pantalla las cifras que no se actualizaban en la siguiente distancia. Para que solo se muestre la nueva informacion necesito hacer un clear de la pantalla antes de imprimirla.

Lo siguiente es ver como hacer que funcione como un menu interactivo. He buscado formas de hacerlo con alguna biblioteca pero creo que es mas facil hacerlo con un simple array de los cafes.

Asique antes de empezar necesito crear la lista de cafes, para ello he implementado una clase Cafe con el nombre y su precio. Tambien con algunas funciones basicas para obtener el nombre y el precio. Para poder hacer que es una pantalla interactiva, esta tendra que ir actualizandose continuamente. Usare una variable como indice para ver en que cafe nos encontramos. Lo hare en la funcion "coffe_show()". Simplemente debera mostrar el cafe que indique en la linea 1 y el siguuiente(index + 1) en la linea 2. Pero hay un problema al no ser un array circular, por lo que debe tener un tope tanto iferior como superior, pero de esto me encargo mas adelante. Para que se pare en el ultimo cafe y siempre muestre dos cafes, he puesto una condicion para que si llega el indice al penultimo cafe, muestre simplemente los dos cafes.
Para probarlo conectare el joystick.

El joystick funciona con dos potenciometros que nos dicen la posicion con dos cordenadas, por ahora solo nececesito informacion sobre el eje Y. El primer problema que me surge es que es demasido sensible , por lo que tengo que usar condicionales para que se ignoren las coordenadas mas cercanas al centro. El segundo inconveniente es que si el joystick se mantiene en una posicion no para de incrementar la posicion del index, asique uso una variable que me dice si esta arriba o abajo, y si no pasa por el centro solo contara como un incremento o decremento. En el control del joystick tambien implemento el comportamiento del index. Tiene un tope tanto inferior como superior para que no se desborde. 

Empiezo con la funcion de arranque. Para hacer la intermitencia del led he usado un bucle, pero de esta forma hacia una espera de un segundo innecesaria asique lo apago y enciando 3 veces. Y a continuacion detecto si hay alguien cerca con la funcion "get_distancia()". El sensor de temperatura todavia no lo tengo conectado asique solo mostrara los cafes despues de detectar a alguien. 

Lo ultimo que me queda para la parte del cliente es la funcion que prepara los cafes. Creo un entero random y lo divido entre la potencia maxima que alcanzara el led para calcular el tiempo del delay en cada iteracion. Como el led a partir de cierta potencia no se nota el incremento de luz, con la funcion "map()" revalorizo la potencia para que como maximo llegue a 20. El led encargado de esto es necesario conectarlo a un pin con pwm.
Para activar esta funcion necesitare implementar el boton implementado en el joystick.

"get_pulse_joistick()" se encarga de detectar la pulsacion del boton del joystick. Se hace con una simple lectura, pero surge un problema muy comun, el rebote. Para evitar esto usaremos una variable que almacene la ultima posicion del boton leida, y por tanto solo nos avisara cuando se haya pulsado y la ultima informacion almacenada era de no estar pulsado. Con esto acabo la parte del cliente.

Para cambiar entre admin y cliente usare un boton. Aqui entra en accion el uso de las interrupciones, que nos evitara estar haciendo una espera activa.






