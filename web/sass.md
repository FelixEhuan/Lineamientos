# BEM

BEM es una convención de nombres para estilos CSS muy poderoso y útil, el cual vuelve el código facil de leer, fácil de trabajar, más robusto, explícito y estricto.

La metodología BEM asegura que cualquiera que participe en el desarrollo de un sitio web trabaja con un único código base y habla el mismo lenguaje. Usando la convención de nombres BEM nos prepara para cambios de diseño a nuestro sitio web.

En BEM existen 3 tipos de elementos: Bloques, Elementos y Modificadores. Cada uno con su propia convención de nombrado y representando una sección del html

## Bloque

Encapsula una única entidad propia. Mientras los bloques pueden ser anidados e interactuar con los demás, semánticamente permanecen iguales, no hay jerarquía.

#### Nombre

Los nombres de los bloques deben consistir en letras latinas, dígitos y guiones

El nombre de la clase de CSS es formada agregando un prefijo que indique la función del bloque `.block`

#### HTML

Cualquier nodo del DOM puede ser un bloque si acepta una clase

```markup
<div class="block">...</div>
```

#### CSS

* Usa el nombre de la clase del selector únicamente
* No incluir tag names o ids de los selectores
* No usar dependencia en otros bloques / elementos en una página

```css
.block { color: #042; }
```

## Elemento

Partes de un bloque que no tiene significado propio. Cualquier elemento que está semánticamente atado a un bloque

#### NOMBRE

 Los nombres de los elementos deben consistir en letras latinas, dígitos, guiones y guión bajo. La clase CSS es formada  cómo el nombre del bloque más dos guiones bajos más el nombre del elemento: `.block__elem`

#### HTML

Cualquier nodo del DOM dentro de un bloque puede ser un elemento. Dentro de un elemento todos los elementos son semánticamente iguales.

```markup
<div class="block">
	  ...
	  <span class="block__elem"></span>
	  ...
</div>
```

#### CSS

* Usa el nombre de la clase del selector únicamente
* No incluir tag names o ids de los selectores
* No usar dependencia en otros bloques / elementos en una página

_Good_

```css
.block__elem { color: #042; }
```

_Bad_

```css
.block .block__elem { color: #042; }
	div.block__elem { color: #042; }
```

_Ejemplo_

{% tabs %}
{% tab title="HTML" %}
```markup
<div class="pyme__banner">
	<!--<img src="assets/closer_background.jpg" alt="">-->
</div>

<div class="pyme__info flex container">
		<div class="pyme__info-logo">
			<img src="assets/pyme-assistant.png" alt="">
</div>

<div class="pyme__info-texto closer__info-texto">
		<h2 class="subtitulo">PYME ASSISTANT</h2>
		<p>Support platform for microentrepreneurs, this solution offers a more efficient control in their administration and daily operations of their businesses.</p>
		<p><b>Including the following benefits:</b></p>
		<ul>
			<li>Diagnosis of the main areas that a business must take, which will help you to know the current state of the company.</li>
			<li>Basic finance with a three-year projection, it will help you in making decisions about purchases, sales or projection of goals.</li>
			<li>Sales CRM, this solution will help you control the status of your sales (sales sheet, customer database, quote format, shipping, sale status).</li>
		</ul>
	</div>
</div>
 
<div class="pyme__badge">
	<div class="pyme__badge--container">
		<div class="pyme__badge--img">
			<a href="https://play.google.com/store/apps/details?id=com.colabora.soluciones.convocatoriafeyac" target="_blank">
				<img src="assets/google-play-badge.png" alt="">
			</a>
		</div>
	</div>
</div>
```
{% endtab %}

{% tab title="CSS" %}
```css
/* La sintaxis corresponde a SCSS */
.pyme {
	color: $gray;
	&__banner {
		padding-top: 83px;
		max-width: 1024px;
		margin: auto;
	}
	&__info {
		align-items: center;
		justify-content: center;
		flex-wrap: wrap;
		&-logo {
			flex-basis: 50%;
			text-align: center;
			height: auto;
			max-width: 500px;
		}
		&-texto {
			flex-basis: 50%;
			padding-left: 50px;
			h2 {
				text-align: center;
				font-size: 50px;
			}	
		}
	}
		&__fotos {
			&-vistas {
				margin-bottom: 50px;
				img {
					flex-basis: 20%;
				}
			}
		}
}

/* Sintaxis en css */

.pyme {
  color: #bababa;
}
.pyme__banner {
  padding-top: 83px;
  max-width: 1024px;
  margin: auto;
}
.pyme__info {
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
}
.pyme__info-logo {
  flex-basis: 50%;
  text-align: center;
  height: auto;
  max-width: 500px;
}
.pyme__info-texto {
  flex-basis: 50%;
  padding-left: 50px;
}
.pyme__info-texto h2 {
  text-align: center;
  font-size: 50px;
}
.pyme__fotos-vistas {
  margin-bottom: 50px;
}
.pyme__fotos-vistas img {
  flex-basis: 20%;
}
```
{% endtab %}
{% endtabs %}



