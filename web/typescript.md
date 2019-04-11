# Typescript

Al momento de escribir typescript podemos seguir ciertas reglas que ayudarán a los demás a entender nuestro código de forma que siempre que alguien quiere trabajar con él no se pierda mucho tiempo en entender la forma de trabajar

### Variables

Las variables deberán tener nombres explícitos \(camelCase\), a su vez se intentarán usar sustantivos para nombrarlas 

```typescript
let aN:any // Wrong
let arrayNombres:string[] // Good
```

Siempre se evitará usar el tipo any a menos que se desconozca la estructura de la información que estamos recibiendo

### Funciones y métodos

Las funciones y métodos deberán ser nombrados en formato camelCase y se intentarán usar verbos para nombrarlos

```typescript
nombres() {} // Wrong
obtenerNombres(){} //Good
```

Si una parte de una función o un método es repetitiva se deberá crear otro método / función que ejecute esa sección repetitiva

Para mejorar la lectura de las funciones y métodos se evitará el _hardcode_ usando en su lugar constantes

{% code-tabs %}
{% code-tabs-item title="Hardcode function" %}
```typescript
calcularAreaCirculo(radio:number) {
    return 3.1416 * Mat.pow(r,2)  // Si queremos cambiar el valor de PI entonces tendríamos que cambiarlo en todas las funciones 
}

calcularAreaEsfera(radio:number) {
    return 4*3.1416 * Mat.pow(r,2)  // Si queremos cambiar el valor de PI entonces tendríamos que cambiarlo en todas las funciones 
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="No hardcode function" %}
```typescript
const PI = 3.1416;
calcularAreaCirculo(radio:number) {
    return PI * Mat.pow(r,2)  // Si queremos cambiar el valor de PI entonces tendríamos que cambiarlo en todas las funciones 
}

calcularAreaEsfera(radio:number) {
    return PI * Mat.pow(r,2)  // Si queremos cambiar el valor de PI entonces tendríamos que cambiarlo en todas las funciones 
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Promesas

Las promesas es una de las grandes novedades del ECMAScript 6 nos permiten tener un mejor control de la programación asíncrona, sin embargo existen algunos problemas derivados de las promesas que podemos evitar.

#### Concatenación de promesas

Evitar la concatenación de promesas ya que dificulta la lectura de la función al hacer crecer el código considerablemente

{% code-tabs %}
{% code-tabs-item title="Concatenación de variables" %}
```typescript
agregarUsuario() {
  abrirModalAgregar().then(data => {
    abrirModalConfirmacion().then( () => {
      abrirLoading().then(loading => {
        this.crearUsuario(data).then( () => {
          loading.dismiss();
        });
      });
    });
  });
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Observamos que la concatenación de las promesas se vuelve un problema mientras más operaciones hagamos y el código se vuelve más ilegible, por lo que se debe usar en su lugar las funciones asíncronas, para mejorar el flujo y lectura del código

Una función con la palabra reservada `async`  admite el uso de la palabra `await` , el cuál básicamente resuelve la promesa y la respuesta del `resolve()`  de la promesa es devuelta cómo `return` de la función \(Ver siguiente función\)

```typescript
async agregarUsuario() {
    const data = await abrirModalAgregar();
    await abrirModalConfirmacion();
    const loading = await abrirLoading();
    await crearUsuario(data)
    loading.dismiss(); // cada instrucción se ejecuta cuando se ha resuelto la promesa anterior
}
```



