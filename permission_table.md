## 📊 Tabla de permisos CAN

| Nivel / Flag                   | Estructura de clases y funciones globales | Estructura interna de clases | Agregar clases y funciones nuevas | Contenido de funciones |
| ------------------------------ | ----------------------------------------- | ---------------------------- | --------------------------------- | ---------------------- |
| **`[X]`** (No estable)         | ✅ PUEDE cambiarse                         | ✅ PUEDE cambiarse            | ✅ PUEDE cambiarse                 | ✅ PUEDE cambiarse      |
| **`[+]`** (Estable externo)    | ❌ NO DEBE cambiarse                       | ✅ PUEDE cambiarse            | ✅ PUEDE cambiarse                 | ✅ PUEDE cambiarse      |
| **`[++]`** (Estable interno)   | ❌ NO DEBE cambiarse                       | ❌ NO DEBE cambiarse          | ✅ PUEDE cambiarse                 | ✅ PUEDE cambiarse      |
| **`[+++]`** (Congelado)        | ❌ NO DEBE cambiarse                       | ❌ NO DEBE cambiarse          | ❌ NO DEBE cambiarse               | ✅ PUEDE cambiarse      |
| **`[@Inmutable]`** (Inmutable) | ❌ NO DEBE cambiarse                       | ❌ NO DEBE cambiarse          | ❌ NO DEBE cambiarse               | ❌ NO DEBE cambiarse    |
