# vue-web-form

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

## View Model and Two Way Data Binding
1. `v-model=` will connect and update to the data property email  
```
    <form>
        <label>Email: </label> 
        <input type="email" required v-model="email">
    </form>
```

2. Data property is updated by the v-model
```
    data() {
        return {
            email: ''
        }
    }
```
3. Either output the data property OR use a method to connect to the data property
```
{{ email }} or `this.email = ...`
```
---
