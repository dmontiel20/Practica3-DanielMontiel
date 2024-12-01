# Practica3-DanielMontiel

Para empezar con la practica lo primero que he hecho es probar la pantalla LCD. Una vez visto como hacer las conexiones con la placa y conectar el potenciometro, he comenzado ha probar la salida de la pantalla con un simple contador. Una vez confirmado su funcionamiento he empezado ha probar el sensor de ultrasonidos. Tras ver su funcionamiento es necesario poder convertir la informacion que nos transmite a la que nosotros nos interesa. Este sensor nos da el tiempo que tarda un sonido en chocar con un objeto y volver. Por lo tanto es necesario saber la velocidad del sonido y una conversion a centimetros que es la unidad en la que trabajaremos.


Lo siguiente es ver como hacer que funcione como un menu interactivo. He buscado formas de hacerlo con alguna biblioteca pero creo que es mas facil hacerlo con un simple array de los cafes.

Asique antes de empezar necesito crear la lista de cafes, para ello he implementado una clase Cafe con el nombre y su precio. Tambien con algunas funciones basicas para obtener el nombre y el precio
