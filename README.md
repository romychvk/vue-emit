# vue-emit

Minimal Vue emit example
========================

Это простейший пример использования `emit` — способа передачи значения переменной из дочернего компонента Vue в родительский компонент.

В файле дочернего компонента `childComponent.vue` добавляем в шаблоне компонента вызов функции `currentComponentFunction` при клике по кнопке, а в самой функции устанавливаем emit таким образом:

```js
this.$emit("customNamedEmit", "Button clicked");
```

Здесь `customNamedEmit` — имя emit'а, через которое мы получим значение `Button clicked` в родительском компоненте. (В коде к значению добавлен счетчик кликов — это сделано для наглядности при тестировании в браузере).

В файле родительского компонента (не обязательно компонента, это может быть и корень всего приложения) `parentComponent.vue` мы вставляем в шаблон тэг самого компонента  `<child-component>`, и к нему добавляем остлеживание нашего emit'а: 

```js
@customNamedEmit="changeSubmitStatus"
```

При клике по кнопке выполнится функция внутри дочернего компонента, сформирует значение и передаст его в `customNamedEmit`. В родителе emit передаст это значение в функцию `changeSubmitStatus` в переменную `value`:

```js
methods: {
  changeSubmitStatus (value) {
    console.log(value);
    this.buttonClickedStatus = value;
  }
}
```

Все, теперь сформированное в дочернем компоненте значение доступно в родителе.

## Project setup

```
npm install
npm run serve
```
