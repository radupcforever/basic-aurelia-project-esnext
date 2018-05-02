# basic-aurelia-project-esnext

The Aurelia quick start guide from https://aurelia.io/docs/tutorials/creating-a-todo-app/ contains some code snippets that are not working if you choose ESNext as a languange

todo.js

```
    export class Todo {
          done = false;

          constructor(public description: string) { }
    }

```

should be

```
    export class Todo {
        constructor(description) {
            this.description = description;
            this.done = false;
        }
    }

```

app.js

```
    import {Todo} from './todo';

    export class App {
      heading = "Todos";
      todos: Todo[] = [];
      todoDescription = '';

      addTodo() {
        if (this.todoDescription) {
          this.todos.push(new Todo(this.todoDescription));
          this.todoDescription = '';
        }
      }

      removeTodo(todo) {
        let index = this.todos.indexOf(todo);
        if (index !== -1) {
          this.todos.splice(index, 1);
        }
      }
    }
    
```

should be

```
    import { Todo } from './todo';

    export class App {
      constructor() {
        this.heading = "Todos";
        this.todos = [];
        this.todoDescription = '';
      }

      addTodo() {
        if (this.todoDescription) {
          this.todos.push(new Todo(this.todoDescription));
          this.todoDescription = '';
        }
      }

      removeTodo(todo) {
        let index = this.todos.indexOf(todo);
        if (index !== -1) {
          this.todos.splice(index, 1);
        }
      }
    }
    
```

main.js

```
    import {Aurelia} from 'aurelia-framework';

    export function configure(aurelia: Aurelia) {
      aurelia.use.basicConfiguration();
      aurelia.start().then(() => aurelia.setRoot());
    }
    
```

should be

```
    import { Aurelia } from 'aurelia-framework';

    export function configure(aurelia) {
      aurelia.use.basicConfiguration();
      aurelia.start().then(() => aurelia.setRoot());
    }
    
```

This repo contains the modified content of basic-aurelia-project.
