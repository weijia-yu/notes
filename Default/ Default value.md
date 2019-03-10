# || Default value

```js
function eatFruit (fruit) {
    fruit = fruit || "strawberry";
    ...
}
```


```js
function eatFruit (fruit) {
    if (fruit === undefined) {
        fruit = "strawberry";
    }
    ...
}```