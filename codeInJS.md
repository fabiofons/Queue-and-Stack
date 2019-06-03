# Queue and Stack code
## Queue
```javascript
function NodeQueue(value,ref) {
  this.val = value;
  this.ref = ref;
}

function Queue() {
  this._head = null;
  this._tail = null;
  this._length = 0;
}

Queue.prototype.push = function(value) {
  let element = new NodeQueue(value)
  if(!this._head){
    this._head = element;
    this._tail = element;
  } else {
    this._tail.ref = element;
    this._tail = element
  }
  this._length++;
}

Queue.prototype.dequeue = function() {
  reference = this._head;
  this._head = reference.ref;
  this._length--;
  return reference.val; 
}

Queue.prototype.length = function() {
  return this._length;
}


```


## Stack
```javascript

function NodeStack(value) {
  this.val = value;
  this.ref = null;
}

function Stack() {
  this._head = null;
  this._tail = null;
  this._length = 0;
  this._valNodes = {};
}

Stack.prototype.push = function(value) {
  const node = new NodeStack(value, null);  
  if(!this._head) {
    this._head = node;
    this._tail = node;
    this._valNodes[this._length] = node.val;
  } else {   
    this._tail.ref = node;   
    this._tail = node;
    this._valNodes[this._length] = node.val;
  }  
  this._length++
}


Stack.prototype.length = function() {
  if (this._length >= 0) {
    return this._length;
  } else {
    return 0;
  }
}


Stack.prototype.pop = function() {
  let value;
  if(this._length <= 0){
    value = null;

  } else if(this.length() === 1) { 
    value = this._tail.val;  
    this._head = null;
    this._tail = null;

  } else {
    value = this._tail.val;
    let reference = new NodeStack(this._valNodes[this._length - 2]);
    this._tail = reference;
  }

  this._length--;
  return value;
}
```
