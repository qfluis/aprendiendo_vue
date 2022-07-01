# Aprendiendo Vue
Repo de aprendizaje de Vue.
## Recursos
[Cheat sheet Fernando Herrera](./recursos/vuejs-cheatsheet-fernando-herrera.pdf)

[Presentación Introducción Aina Palacios (IT-Academy)](./recursos/vuejs-itacademy-aina-palacios.pdf)

## Introducción a Vue
Ver ejemplo en [01-bases](./01-bases)
### Uso de Vue con CDN
En fichero `.html` añadir:
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
- Entre `{{ }}` podemos añadir variables y algunas expresiones javascript
- En `data(){ return { variable:valor }}` introducimos las variables