# Code Assist Notation

## Notación de asistencia en código

**(CAN)** es un conjunto de instrucciones diseñadas para facilitar la asistencia de agentes de IA en la escritura y modificación de código.
Estas instrucciones se expresan como **comentarios embebidos** en el código a intervenir o en archivos de configuración específicos.
Pueden ser introducidas tanto por el usuario como por el propio agente de IA.

---

# Reglas

## Políticas de aplicación

* Los comandos son interpretados como **sugerencias**, excepto los comandos de ejecución `INSERT`, que requieren explícitamente la creación o reescritura de código por parte de la IA.

## Comportamiento de la IA

* Cada vez que la IA genere bloques de código, debe marcar la **autoría** con un comando de autoría.
* Los bloques agregados deben identificarse con el permiso `[X]`.

## Scope de comandos

* Los comandos afectan únicamente a las declaraciones dentro del **contexto en que se aplican**.
* `>>` indica que el comando aplica al **bloque siguiente**.
* `**` indica que aplica a **todo el contenido del contexto actual**.

**Ejemplo:**

```js
// [+]
function hello() {
  function handshake() {
    ...
  }
}

function bye() {
  ...
}
```

En este caso, `[+]` afecta a `hello` y a `handshake`, pero no a `bye`.

## Herencia

* No existe herencia de permisos.
* El último comando definido en un mismo nivel **sobrescribe** cualquier otro comando previo del mismo tipo.

## Reglas por defecto

* El contexto general de un archivo tiene, por defecto, un permiso global equivalente a `[X]*`.

---

# Comandos de permiso

## Alcance

* A nivel documento, el permiso se establece con:

```js
// @Document: [++]
```

Este debe ser el **primer permiso declarado** en el archivo.

* Para excepciones en una clase o función, debe colocarse el permiso inmediatamente antes de su declaración.

## Flags de Refactorización

### NO ESTABLE

Todo puede modificarse.

```js
// [X]
```

### ESTABLE Y REFACTORIZABLE (externo)

* Clases y funciones no deben eliminarse.
* Los nombres, argumentos y salidas de funciones globales no deben modificarse.
* Los nombres de clases no deben modificarse.
* Dentro de clases, funciones y propiedades **sí pueden modificarse**.
* Se permite crear nuevas funciones y clases.

```js
// [+]
```

### ESTABLE Y REFACTORIZABLE (interno)

* Clases y funciones no deben eliminarse.
* Los nombres, argumentos y salidas de funciones globales no deben modificarse.
* Los nombres de clases no deben modificarse.
* Los nombres, argumentos, salidas y propiedades internas **tampoco deben modificarse**.
* Se permite crear nuevas funciones y clases.

```js
// [++]
```

### ESTABLE, NO REFACTORIZABLE

* Clases y funciones no deben eliminarse.
* Nombres, argumentos y salidas no deben modificarse.
* Propiedades internas no deben modificarse.
* No está permitido agregar nuevas funciones ni clases.

```js
// [+++]
```

### COMPLETAMENTE INMUTABLE

* Las declaraciones son estables y no deben modificarse bajo ninguna circunstancia.
* Ni los nombres ni el contenido de funciones y clases pueden alterarse.

```js
// [@Inmutable]
```

## Flag de confirmación

Cualquier flag puede combinarse con `?` para requerir confirmación antes de aplicar cambios.

```js
// [+] [?]
```

---

# Comandos de foco

Definen explícitamente dónde debe trabajar la IA.

```js
// [FOCUS]
// [DEPRECATED]
```

---

# Comandos de autoría

Indican quién generó un bloque de código.

```js
// @IA.AgentName >>
// @IA >>
// @UserName >>
```

---

# Comandos de ejecución

### Inserción en línea

```js
// >> Reemplazar este comentario con código.
```

### Inserción en contexto

```js
// >> !! Autorizado a reescribir todo el contexto
```

### Sugerencia en línea

```js
// > Sugerencia para reemplazar esta línea por código.
```

### Sugerencia en contexto

```js
// > !! Sugerencia para reemplazar el contexto completo
```

---

# Comandos de contexto

Comentarios especializados para guiar a la IA o al usuario.

```js
// @IA.OptionalAgentName: Comentario de IA
// @IA: !! Comentario prioritario
// @IA: ?? Comentario que requiere decisión del usuario
// @IA: @TODO: Sugerencia de implementación futura
// Comentario sin flags → contexto humano
// @USER.UserName: Comentario explícito del usuario
// @TODO: Pendientes a resolver
```

---

# Comandos de bloque

Delimitan un bloque lógico de código.

```js
// {BlockName} >>
...
// << {BlockName}
```

---

# Comandos de ancla

Permiten marcar puntos clave de referencia.

```js
// #PointID
```
