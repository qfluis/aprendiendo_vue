# Aprendiendo Vue
Repo de aprendizaje de Vue.
## Recursos
[Cheat sheet Fernando Herrera](./recursos/vuejs-cheatsheet-fernando-herrera.pdf)

[Presentación Introducción Aina Palacios (IT-Academy)](./recursos/vuejs-itacademy-aina-palacios.pdf)

## Introducción a Vue
Ver ejemplo en [01-bases](./01-bases)
## Instalaciones
- Node JS
- Vue/cli (`npm install -g @vue/cli`, `vue --version`)
- Vetur. Extensión vue para VSC.
- Typescript importer. Extensión VSC. Ayuda con las autoimportaciones.
- Vue.js devtools, extensión Chrome.


### Uso de Vue con CDN y Options api
En fichero `index.html`:
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vue.js Intro</title>
    <script src="https://unpkg.com/vue@next"></script>
</head>
<body>    
    <!-- Control absoluto de este DIV -->
    <div id="myApp">
        <h1>Batman quotes  <small>{{ newQuote }}</small> </h1>
        <input
          type="text"
          v-model="newQuote"
          v-on:keypress.enter="addQuote">
        <hr>       
        <ul>
            <li v-for="({ quote, author }, index) in quotes">
                <span>{{ index + 1 }} - {{ quote }}</span>
                <!-- <blockquote v-if="author">-{{ author }}</blockquote> -->
                <blockquote v-show="false">-{{ author }}</blockquote>
            </li>
        </ul>
    </div>    
    <script src="app.js"></script>
</body>
</html>
```
En `app.js`:
```
const quotes = [
    { quote: 'The night is darkest just before the dawn. And I promise you, the dawn is coming.', author: 'Harvey Dent, The Dark Knight' },
    { quote: 'I believe what doesn’t kill you simply makes you, stranger.', author: 'The Joker, The Dark Knight' },
    { quote: 'Your anger gives you great power. But if you let it, it will destroy you… As it almost did me', author: 'Henri Ducard, Batman Begins' },
    { quote: 'You either die a hero or live long enough to see yourself become the villain.', author: 'Harvey Dent, The Dark Knight' },
    { quote: 'If you’re good at something, never do it for free.', author: 'The Joker, The Dark Knight' },
    { quote: 'Yes, father. I shall become a bat.', author: 'Bruce Wayne/Batman, Batman: Year One' },
]
const app = Vue.createApp({ 
    data() {
        return {
            quotes,
            newQuote: 'Hola mundo'
        }
    },
    methods: {
        addQuote() {

            this.quotes.unshift({
                quote: this.newQuote
            })
        }
    }    
})

app.mount('#myApp')
```
- Entre `{{ }}` podemos añadir variables y algunas expresiones javascript
- En `data(){ return { variable:valor }}` introducimos las variables
- En `methods: { nombreMetodo(){...} }` introducimos los métodos
- Si en un input añadimos `v-model="variable"`, hacemos 2-ways data binding (lo que se actualiza por js se muestra en input y lo que se actualiza en el input se actualiza en js +-)
- `v-on:keypress.enter="funcion"`, v-on nos permite, trabajar con eventos, por defecto la funcion recibe el evento (no hace falta especificarlo). Si hubiese que enviar algún parámetro mas se pondría de la siguiente manera: `v-on:keypress.enter="function(param, $event)"`.`v-on`
- `v-for="({ quote, author }, index) in quotes"`, permite hacer un for en el template html.
- `v-if="author"` y `v-show="condicion"`, muestran un contenido según la condición. Tienen algunas diferencias, la principal es que v-show oculta por css y v-if no genera el contenido. 
### Crear proyecto con Vue cli
- `vue create nombreProyecto`, crea un proyecto con Vue.
- `npm run serve`, para iniciar servidor.

