# CSS
Introducción a CSS

<h3 id="selector-universal">2.1.1. Selector universal</h3>
<p>Se utiliza para seleccionar todos los elementos de la página. El siguiente ejemplo elimina el margen y el relleno de todos los elementos HTML (por ahora no es importante fijarse en la parte de la declaración de la regla CSS):</p>
<div class="code css"><pre class="css">* {
  <span class="hljs-attribute">margin</span>: <span class="hljs-number">0</span>;
  <span class="hljs-attribute">padding</span>: <span class="hljs-number">0</span>;
}</pre></div>
<p>El selector universal se indica mediante un asterisco (<code>*</code>). A pesar de su sencillez, no se utiliza habitualmente, ya que es difícil que un mismo estilo se pueda aplicar a todos los elementos de una página.</p>
<p>No obstante, sí que se suele combinar con otros selectores y además, forma parte de algunos <em>hacks</em> muy utilizados, como se verá más adelante.</p>
<h3 id="selector-de-tipo-o-etiqueta">2.1.2. Selector de tipo o etiqueta</h3>
<p>Selecciona todos los elementos de la página cuya etiqueta HTML coincide con el valor del selector. El siguiente ejemplo selecciona todos los párrafos de la página:</p>
<div class="code css"><pre class="css"><span class="hljs-selector-tag">p</span> {
  ...
}</pre></div>
<p>Para utilizar este selector, solamente es necesario indicar el nombre de una etiqueta HTML (sin los caracteres <code>&lt;</code> y <code>&gt;</code>) correspondiente a los elementos que se quieren seleccionar.</p>
<p>El siguiente ejemplo aplica diferentes estilos a los titulares y a los párrafos de una página HTML:</p>
<div class="code css"><pre class="css"><span class="hljs-selector-tag">h1</span> {
  <span class="hljs-attribute">color</span>: red;
}

<span class="hljs-selector-tag">h2</span> {
  <span class="hljs-attribute">color</span>: blue;
}

<span class="hljs-selector-tag">p</span> {
  <span class="hljs-attribute">color</span>: black;
}</pre></div>
<p>Si se quiere aplicar los mismos estilos a dos etiquetas diferentes, se pueden encadenar los selectores. En el siguiente ejemplo, los títulos de sección <code>h1</code>, <code>h2</code> y <code>h3</code> comparten los mismos estilos:</p>
<div class="code css"><pre class="css"><span class="hljs-selector-tag">h1</span> {
  <span class="hljs-attribute">color</span>: <span class="hljs-number">#8A8E27</span>;
  <span class="hljs-attribute">font-weight</span>: normal;
  <span class="hljs-attribute">font-family</span>: Arial, Helvetica, sans-serif;
}
<span class="hljs-selector-tag">h2</span> {
  <span class="hljs-attribute">color</span>: <span class="hljs-number">#8A8E27</span>;
  <span class="hljs-attribute">font-weight</span>: normal;
  <span class="hljs-attribute">font-family</span>: Arial, Helvetica, sans-serif;
}
<span class="hljs-selector-tag">h3</span> {
  <span class="hljs-attribute">color</span>: <span class="hljs-number">#8A8E27</span>;
  <span class="hljs-attribute">font-weight</span>: normal;
  <span class="hljs-attribute">font-family</span>: Arial, Helvetica, sans-serif;
}</pre></div>
<p>En este caso, CSS permite agrupar todas las reglas individuales en una sola regla con un selector múltiple. Para ello, se incluyen todos los selectores separados por una coma (<code>,</code>) y el resultado es que la siguiente regla CSS es equivalente a las tres reglas anteriores:</p>
<div class="code css"><pre class="css"><span class="hljs-selector-tag">h1</span>, <span class="hljs-selector-tag">h2</span>, <span class="hljs-selector-tag">h3</span> {
  <span class="hljs-attribute">color</span>: <span class="hljs-number">#8A8E27</span>;
  <span class="hljs-attribute">font-weight</span>: normal;
  <span class="hljs-attribute">font-family</span>: Arial, Helvetica, sans-serif;
}</pre></div>
<p>En las hojas de estilo complejas, es habitual agrupar las propiedades comunes de varios elementos en una única regla CSS y posteriormente definir las propiedades específicas de esos mismos elementos. El siguiente ejemplo establece en primer lugar las propiedades comunes de los títulos de sección (color y tipo de letra) y a continuación, establece el tamaño de letra de cada uno de ellos:</p>
<div class="code css"><pre class="css"><span class="hljs-selector-tag">h1</span>, <span class="hljs-selector-tag">h2</span>, <span class="hljs-selector-tag">h3</span> {
  <span class="hljs-attribute">color</span>: <span class="hljs-number">#8A8E27</span>;
  <span class="hljs-attribute">font-weight</span>: normal;
  <span class="hljs-attribute">font-family</span>: Arial, Helvetica, sans-serif;
}

<span class="hljs-selector-tag">h1</span> { <span class="hljs-attribute">font-size</span>: <span class="hljs-number">2em</span>; }
<span class="hljs-selector-tag">h2</span> { <span class="hljs-attribute">font-size</span>: <span class="hljs-number">1.5em</span>; }
<span class="hljs-selector-tag">h3</span> { <span class="hljs-attribute">font-size</span>: <span class="hljs-number">1.2em</span>; }</pre></div>
<h3 id="selector-descendente">2.1.3. Selector descendente</h3>
<p>Selecciona los elementos que se encuentran dentro de otros elementos. Un elemento es descendiente de otro cuando se encuentra entre las etiquetas de apertura y de cierre del otro elemento.</p>
<p>El selector del siguiente ejemplo selecciona todos los elementos <code>&lt;span&gt;</code> de la página que se encuentren dentro de un elemento <code>&lt;p&gt;</code>:</p>
<div class="code css"><pre class="css"><span class="hljs-selector-tag">p</span> <span class="hljs-selector-tag">span</span> { <span class="hljs-attribute">color</span>: red; }</pre></div>
<p>Si el código HTML de la página es el siguiente:</p>
<div class="code html"><pre class="html"><span class="hljs-tag">&lt;<span class="hljs-name">p</span>&gt;</span>
  ...
  <span class="hljs-tag">&lt;<span class="hljs-name">span</span>&gt;</span>texto1<span class="hljs-tag">&lt;/<span class="hljs-name">span</span>&gt;</span>
  ...
  <span class="hljs-tag">&lt;<span class="hljs-name">a</span> <span class="hljs-attr">href</span>=<span class="hljs-string">""</span>&gt;</span>...<span class="hljs-tag">&lt;<span class="hljs-name">span</span>&gt;</span>texto2<span class="hljs-tag">&lt;/<span class="hljs-name">span</span>&gt;</span><span class="hljs-tag">&lt;/<span class="hljs-name">a</span>&gt;</span>
  ...
<span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span></pre></div>
<p>El selector <code>p span</code> selecciona tanto <code>texto1</code> como <code>texto2</code>. El motivo es que en el selector descendente, un elemento no tiene que ser descendiente directo del otro. La única condición es que un elemento debe estar dentro de otro elemento, sin importar el nivel de profundidad en el que se encuentre.</p>
<p>Al resto de elementos <code>&lt;span&gt;</code> de la página que no están dentro de un elemento <code>&lt;p&gt;</code>, no se les aplica la regla CSS anterior.</p>
<p>Los selectores descendentes permiten aumentar la precisión del selector de tipo o etiqueta. Así, utilizando el selector descendente es posible aplicar diferentes estilos a los elementos del mismo tipo. El siguiente ejemplo amplía el anterior y muestra de color azul todo el texto de los <code>&lt;span&gt;</code> contenidos dentro de un <code>&lt;h1&gt;</code>:</p>
<div class="code css"><pre class="css"><span class="hljs-selector-tag">p</span> <span class="hljs-selector-tag">span</span>  { <span class="hljs-attribute">color</span>: red;  }
<span class="hljs-selector-tag">h1</span> <span class="hljs-selector-tag">span</span> { <span class="hljs-attribute">color</span>: blue; }</pre></div>
<p>Con las reglas CSS anteriores:</p>
<ul>
<li>Los elementos <code>&lt;span&gt;</code> que se encuentran dentro de un elemento <code>&lt;p&gt;</code> se muestran de color rojo.</li>
<li>Los elementos <code>&lt;span&gt;</code> que se encuentran dentro de un elemento <code>&lt;h1&gt;</code> se muestran de color azul.</li>
<li>El resto de elementos <code>&lt;span&gt;</code> de la página, se muestran con el color por defecto aplicado por el navegador.</li>
</ul>
<p>La sintaxis formal del selector descendente se muestra a continuación:</p>
<div class="code"><pre class="code">selector1 selector2 selector3 ... selectorN</pre></div>
<p>Los selectores descendentes siempre están formados por dos o más selectores separados entre sí por espacios en blanco. El último selector indica el elemento sobre el que se aplican los estilos y todos los selectores anteriores indican el lugar en el que se debe encontrar ese elemento.</p>
<p>En el siguiente ejemplo, el selector descendente se compone de cuatro selectores:</p>
<div class="code css"><pre class="css"><span class="hljs-selector-tag">p</span> <span class="hljs-selector-tag">a</span> <span class="hljs-selector-tag">span</span> <span class="hljs-selector-tag">em</span> { <span class="hljs-attribute">text-decoration</span>: underline; }</pre></div>
<p>Los estilos de la regla anterior se aplican a los elementos de tipo <code>&lt;em&gt;</code> que se encuentren dentro de elementos de tipo <code>&lt;span&gt;</code>, que a su vez se encuentren dentro de elementos de tipo <code>&lt;a&gt;</code> que se encuentren dentro de elementos de tipo <code>&lt;p&gt;</code>.</p>
<p>No debe confundirse el selector descendente con la combinación de selectores:</p>
<div class="code css"><pre class="css"><span class="hljs-comment">/* El estilo se aplica a todos los elementos "p", "a", "span" y "em" */</span>
<span class="hljs-selector-tag">p</span>, <span class="hljs-selector-tag">a</span>, <span class="hljs-selector-tag">span</span>, <span class="hljs-selector-tag">em</span> { <span class="hljs-attribute">text-decoration</span>: underline; }

<span class="hljs-comment">/* El estilo se aplica solo a los elementos "em" que se
   encuentran dentro de "p a span" */</span>
<span class="hljs-selector-tag">p</span> <span class="hljs-selector-tag">a</span> <span class="hljs-selector-tag">span</span> <span class="hljs-selector-tag">em</span> { <span class="hljs-attribute">text-decoration</span>: underline; }</pre></div>
<p>Se puede restringir el alcance del selector descendente combinándolo con el selector universal. El siguiente ejemplo, muestra los dos enlaces de color rojo:</p>
<div class="code css"><pre class="css"><span class="hljs-selector-tag">p</span> <span class="hljs-selector-tag">a</span> { <span class="hljs-attribute">color</span>: red; }

&lt;<span class="hljs-selector-tag">p</span>&gt;&lt;<span class="hljs-selector-tag">a</span> <span class="hljs-selector-tag">href</span>="#"&gt;<span class="hljs-selector-tag">Enlace</span>&lt;/<span class="hljs-selector-tag">a</span>&gt;&lt;/<span class="hljs-selector-tag">p</span>&gt;
&lt;<span class="hljs-selector-tag">p</span>&gt;&lt;<span class="hljs-selector-tag">span</span>&gt;&lt;<span class="hljs-selector-tag">a</span> <span class="hljs-selector-tag">href</span>="#"&gt;<span class="hljs-selector-tag">Enlace</span>&lt;/<span class="hljs-selector-tag">a</span>&gt;&lt;/<span class="hljs-selector-tag">span</span>&gt;&lt;/<span class="hljs-selector-tag">p</span>&gt;</pre></div>
<p>Sin embargo, en el siguiente ejemplo solamente el segundo enlace se muestra de color rojo:</p>
<div class="code css"><pre class="css"><span class="hljs-selector-tag">p</span> * <span class="hljs-selector-tag">a</span> { <span class="hljs-attribute">color</span>: red; }

&lt;<span class="hljs-selector-tag">p</span>&gt;&lt;<span class="hljs-selector-tag">a</span> <span class="hljs-selector-tag">href</span>="#"&gt;<span class="hljs-selector-tag">Enlace</span>&lt;/<span class="hljs-selector-tag">a</span>&gt;&lt;/<span class="hljs-selector-tag">p</span>&gt;
&lt;<span class="hljs-selector-tag">p</span>&gt;&lt;<span class="hljs-selector-tag">span</span>&gt;&lt;<span class="hljs-selector-tag">a</span> <span class="hljs-selector-tag">href</span>="#"&gt;<span class="hljs-selector-tag">Enlace</span>&lt;/<span class="hljs-selector-tag">a</span>&gt;&lt;/<span class="hljs-selector-tag">span</span>&gt;&lt;/<span class="hljs-selector-tag">p</span>&gt;</pre></div>
<p>La razón es que el selector <code>p * a</code> se interpreta como <em>todos los elementos de tipo <code>&lt;a&gt;</code> que se encuentren dentro de cualquier elemento que, a su vez, se encuentre dentro de un elemento de tipo <code>&lt;p&gt;</code></em>. Como el primer elemento <code>&lt;a&gt;</code> se encuentra directamente bajo un elemento <code>&lt;p&gt;</code>, no se cumple la condición del selector <code>p * a</code>.</p>
<h3 id="selector-de-clase">2.1.4. Selector de clase</h3>
<p>Si se considera el siguiente código HTML de ejemplo:</p>
<div class="code html"><pre class="html"><span class="hljs-tag">&lt;<span class="hljs-name">body</span>&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">p</span>&gt;</span>Lorem ipsum dolor sit amet...<span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">p</span>&gt;</span>Nunc sed lacus et est adipiscing accumsan...<span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">p</span>&gt;</span>Class aptent taciti sociosqu ad litora...<span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">body</span>&gt;</span></pre></div>
<p>¿Cómo se pueden aplicar estilos CSS sólo al primer párrafo? El selector universal (<code>*</code>) no se puede utilizar porque selecciona todos los elementos de la página. El selector de tipo o etiqueta (<code>p</code>) tampoco se puede utilizar porque seleccionaría todos los párrafos. Por último, el selector descendente (<code>body p</code>) tampoco se puede utilizar porque todos los párrafos se encuentran en el mismo sitio.</p>
<p>Una de las soluciones más sencillas para aplicar estilos a un solo elemento de la página consiste en utilizar el atributo <code>class</code> de HTML sobre ese elemento para indicar directamente la regla CSS que se le debe aplicar:</p>
<div class="code html"><pre class="html"><span class="hljs-tag">&lt;<span class="hljs-name">body</span>&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">p</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"destacado"</span>&gt;</span>Lorem ipsum dolor sit amet...<span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">p</span>&gt;</span>Nunc sed lacus et est adipiscing accumsan...<span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">p</span>&gt;</span>Class aptent taciti sociosqu ad litora...<span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">body</span>&gt;</span></pre></div>
<p>A continuación, se crea en el archivo CSS una nueva regla llamada <code>destacado</code> con todos los estilos que se van a aplicar al elemento. Para que el navegador no confunda este selector con los otros tipos de selectores, se prefija el valor del atributo <code>class</code> con un punto (<code>.</code>) tal y como muestra el siguiente ejemplo:</p>
<div class="code css"><pre class="css"><span class="hljs-selector-class">.destacado</span> { <span class="hljs-attribute">color</span>: red; }</pre></div>
<p>El selector <code>.destacado</code> se interpreta como <em>"cualquier elemento de la página cuyo atributo <code>class</code> sea igual a <code>destacado</code>"</em>, por lo que solamente el primer párrafo cumple esa condición.</p>
<p>Este tipo de selectores se llaman selectores de clase y son los más utilizados junto con los selectores de ID que se verán a continuación. La principal característica de este selector es que en una misma página HTML varios elementos diferentes pueden utilizar el mismo valor en el atributo <code>class</code>:</p>
<div class="code html"><pre class="html"><span class="hljs-tag">&lt;<span class="hljs-name">body</span>&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">p</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"destacado"</span>&gt;</span>Lorem ipsum dolor sit amet...<span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">p</span>&gt;</span>Nunc sed lacus et <span class="hljs-tag">&lt;<span class="hljs-name">a</span> <span class="hljs-attr">href</span>=<span class="hljs-string">"#"</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"destacado"</span>&gt;</span>est adipiscing<span class="hljs-tag">&lt;/<span class="hljs-name">a</span>&gt;</span> accumsan...<span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">p</span>&gt;</span>Class aptent taciti <span class="hljs-tag">&lt;<span class="hljs-name">em</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"destacado"</span>&gt;</span>sociosqu ad<span class="hljs-tag">&lt;/<span class="hljs-name">em</span>&gt;</span> litora...<span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">body</span>&gt;</span></pre></div>
<p>Los selectores de clase son imprescindibles para diseñar páginas web complejas, ya que permiten disponer de una precisión total al seleccionar los elementos. Además, estos selectores permiten reutilizar los mismos estilos para varios elementos diferentes.</p>
<p>A continuación se muestra otro ejemplo de selectores de clase:</p>
<div class="code css"><pre class="css"><span class="hljs-selector-class">.aviso</span> {
  <span class="hljs-attribute">padding</span>: <span class="hljs-number">0.5em</span>;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">1px</span> solid <span class="hljs-number">#98be10</span>;
  <span class="hljs-attribute">background</span>: <span class="hljs-number">#f6feda</span>;
}

<span class="hljs-selector-class">.error</span> {
  <span class="hljs-attribute">color</span>: <span class="hljs-number">#930</span>;
  <span class="hljs-attribute">font-weight</span>: bold;
}
&lt;<span class="hljs-selector-tag">span</span> <span class="hljs-selector-tag">class</span>="<span class="hljs-selector-tag">error</span>"&gt;...&lt;/<span class="hljs-selector-tag">span</span>&gt;

&lt;<span class="hljs-selector-tag">div</span> <span class="hljs-selector-tag">class</span>="<span class="hljs-selector-tag">aviso</span>"&gt;...&lt;/<span class="hljs-selector-tag">div</span>&gt;</pre></div>
<p>El elemento <code>&lt;span&gt;</code> tiene un atributo <code>class="error"</code>, por lo que se le aplican las reglas CSS indicadas por el selector <code>.error</code>. Por su parte, el elemento <code>&lt;div&gt;</code> tiene un atributo <code>class="aviso"</code>, por lo que su estilo es el que definen las reglas CSS del selector <code>.aviso</code>.</p>
<p>En ocasiones, es necesario restringir el alcance del selector de clase. Si se considera de nuevo el ejemplo anterior:</p>
<div class="code html"><pre class="html"><span class="hljs-tag">&lt;<span class="hljs-name">body</span>&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">p</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"destacado"</span>&gt;</span>Lorem ipsum dolor sit amet...<span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">p</span>&gt;</span>Nunc sed lacus et <span class="hljs-tag">&lt;<span class="hljs-name">a</span> <span class="hljs-attr">href</span>=<span class="hljs-string">"#"</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"destacado"</span>&gt;</span>est adipiscing<span class="hljs-tag">&lt;/<span class="hljs-name">a</span>&gt;</span> accumsan...<span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">p</span>&gt;</span>Class aptent taciti <span class="hljs-tag">&lt;<span class="hljs-name">em</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"destacado"</span>&gt;</span>sociosqu ad<span class="hljs-tag">&lt;/<span class="hljs-name">em</span>&gt;</span> litora...<span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">body</span>&gt;</span></pre></div>
<p>¿Cómo es posible aplicar estilos solamente al párrafo cuyo atributo <code>class</code> sea igual a <code>destacado</code>? Combinando el selector de tipo y el selector de clase, se obtiene un selector mucho más específico:</p>
<div class="code css"><pre class="css"><span class="hljs-selector-tag">p</span><span class="hljs-selector-class">.destacado</span> { <span class="hljs-attribute">color</span>: red }</pre></div>
<p>El selector <code>p.destacado</code> se interpreta como <em>"aquellos elementos de tipo <code>&lt;p&gt;</code> que dispongan de un atributo <code>class</code> con valor <code>destacado</code>"</em>. De la misma forma, el selector <code>a.destacado</code> solamente selecciona los enlaces cuyo atributo <code>class</code> sea igual a <code>destacado</code>.</p>
<p>De lo anterior se deduce que el atributo <code>.destacado</code> es equivalente a <code>*.destacado</code>, por lo que todos los diseñadores obvian el símbolo <code>*</code> al escribir un selector de clase normal.</p>
<p>No debe confundirse el selector de clase con los selectores anteriores:</p>
<div class="code css"><pre class="css"><span class="hljs-comment">/* Todos los elementos de tipo "p" con atributo class="aviso" */</span>
<span class="hljs-selector-tag">p</span><span class="hljs-selector-class">.aviso</span> { ... }

<span class="hljs-comment">/* Todos los elementos con atributo class="aviso" que estén dentro
   de cualquier elemento de tipo "p" */</span>
<span class="hljs-selector-tag">p</span> <span class="hljs-selector-class">.aviso</span> { ... }

<span class="hljs-comment">/* Todos los elementos "p" de la página y todos los elementos con
   atributo class="aviso" de la página */</span>
<span class="hljs-selector-tag">p</span>, <span class="hljs-selector-class">.aviso</span> { ... }</pre></div>
<p>Por último, es posible aplicar los estilos de varias clases CSS sobre un mismo elemento. La sintaxis es similar, pero los diferentes valores del atributo <code>class</code> se separan con espacios en blanco. En el siguiente ejemplo:</p>
<div class="code html"><pre class="html"><span class="hljs-tag">&lt;<span class="hljs-name">p</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"especial destacado error"</span>&gt;</span>Párrafo de texto...<span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span></pre></div>
<p>Al párrafo anterior se le aplican los estilos definidos en las reglas <code>.especial</code>, <code>.destacado</code> y <code>.error</code>, por lo que en el siguiente ejemplo, el texto del párrafo se vería de color rojo, en negrita y con un tamaño de letra de 15 píxel:</p>
<div class="code html"><pre class="html">.error { color: red; }
.destacado { font-size: 15px; }
.especial  { font-weight: bold; }

<span class="hljs-tag">&lt;<span class="hljs-name">p</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"especial destacado error"</span>&gt;</span>Párrafo de texto...<span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span></pre></div>
<p>Si un elemento dispone de un atributo <code>class</code> con más de un valor, es posible utilizar un selector más avanzado:</p>
<div class="code html"><pre class="html">.error { color: red; }
.error.destacado { color: blue; }
.destacado { font-size: 15px; }
.especial  { font-weight: bold; }

<span class="hljs-tag">&lt;<span class="hljs-name">p</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"especial destacado error"</span>&gt;</span>Párrafo de texto...<span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span></pre></div>
<p>En el ejemplo anterior, el color de la letra del texto es azul y no rojo. El motivo es que se ha utilizado un selector de clase múltiple <code>.error.destacado</code>, que se interpreta como <em>"aquellos elementos de la página que dispongan de un atributo <code>class</code> con al menos los valores <code>error</code> y <code>destacado</code>"</em>.</p>
<h3 id="selectores-de-id">2.1.5. Selectores de ID</h3>
<p>En ocasiones, es necesario aplicar estilos CSS a un único elemento de la página. Aunque puede utilizarse un selector de clase para aplicar estilos a un único elemento, existe otro selector más eficiente en este caso.</p>
<p>El selector de ID permite seleccionar un elemento de la página a través del valor de su atributo <code>id</code>. Este tipo de selectores sólo seleccionan un elemento de la página porque el valor del atributo <code>id</code> no se puede repetir en dos elementos diferentes de una misma página.</p>
<p>La sintaxis de los selectores de ID es muy parecida a la de los selectores de clase, salvo que se utiliza el símbolo de la almohadilla (<code>#</code>) en vez del punto (<code>.</code>) como prefijo del nombre de la regla CSS:</p>
<div class="code css"><pre class="css"><span class="hljs-selector-id">#destacado</span> { <span class="hljs-attribute">color</span>: red; }

&lt;<span class="hljs-selector-tag">p</span>&gt;<span class="hljs-selector-tag">Primer</span> <span class="hljs-selector-tag">p</span>á<span class="hljs-selector-tag">rrafo</span>&lt;/<span class="hljs-selector-tag">p</span>&gt;
&lt;<span class="hljs-selector-tag">p</span> <span class="hljs-selector-tag">id</span>="<span class="hljs-selector-tag">destacado</span>"&gt;<span class="hljs-selector-tag">Segundo</span> <span class="hljs-selector-tag">p</span>á<span class="hljs-selector-tag">rrafo</span>&lt;/<span class="hljs-selector-tag">p</span>&gt;
&lt;<span class="hljs-selector-tag">p</span>&gt;<span class="hljs-selector-tag">Tercer</span> <span class="hljs-selector-tag">p</span>á<span class="hljs-selector-tag">rrafo</span>&lt;/<span class="hljs-selector-tag">p</span>&gt;</pre></div>
<p>En el ejemplo anterior, el selector <code>#destacado</code> solamente selecciona el segundo párrafo (cuyo atributo <code>id</code> es igual a <code>destacado</code>).</p>
<p>La principal diferencia entre este tipo de selector y el selector de clase tiene que ver con HTML y no con CSS. Como se sabe, en una misma página, el valor del atributo <code>id</code> debe ser único, de forma que dos elementos diferentes no pueden tener el mismo valor de <code>id</code>. Sin embargo, el atributo <code>class</code> no es obligatorio que sea único, de forma que muchos elementos HTML diferentes pueden compartir el mismo valor para su atributo <code>class</code>.</p>
<p>De esta forma, la recomendación general es la de utilizar el selector de ID cuando se quiere aplicar un estilo a un solo elemento específico de la página y utilizar el selector de clase cuando se quiere aplicar un estilo a varios elementos diferentes de la página HTML.</p>
<p>Al igual que los selectores de clase, en este caso también se puede restringir el alcance del selector mediante la combinación con otros selectores. El siguiente ejemplo aplica la regla CSS solamente al elemento de tipo <code>&lt;p&gt;</code> que tenga un atributo <code>id</code> igual al indicado:</p>
<div class="code css"><pre class="css"><span class="hljs-selector-tag">p</span><span class="hljs-selector-id">#aviso</span> { <span class="hljs-attribute">color</span>: blue; }</pre></div>
<p>A primera vista, restringir el alcance de un selector de ID puede parecer absurdo. En realidad, un selector de tipo <code>p#aviso</code> sólo tiene sentido cuando el archivo CSS se aplica sobre muchas páginas HTML diferentes.</p>
<p>En este caso, algunas páginas pueden disponer de elementos con un atributo <code>id</code> igual a <code>aviso</code> y que no sean párrafos, por lo que la regla anterior no se aplica sobre esos elementos.</p>
<p>No debe confundirse el selector de ID con los selectores anteriores:</p>
<div class="code css"><pre class="css"><span class="hljs-comment">/* Todos los elementos de tipo "p" con atributo id="aviso" */</span>
<span class="hljs-selector-tag">p</span><span class="hljs-selector-id">#aviso</span> { ... }

<span class="hljs-comment">/* Todos los elementos con atributo id="aviso" que estén dentro
	de cualquier elemento de tipo "p" */</span>
<span class="hljs-selector-tag">p</span> <span class="hljs-selector-id">#aviso</span> { ... }

<span class="hljs-comment">/* Todos los elementos "p" de la página y todos los elementos con
	atributo id="aviso" de la página */</span>
<span class="hljs-selector-tag">p</span>, <span class="hljs-selector-id">#aviso</span> { ... }</pre></div>
<h3 id="combinacion-de-selectores-basicos">2.1.6. Combinación de selectores básicos</h3>
<p>CSS permite la combinación de uno o más tipos de selectores para restringir el alcance de las reglas CSS. A continuación se muestran algunos ejemplos habituales de combinación de selectores.</p>
<div class="code css"><pre class="css"><span class="hljs-selector-class">.aviso</span> <span class="hljs-selector-class">.especial</span> { ... }</pre></div>
<p>El anterior selector solamente selecciona aquellos elementos con un <code>class="especial"</code> que se encuentren dentro de cualquier elemento con un <code>class="aviso"</code>.</p>
<p>Si se modifica el anterior selector:</p>
<div class="code css"><pre class="css"><span class="hljs-selector-tag">div</span><span class="hljs-selector-class">.aviso</span> <span class="hljs-selector-tag">span</span><span class="hljs-selector-class">.especial</span> { ... }</pre></div>
<p>Ahora, el selector solamente selecciona aquellos elementos de tipo <code>&lt;span&gt;</code> con un atributo <code>class="especial"</code> que estén dentro de cualquier elemento de tipo <code>&lt;div&gt;</code> que tenga un atributo <code>class="aviso"</code>.</p>
<p>La combinación de selectores puede llegar a ser todo lo compleja que sea necesario:</p>
<div class="code css"><pre class="css"><span class="hljs-selector-tag">ul</span><span class="hljs-selector-id">#menuPrincipal</span> <span class="hljs-selector-tag">li</span><span class="hljs-selector-class">.destacado</span> <span class="hljs-selector-tag">a</span><span class="hljs-selector-id">#inicio</span> { ... }</pre></div>
<p>El anterior selector hace referencia al enlace con un atributo <code>id</code> igual a <code>inicio</code> que se encuentra dentro de un elemento de tipo <code>&lt;li&gt;</code> con un atributo <code>class</code> igual a <code>destacado</code>, que forma parte de una lista <code>&lt;ul&gt;</code> con un atributo <code>id</code> igual a <code>menuPrincipal</code>.</p>
