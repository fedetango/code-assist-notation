# Code Assist Notation
# Notación de asistencia en código

**(CAN)** es una serie de instrucciones pensadas para facilitar la asistencia de agentes IA en código.Estás instrucciones son colocadas en forma de comentarios en el código a intervenir o en archivos de configuración especiales.Las instrucciones pueden ser colocadas por el usuario o por el agente de IA.

# Reglas

## Políticas de aplicación
- Los comandos son sugerencias a excepción de los comandos de ejecución INSERT que solicitan explicitamente a la IA que cree código.

## Comportamiento de la UA
- Cuando la IA agrega bloques debe definir la autoría con un comando de autoría.
- Cuando la IA agrega bloques de código debe marcarlos como `[X]`

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

## Herencia
- No hay herencia. 
- El último comando establecido sobrescribe el comportamiento del último comando del mismo tipo.

## Reglas por defecto
- Por defecto el contexto general tiene un permiso golbal `[X]*`






## Comandos de permiso 

### Alcance
- A nivel documento el permiso se establece así: `// @Document: [++]`. Debe ser el primer permiso mencionado en todo el documento.
- Para crear excepciones a nivel clase o función debe colocarse un `// [+]` inmediatamente antes a la declaración que se quiere afectar.

### Flags de Refactorización

#### NO ESTABLE
- Todo es modificable.
```js
// [X]
```

#### ESTABLE Y REFACTORIZABLE
- Las funciones y clases NO DEBEN eliminarse.
- Los nombres, argumentos y outputs de las funciones globales NO DEBEN modificarse.
- Los nombres de clases NO DEBEN modificarse.
- Las funciones y propiedades internas de clases **SI PUEDEN** modificarse.
- **SI PUEDEN** crearse nuevas clases y funciones.
```js
// [+]
```

#### ESTABLE Y REFACTORIZABLE
- Las funciones y clases **NO DEBEN** eliminarse.
- Los nombres y argumentos de las funciones globales **NO DEBEN** modificarse.
- Los nombres de clases **NO DEBEN** modificarse.
- Los nombres de funciones, sus argumentos y outputs; y propiedades internas de clases **NO DEBEN** modificarse.
- **SI PUEDEN** crearse nuevas clases y funciones.
```js
// [++]
```

#### ESTABLE, NO REFACTORIZABLE
- Las funciones y clases NO DEBEN eliminarse.
- Los nombres y argumentos de las funciones globales NO DEBEN modificarse.
- Los nombres de clases NO DEBEN modificarse.
- Las funciones y propiedades internas de clases **NO DEBEN** modificarse.
- **NO DEBEN** crearse nuevas clases y funciones.
```js
// [+++]
```

#### COMPLETAMENTE INMUTABLE
Las declaraciones afectadas son estables y NO DEBEN modificarse.
Tanto los nombres de las declaraciones como el contenido de las funciones y clases NO DEBEN modificarse.
```js
// [@Inmutable]
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




## Comandos de ejecución 

#### Inserción en línea
```js
// >> Reemplaza este comentario por código.
```

#### Inserción en contexto
```js
// >> !! Autorizado a reescribir todo el contexto
```

#### Sugerencia de inserción en línea
```js
// > Sugerencia para reemplazar esta línea por código.
```

#### Sugerencia de inserción contexto
```js
// > !! Sugerencia para reemplazar el contexto actual por otro código
```



## Comandos de contexto 

```js
// @IA.OptionalAgentName: Comentarios de IA
```

```js
// @IA: !! Comentarios de IA con prioridad 
```

```js
// @IA: ?? Comentario de IA que requiere una decisión por parte del usuario 
```

```js
// @IA: @TODO: Sugerencias para próximas implementaciones por parte de la IA.
```

```js
// Cualquier texto sin flags es conciderado un comentario de contexto hecho por un humano 
```

```js
// @USER.UserName: También se puede nombrar explícitamente.
```

```js
// @TODO: Cosas a resolver
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
