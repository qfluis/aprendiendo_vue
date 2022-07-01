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
<script src="https://unpkg.com/vue@3"></script>

<div id="app">{{ message }}</div>

<script>
  const { createApp } = Vue

  createApp({
    data() {
      return {
        message: 'Hello Vue!'
      }
    }
  }).mount('#app')
</script>
```