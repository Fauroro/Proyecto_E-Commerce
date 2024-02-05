# PROYECTO E-COMMERCE

Para este proyecto se requirió la creación de los siguientes archivos de estilos:

* **style.css ->** Archivo de estilos principal, en ella se realizan la edición de los estilos generales de todo el proyecto
* **styCat1.css ->** Esta hoja de estilos se encarga de modificar y dar estilos específicos para todas las paginas que muestran las categorías, además de modificar el MediaQuery que se encargara del responsive de dichas paginas; las hojas **styCat#.css** que comienzan a partir del 2 se encargan de modificar  las imágenes necesarias para cada categoría individual.
* **styProd1.css ->** Hoja de estilos encargada de generalizar los estilos y disposición para cada uno de los productos que corresponden a su categoría: se genera un archivo **styProd#.css** para cada hoja de estilos de los productos dependiendo de la categoría.

## style.css

En * se inicializan los estilos eliminando **margin** y **padding** predeterminados por el navegador, además se inicializa el tamaño total del elemento con **box-sizyng**

al body se le asigna una imagen de background fijo y que ocupe toda la pantalla sin desplazarse

al header se le asigna un color de fondo

```css
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}
body{
    background: url('../images/5594016.jpg') no-repeat center center fixed;
    background-size: cover;
    
}
header{
    background: lightgray;
}
```

en up i se le asigna el estilo al boton que se encarga de regresar a la parte superior de todas las paginas; se fija con **position:fixed;** de tal manera que siempre se mantenga en una ubicacion predeterminada, se le asigna color forma y prioridad con **z-index** para que siempre se encuentre en el nivel superior

```css
.up i {
    color: #d3d3d3;
    padding: 10px;
    position: fixed;
    bottom: 3%;
    right: 3%;
    background-color: #193d549a;
    padding: 0;
    width: fit-content;
    border-radius: 50%;
    font-size: 2rem;
    z-index: 100;
}
```

con ul, li se le quita el formato de lista para generar la disposición del menú hamburguesa

```css
ul,li {
    list-style: none;
    padding: 10px;
}
```

con .nave, .navCat se le asigna formato a los menus utilizados, se disponen como flex para facilitar el manejo del menú hamburguesa y se usa **justify-content: space-between;** para dar espacio entre los logos y el nombre y las opciones del menú 

```css
.nave, .navCat {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 100px;
    padding: 0px 20px;
    padding-left: 60px;
}
```

en el estilo de .navTarget, .navCatTarget, .cerrar-menu se ocultan todos los botones que no serán usados hasta que se active el MediaQuery

```css
.navTarget, .navCatTarget, .cerrar-menu {
    display: none;
    cursor: pointer;
    order: 1;
}
```

a .destacados se le asigna una transición cuando el mouse pase sobre las imágenes

```css
.destacados img{
    max-width: 500px;
    width: 100%;
    transition: 0.3s ease-in-out;
}
.destacados img:hover{
    transform: scale(1.1);
}
```

Se asigna un valor maximo horizontal de la pantalla para que se active la transformación mediante el MediaQuery

```css
@media (max-width: 750px){
```

Se muestran los botones ocultos anteriormente, luego se cambia la disposicion del menu para que sea mas comodo de usa cambiando el sentido del flex con  **flex-direction: column**; se genera una transicion del despliegue de los menús usando **clip-path: circle(150% at top right);** para hacer que sea visible en esa zona y desplegarlo cuando se haga target en el menú **clip-path: circle(0% at top right);** se encarga de quitar la visibilidad de los menús

```css
    .menu, .menuProd{
        position: fixed;
        width: 100%;
        height: 100vh;
        background: #d3d3d3;
        left: 0;
        top: 0;
        display: flex;
        flex-direction: column;
        text-align: center;
        padding: 20px;
        z-index: 1;        
        clip-path: circle(0% at top right);
        transition: clip-path 0.6s;
    }
    .menu:target, .menuProd:target{
        clip-path: circle(150% at top right);
    }    
```

## styCat1.css

Nota: En esta hoja de estilos se reutilizaron algunos estilos, por lo tanto se omitirán

Container será el contenedor de todos los productos de la categoría, se usa gap para generar separación entre cada producto de la categoría; además se genera un background transparent junto con backdrop-filter: blur(8px); para generar un efecto de blur en el fondo de cada producto.

```css
.container{
    display: flex;
    align-items: center;
    padding: 0px 50px;
    gap: 50px;
    border-radius: 10px;
    border: 2px solid gray;
    background: transparent;
    backdrop-filter: blur(8px);
}
```

Se genera el grid que se usara para la disposicion de las imagenes; **grid-template-columns: 20% 80%;** dos columnas con un ancho relativo **grid-template-rows: repeat(4,1fr);** 4 filas que usaran 1 fracción del espacio disponible cada una

```
.vistas{
    margin: 20px;
    display: grid;
    grid-template-columns: 20% 80%;
    grid-template-rows: repeat(4,1fr);
    gap: 15px;
    width: 100%;
    height: 100%;
}
```

En esta seccion se utiliza la imagen del producto como un fondo, de tal manera que cuando se realice :hover a otras imágenes se pueda modificar mas fácilmente la imagen que se presenta como principal; además se hace la distribución de las imagenes con un grid de tal manera que todas las imágenes posean el mismo nivel y poder usar un selector especifico **~** para poder cambiar las propiedades del otro elemento.

**.vistas > .vista1:hover** muestra la ruta y cuando se realiza :hover sobre cada imagen se modifica el background de la imagen principal; esta función se utilizo para las cuatro vistas por producto

```css
.imgPpal{
    background: url('../images/Cat1/producto1/rubik.png') no-repeat center center;
    background-size: cover;
    width: 100%;
    padding: 0;
    margin: 20px;
    grid-column: 2;
    grid-row: 1/span 4;
}
.vistas > .vista1:hover ~ .imgPpal1{
    background: url('../images/Cat1/producto1/vista1.jpg') no-repeat center center;
    background-size: cover;
    width: 100%;
    box-shadow: 10px 10px 10px gray;
}
```

**Nota:** En cada archivo de html adicional para las categorías se llama la hoja de estilos principal de las categorías que es **styCat1.css** y se modifica únicamente las imágenes en las demás que están dadas por **styCat#.css**

## styProd1.css

Nota: En esta hoja de estilos se reutilizaron algunos estilos, por lo tanto se omitirán.

La mayoría de los estilos se configuran de manera muy similar, el cambio se da al usar MediaQuery para cambiar la disposición del grid, puesto que en la vista responsiva las imágenes están dispuestas de una manera diferente.

Adicional a esto se ubica imagen por imagen en las coordenadas del grid correspondiente.

```css
    .vistas{
        margin: 10px;
        display: grid;
        grid-template-columns: repeat(4,1fr);
        grid-template-rows: 80% 20%;
        justify-content: center;
        gap: 15px;
        width: 100%;
        height: 400px;
    }
    .imgPpal {
        width: 100%;
        margin-left: 0;
        height: auto;
        grid-row: 1;
        grid-column: 1/span 4;
    }
    .vistas img{
        width: 100%;
        height: auto;
    }
    .vista1{
        grid-row: 2;
        grid-column: 1;
    }
    .vista2{
        grid-row: 2;
        grid-column: 2;
    }
    .vista3{
        grid-row: 2;
        grid-column: 3;
    }
    .vista4{
        grid-row: 2;
        grid-column: 4;
    }
```

**Nota:** En cada archivo de html adicional para los productos por categoria se llama la hoja de estilos principal de los productos que es **styProd1.css** y se modifica únicamente las imágenes en las demás que están dadas por **styProd#.css**; cada hoja de estilo adicional para los productos contiene la modificación de todas las imágenes de cada categoría, es decir el **#** indica el numero de la categoría que le corresponde.