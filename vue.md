# binding textfield
use v-model
```
<input type="text" id="name" name="name" v-model="deckName"> {{ deckName.length }} characters
 <textarea id="description" name="description" v-model="deckDescription"></textarea> {{ 200 - deckDescription.length }} left
 ```

## show on off instead of true / false
<input v-model="reverse" true-value="on" false-value="off" type="checkbox" id="reverse" value="reverse">

- array
```
<input v-model="options" type="checkbox" id="reverse" value="reverse">
<input v-model="options" type="checkbox" id="time_limit" value="time_limit">
```

```
return {
deckName: 'Vue.js Fundamentals',
deckDescription: 'Core concepts and directives for working with Vue.js',
reverse: false,
options: []
};
```
