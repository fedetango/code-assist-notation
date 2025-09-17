# Code Assist Notation
# Notación de asistencia en código

**(CAN)** es una serie de instrucciones pensadas para facilitar la asistencia de agentes IA en código.Estás instrucciones son colocadas en forma de comentarios en el código a intervenir o en archivos de configuración especiales.Las instrucciones pueden ser colocadas por el usuario o por el agente de IA.

# Reglas

## Políticas de aplicación
- Los comandos son sugerencias a excepción de los comandos de ejecución INSERT que solicitan explicitamente a la IA que cree código.
- Cuando la IA agrega bloques debe definir la autoría con un comando de autoría.

## Scope de comandos
- Los comandos afectan a las declaraciones en derminado contexto.
- `>>` Quiere decir "el siguiente bloque".
- `**` Quiere decir "todo lo presente en el contexto actual".
- Cuando afecta a una función 

El `[+]` afecta a la función de `hello` y `handshake`.

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

## Jerarquía
- Gana el último comando establecido

## Reglas por defecto
- Por defecto el contexto general tiene los siguientes permisos implícitos:


# Comandos de bloque

## Comandos de autoría 

Indica quien escribió el bloque de código.
```js
// @IA.AgentName >>
```

```js
// @IA >>
```

```js
// @UserName >>
```

## Comandos de permiso 

NO ESTABLE
Todas las funciones, clases y contenidos establecidos en el contexto pueden eliminarse.
```js
// [X]
```

ESTABLE Y REFACTORIZABLE
Las declaraciones afectadas son estables. 
Los nombres de las declaraciones DEBEN permanecer igual y las funciones DEBEN respetar los INPUT y OUPUT.
El contenido de las funciones PUEDE modificarse.
PUEDEN crearse nuevas funciones para refactorizar.
```js
// [+]
```

ESTABLE, FIJO Y NO REFACTORIZABLE
Las declaraciones afectadas son estables y NO DEBEN modificarse.
Tanto los nombres de las declaraciones como el contenido de las funciones y clases NO DEBEN modificarse.
```js
// [+++]
```

### Flag de confirmación

```js
// [+] [?] → Requiere confirmación antes de ejecutar.
// Puede utilizarse en combinación de cualquier flag de permiso
```


##  Comandos de foco
Indica a la IA donde trabajar
```js
// [FOCUS]
```

```js
// [DECREPTED]
```



# Comandos en línea

## Comandos de ejecución 

LOCAL INSERT
```js
// >> Reemplaza este comentario por código.
```

CONTEXT INSERT
```js
// >> !! Autorizado a reescribir todo el contexto
```

Sugerencia
```js
// * Sugerencia de contenido.
```

## Comandos de contexto 

```js
// @IA: Comentarios de IA
```

```js
// @IA: !! Comentarios de IA con prioridad 
```

```js
// @IA: ?? Comentario de IA que requiere una decisión por parte del usuario 
```

```js
// Cualquier texto sin flags es conciderado un comentario de contexto hecho por un humano 
```

```js
// @TODO: Cosas a resolver (definido por humano)
```



# Comandos de contexto

## Comandos de bloque
```js
// {BlockName} >>
```

```js
// << {BlockName}
```

## Comandos de ancla
```js
// #PointID
```




# Archivos

## Archivos de comando

## Archivos de configuración 

## Archivos de test
