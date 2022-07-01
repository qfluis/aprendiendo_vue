# Aprendiendo Vue
Repo de aprendizaje de Vue.
## Recursos
[Cheat sheet Fernando Herrera](./recursos/vuejs-cheatsheet-fernando-herrera.pdf)

[Presentación Introducción Aina Palacios (IT-Academy)](./recursos/vuejs-itacademy-aina-palacios.pdf)

## Introducción a Vue
Ver ejemplo en [01-bases](./01-bases)
### Uso de Vue con CDN
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