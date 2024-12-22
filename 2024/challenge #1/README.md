# Problema:

Santa Claus 🎅 ha recibido una lista de números mágicos que representan regalos 🎁, pero algunos de ellos están duplicados y deben ser eliminados para evitar confusiones. Además, los regalos deben ser ordenados en orden ascendente antes de entregárselos a los elfos.

Tu tarea es escribir una función que reciba una lista de números enteros (que pueden incluir duplicados) y devuelva una nueva lista sin duplicados, ordenada en orden ascendente.

**Ejmplos del Output:**

```javascript
const gifts1 = [3, 1, 2, 3, 4, 2, 5];
const preparedGifts1 = prepareGifts(gifts1);
console.log(preparedGifts1); // [1, 2, 3, 4, 5]

const gifts2 = [6, 5, 5, 5, 5];
const preparedGifts2 = prepareGifts(gifts2);
console.log(preparedGifts2); // [5, 6]

const gifts3 = [];
const preparedGifts3 = prepareGifts(gifts3);
console.log(preparedGifts3); // []
// No hay regalos, la lista queda vacía
```

# Soluciones Día #1

## Solución #1: con `Set` y `sort`:

**Complejidad:**

- Time complexity: `O(n log n)` debido al `sort`.
- Space complexity: `O(n)` donde `n` es el número de elementos únicos almacenados en `Set()`.

**Código:**

- La mejor solucion al problema, es la más eficiente en terminos de complejidad. También, es la más lejible y concisa además de ser idiomatica de JS.

```javascript
function prepareGifts(gifts) {
  return [...new Set(gifts)].sort((a, b) => a - b);
}
```

## Solución #2: con `reduce`:

**Complejidad:**

- Time complexity: `O(n²)` debido al `includes()` dentro de `reduce()`.
- Space complexity: `O(n)`donde `n` es el número de elementos únicos almacenados en el array de `reduce()`.

**Código:**

- Menos eficiente que usar `Set` debido al uso de `includes()`.

```javascript
function prepareGifts(gifts) {
  return gifts
    .reduce((unique, gift) => {
      if (!unique.includes(gift)) {
        unique.push(gift);
      }
      return unique;
    }, [])
    .sort((a, b) => a - b);
}
```

## Solución #3: Usando `Object` como `hash table`:

**Complejidad:**

- Time complexity: `O(n log n)` debido al `sort()`.
- Space complexity: `O(n)` donde `n` es el número de elementos únicos almacenados.

**Código:**

- Igual de eficiente que usar `Set` pero menos legible.

```javascript
function prepareGifts(gifts) {
  const uniqueObj = {};
  for (const gift of gifts) {
    uniqueObj[gift] = true;
  }
  return Object.keys(uniqueObj)
    .map(Number)
    .sort((a, b) => a - b);
}
```

## Solución #4: Usando el metodo de `Filter`:

**Complejidad:**

- Time complexity: ` O(n²)` debido al `Filter` y `indexOf()`.
- Space complexity: `O(n)` donde `n` es el número de elementos únicos almacenados.

**Código:**

- Igual de eficiente que usar `Set` pero menos legible.

```javascript
function prepareGifts(gifts) {
  return gifts
    .filter((gift, index) => gifts.indexOf(gift) === index)
    .sort((a, b) => a - b);
}
```
