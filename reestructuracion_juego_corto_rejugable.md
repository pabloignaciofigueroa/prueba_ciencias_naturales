# Reestructuración corta y rejugable · Ciencias Naturales 1° básico

## Regla base
- Cada sección muestra **máximo 5 preguntas reales por partida**.
- No se cargan todas las preguntas al primer intento.
- Cada vez que el niño o niña toca **“Volver a jugar”**, la sección sortea un set nuevo.
- El sorteo no es caótico: cada sección elige **1 pregunta por bucket**, así mantiene variedad y coherencia.

## Cómo queda el juego

### Mundo 1 · Detective de los sentidos
Hook: descubrir qué sentido sirve en cada caso.  
Ronda: 5 preguntas.
- 1 de relacionar sentido y cuerpo
- 1 de completar
- 1 de situación
- 1 de verdadero/falso
- 1 de adivinanza

### Mundo 2 · Escudo protector
Hook: decidir qué cuida y qué daña los sentidos.  
Ronda: 5 preguntas.
- 1 de cuida/daña
- 1 de bien/mal
- 1 de emparejar cuidado
- 1 de acción correcta
- 1 de decisión cotidiana

### Mundo 3 · Cuerpo en movimiento
Hook: reconocer qué acciones ayudan al cuerpo.  
Ronda: 5 preguntas.
- 1 de mover o no
- 1 de hace bien / no
- 1 de completar idea
- 1 de decisión saludable
- 1 de verdadero/falso

### Mundo 4 · Mercado saludable
Hook: elegir comidas y colaciones mejores para el cuerpo.  
Ronda: 5 preguntas.
- 1 de clasificar
- 1 de clasificar 2
- 1 de mejor opción
- 1 de colación
- 1 de verdadero/falso

### Mundo 5 · Copa Natural
Hook: cierre corto con mezcla de temas.  
Ronda: 5 preguntas.
- 1 de sentidos
- 1 de cuidado
- 1 de movimiento
- 1 de comida
- 1 reto mixto

## Qué cambia de fondo
El juego deja de ser una ficha gigante disfrazada y pasa a ser:
- ronda corta
- premio rápido
- fin claro
- replay inmediato
- preguntas nuevas en la siguiente vuelta

## Qué artefactos te dejo
1. `pool_juego_randomizable_ciencias.json`
   - pool reducido y bucketizado
   - 5 secciones
   - 5 preguntas por run
   - selección coherente para replay

2. `selector_rondas_ciencias.js`
   - helper simple para sacar una ronda nueva
   - evita repetir las últimas preguntas vistas por bucket

## Recomendación de UX
Al terminar cada mundo:
- mostrar estrellas
- mostrar “Jugaste 5 de X”
- botón **Seguir**
- botón **Volver a jugar**
- texto corto: “Te saldrá una ronda nueva”

## Regla importante
No vuelvas a mostrar listas largas de 8, 10 o 12 preguntas de una sola vez.
El pool puede ser grande.
La ronda visible no.
