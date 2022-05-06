# Marvel-United-Json-Database
## english

This repository contains JSON files that can be used to generate a United games (like Marvel United and Marvel United X-Men from CMON and Spinmaster Games) apps, webs or databases.

The files are sorted by language into folders.

Check [STATUS.md](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/STATUS.md#en) to know more about current state of the files and get the direct links to the json files.

## español

Este repositorio contiene archivos JSON que pueden usarse para crear aplicaciones, webs o bases de datos relacionadas con los juegos United de CMON y Spinmaster Games como Marvel United y Marvel United X-Men.

Los archivos están ordenador en carpetas por idiomas.

Revisa [STATUS.md](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/STATUS.md#es) para conocer el estado actual de cada archivo y obtener los enlaces directos a los json.

Este README se actualizará con explicaciones sobre la estructura de los archivos para que cualquiera pueda editarlos, copiarlos y crear sus propias versiones. Si quieres colaborar contacta conmigo.

### Estructura del archivo json

Los archivos están planteados como cajas. A partir de ahora se entiende que cuando hablamos de un json nos referimos a una caja y viceversa. Cada caja / json contiene una serie de componentes. Todos los datos de la caja son opcionales excepto el boxId. A continuación se detallan todos los campos disponibles con su tipo y posibles usos:


#### Caja

- boxId: String. Identificador único de la caja (por ejemplo podríamos usar MUN001 como identificador de la caja equivalente al juego base)
- baseUrl: String opcional. Si se especifíca, se concatenará "baseUrl" antes de cada "img".
- img: String opcional. Ruta en la que se aloja una imagen. Puede ser la ruta absoluta o relativa a "baseUrl".
- name: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional.
- rulebook: String opcional. Ruta en la que se aloja un documento pdf. Puede ser la ruta absoluta o relativa a "baseUrl".
- tokens: Array\<String\> opcional. Lista de URLs a las imágenes de los tokens incluidos en esta caja (actualmente sin uso conocido).
- locations: Array\<Location\> opcional. Lista de Lugares. [Ver documentación de "Location"](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#Location).
- challenges: Array\<Challenge\> opcional. Lista de Desafíos. [Ver documentación de "Challenge"](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#Challenge).
- cards: Array\<Card\> opcional. Lista de Cartas. [Ver documentación de "Card"](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#Card).
- characters: Array\<Character\> opcional. Lista de Personajes. [Ver documentación de "Character"](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#Character).
- faq: Array\<Faq\> opcional. Lista de Preguntas. [Ver documentación de "Faq"](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#Faq).
- trophies: Array\<Trophie\> opcional. Lista de Logros. [Ver documentación de "Trophie"](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#Trophie).

#### LocalizedText

- Texto que admite dos valores. Ideado para contener el texto original en inglés y su traducción.

#### Location

- img: String opcional. Ruta en la que se aloja una imagen. Puede ser la ruta absoluta o relativa a "baseUrl".
- title: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. El título o nombre del Lugar.
- endOfTurn: [EndOfTurn](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#EndOfTurn) opcional.
- slots. Array\<String\> opcional. Indica el número de huecos que tiene el Lugar y su tipo para la preparación inicial. Valores posibles actualmente: "C", "T", "D", "empty"

#### EndOfTurn

- mandatory: Bool opcional. Indica si el efecto de fin de turno del Lugar es obligatorio (fondo oscuro) o no.
- effect: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Descripción del efecto.

#### Challenge

- img: String opcional. Ruta en la que se aloja una imagen. Puede ser la ruta absoluta o relativa a "baseUrl".
- title: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Nombre del Desafío
- description: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Texto de la carta explicativa del Desafío.
- cards: Array\<Card\> opcional. Lista de Cartas. [Ver documentación de "Card"](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#Card). Ideado para contener las cartas asociadas a un desafío (por ejemplo las cartas de misión alternativas para el desafío Plan B).

#### Card

- cardType: String opcional. Valores posibles actualmente: "hero", "plan", "threat", "challenge", "gem", "other"
- img: String opcional. Ruta en la que se aloja una imagen. Puede ser la ruta absoluta o relativa a "baseUrl".
- title: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Título / cabecera de la carta (por ejemplo en las cartas de Héroe o de Plan Maestro el nombre del personaje, en las cartas de Amenaza el nombre de la Amenaza, etc.).
- description": [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Descripción del efecto de la carta (pensado para cartas que no tienen efecto especial como las amenazas, desafíos, etc.).
- specialEffect": [SpecialEffect](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#SpecialEffect) opcional.
- movement: Int opcional. Indica el número de Lugares que mueve el Villano en una carta de Plan Maestro. El signo positivo indica movimiento en el sentido de las agujas del reloj. Los valores negativos indican movimiento en sentido contrario a las agujas del reloj.
- movementText: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Texto de movimiento en una carta de Plan Maestro (como las cartas de Rhino o Loki que indican un texto en lugar de un número de Lugares).
- bam: Bool opcional. Indica si la carta de Plan Maestro o de Amenaza tiene BAM!
- actions: Array\<String\> opcional. Indica las acciones de una carta de Héroe (solo las acciones normales, no lo símbolos asociados a un efecto especial) o las fichas necesarias para eliminar una Amenaza. Valores posibles actualmente: "A", "H", "M", "W".
- add: [Add](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#Add) opcional.
- lifePoints: [LifePoints](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LifePoints) opcional.
- locationEffect": Bool opcional. Indica si una carta (normalmente una Amenaza) tiene el icono de Efecto de Lugar, indicando que ese efecto se activa cuando el Villano termina su turno en ese Lugar.
- startingHand: Bool opcional. Indica si una carta debe colocarse en la parte superior del mazo porque es parte de la mano inicial.
- bottomDeck: Bool opcional. Indica si una carta debe colocarse en la parte inferior del mazo porque debe robarse al final del mazo.

#### SpecialEffect

- mandatory: Bool opcional. Indica si el Efecto Especial de la carta es obligatorio (fondo oscuro).
- title: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Nombre del Efecto Especial.
- description: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Descripción del Efecto Especial.

#### Add

- left: Array\<String\> opcional. Indica el número y tipo de fichas que una carta de Plan Maestro añade a un Lugar. Valores posibles actualmente: "C", "T".
- center: Array\<String\> opcional. Indica el número y tipo de fichas que una carta de Plan Maestro añade a un Lugar. Valores posibles actualmente: "C", "T".
- right: Array\<String\> opcional. Indica el número y tipo de fichas que una carta de Plan Maestro añade a un Lugar. Valores posibles actualmente: "C", "T".

#### LifePoints

- twoHeroes: Int opcional. Indica los puntos de vida de una Carta o Villano. Normalmente las Amenazas tienen los mismos puntos sin tener en cuenta el número de jugadores.
- threeHeroes: Int opcional. Indica los puntos de vida de una Carta o Villano. Normalmente las Amenazas tienen los mismos puntos sin tener en cuenta el número de jugadores.
- fourHeroes: Int opcional. Indica los puntos de vida de una Carta o Villano. Normalmente las Amenazas tienen los mismos puntos sin tener en cuenta el número de jugadores.

#### Character

- img: String opcional. Ruta en la que se aloja una imagen. Puede ser la ruta absoluta o relativa a "baseUrl".
- loyalty: String opcional. Indica el tipo de personaje. Valores posibles actualmente: "hero", "villain", "anti-hero".
- name: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Nombre del personaje.
- realName: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Nombre real del personaje.
- bio: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Texto descriptivo del personaje.
- cards: Array\<Card\> opcional. Lista de Cartas. [Ver documentación de "Card"](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#Card).
- dashboard: [Dashboard](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#Dashboard) opcional.
- tokens: Array\<String\> opcional. Lista de URLs a las imágenes de los tokens específicos de este personaje (actualmente sin uso conocido).

#### Dashboard

- back: [Back](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#Back) opcional.
- front: [Front](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#Front) opcional.

#### Back

- img: String opcional. Ruta en la que se aloja una imagen. Puede ser la ruta absoluta o relativa a "baseUrl".
- specialSetup: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Texto que explica si este Villano requiere alguna preparación especial.
- superVillain: Array\<String\> opcional. Lista que indica las fichas que se entregan en el modo Súper Villano. Valores posibles actualmente: "A", "H", "M", "W".
- superVillainText: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Texto que explica si se debe aplicar alguna regla especial en el modo Súper Villano.

#### Front

- img: String opcional. Ruta en la que se aloja una imagen. Puede ser la ruta absoluta o relativa a "baseUrl".
- specialRules: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Texto que explica las reglas especiales del Villano.
- overflow: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Texto que explica el efecto de Exceso del Villano.
- bam: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Texto que explica el efecto BAM! del Villano.
- plot: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Texto que explica el Complot Maligno del Villano. 
- lifePoints: [LifePoints](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LifePoints) opcional. Puntos de vida del Villano.

#### Faq

- question: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Texto de la pregunta.
- answer: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Texto de la respuesta.

#### Trophie

- id: String. Identificador único del Logro / Trofeo, necesario para que funcione la persistencia en las aplicaciones móviles.
- category: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Categoría a la que se asocia el Trofeo (para poder filtrar los Logros / Trofeos por tipo).
- description: [LocalizedText](https://github.com/OscarGarPer/Marvel-United-Json-Database/blob/main/README.md#LocalizedText) opcional. Descrición o condición para obtener el Logro / Trofeo.
- completed: Bool opcional. Indica si el Logro / Trofeo se ha completado o no (pensado para el usuario final).
