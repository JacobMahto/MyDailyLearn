#### Understanding Asynchronous JavaScript — the Event Loop 
  

- Heap -> Memory allocation 
- Stack -> execution contexts
- Browser, web api
- callback queue
- Event Loop

[Philip Roberts Video](https://www.youtube.com/watch?v=8aGhZQkoFbQ)

#### Example 1:

```js
function main(){
  console.log('A');
  setTimeout( () => {
    console.log('B');
  }, 1000); // first 1000, then try with 0 sec
	console.log('C');
}
main();
//	Output
//	A
//	C
//  B
```

[Ref](https://medium.com/front-end-hacking/javascript-event-loop-explained-4cd26af121d4)

#### Example 2:

```js
function main(){
  console.log('A');
  setTimeout(
    function exec(){ console.log('B'); }
  , 0);
  runWhileLoopForNSeconds(3);
  console.log('C');
}
main();
function runWhileLoopForNSeconds(sec){
  let start = Date.now(), now = start;
  while (now - start < (sec*1000)) {
    now = Date.now();
  }
}
// Output
// A
// C

```

#### Example 3: Callback hell
```js
doA(() => {           |   first(() => {
  doB();              |     third();
  doC(() => {         |     fourth(() => {
    doD()             |       sixth();
  });                 |     });
  doE();              |     fifth()
});                   |   })
doF();                |   second();
```

[Event loop in MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop)
