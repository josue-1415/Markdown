> Marckdown es un lenguaje de marcado.

<!--Comentario-->

<!--Headings(Encabezados)-->
# Titulo h1
## Titulo h2
### Titulo h3
#### Titulo h4
##### Titulo h5
###### Titulo h6

___________________________________________________
## Tipos de textos
<!--Tipos de textos-->
Texto en italica: *texto italica*

Texto en negrita: **Texto**

Texto tachado: ~~tachado~~

___________________________________________________
## Listas:
<!--Listas desordenadas Ul-->
Listas desordenadas:
* Item 1
  * Subitem 1
  * Subitem 2
* Item 2
* Item 3
* Item 4

<!--listas ordenadas li-->
Listas ordenadas:
1. Item 1
2. Item 2
   1. subitem 1
   2. subitem 2
3. Item 3
4. Item 4
___________________________________________________

## Enlaces:

[Repositorio de Marckdown en mi cuenta de github](https://github.com/josue-1415/Markdown.git)

[Repositorio de Marckdown en mi cuenta de github](https://github.com/josue-1415/Markdown.git "My repositorio")

## Citas:

> Esta es una cita

Lineas horizontales

"---"

"___"

## Insertar codigo:

Line de codigo: 

Lina de codigo en javascript `console.log("hola mundo")`

Bloque de codigo:

## Codifo de javascript:

```javascript
var createError = require('http-errors');
var express = require('express');
var path = require('path');
var cookieParser = require('cookie-parser');
var logger = require('morgan');
var expressHbs=require('express-handlebars')
var mongoose=require('mongoose')
var session=require('express-session')
var passport=require('passport')
var flash=require('connect-flash')
var validator=require('express-validator')
//storing session in connect-mongo package
var mongoStore=require('connect-mongo')(session)

var indexRouter = require('./routes/index');
var usersRouter = require('./routes/user'); 

var app = express();

var url = process.env.DATABASE_URL || "mongodb://localhost:27017/shopping21"; 
mongoose.connect(url, { useNewUrlParser: true })
    .then(() => console.log("Connection Successful"))
    .catch(err => console.log(err));
//mongoose.connect('localhost:27017/myEmployee',{useNewUrlParser: true});
let db=mongoose.connection
console.log(db)
db.once('open',function(){
    console.log('connected to mongodb')
})
db.on('error',function(err){
    console.log(err)
})

require('./config/passport')
// view engine setup
app.engine('.hbs',expressHbs({defaultLayout:'layout',extname:'.hbs'}))
app.set('view engine', '.hbs');

app.use(logger('dev'));
app.use(express.json());
app.use(express.urlencoded({ extended: false }));
app.use(validator())
app.use(cookieParser());
app.use(session({
  secret:'mysecret',
  resave:false,
  saveUninitialized:false,
  store:new mongoStore({mongooseConnection:mongoose.connection}),
  cookie:{maxAge:1440*60*1000}
})
)
app.use(flash())
app.use(passport.initialize())
app.use(passport.session())
app.use(express.static(path.join(__dirname, 'public')));

app.use(function(req,res,next){
  //login and session are global variables available to all views file
  res.locals.login=req.isAuthenticated()
  res.locals.session=req.session
  next()
})
app.use('/user', usersRouter);
app.use('/', indexRouter);

// catch 404 and forward to error handler
app.use(function(req, res, next){
  next(createError(404));
});

// error handler
app.use(function(err, req, res, next) {
  // set locals, only providing error in development
  res.locals.message = err.message;
  res.locals.error = req.app.get('env') === 'development' ? err : {};
  // render the error page
  res.status(err.status || 500);
  res.render('error');
});

module.exports = app;
```
## Codigo html:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <h1>hola mundo</h1>
</body>
</html>
```
## Codigo css:

```css
h1{
    color:red;
}
```
## Codigo de python:

```python
print("hola mundo")
```
## Codigo c++:
```c++
#include<iostream>
using namespace std;
int main(){
    cout<<"hola mundo"<<endl;
    return 0;
}
```
---
## Tablas 

 <!--Encabezado-->
| Columna 1 | Columna 2 | Columna 3 |
| --------  | --------  | --------  |
| Valor 1   | Valor 2   | Valor 3   |
| Valor 4   | Valor 5   | Valor 6   |
| Valor 7   | Valor 8   | Valor 9   |
| Valor 10  | Valor 11  | Valor 12  |

## Insertar imagenes:

### cargar imagen desde la web con url:
![alt text](https://images.unsplash.com/photo-1518791841217-8f162f1e1131?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=500&q=60)

![alt text](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Visual_Studio_Code_1.35_icon.svg/2048px-Visual_Studio_Code_1.35_icon.svg.png "Logo de Visual Studio Code" )

### cargar imagen desde la carpeta local:

<div>
<p style = 'text-align:center;'>
<img src="https://pbs.twimg.com/media/EiAAHfoU4AADis4?format=jpg&name=small" alt="JuveYell" width="300px">
</p>
</div>

# Github marckdown

Listas de checkbox:
<!--tareas no realizadas-->
* [ ] Tarea 1
* [ ] Tarea 2
* [ ] Tarea 3
<!--tareas realizadas-->
* [x] Tarea 1
* [x] Tarea 2
* [x] Tarea 3

# Texto matemático LaTeX en marckdown

$$ \textup{La serie geométrica }\sum_{k=0}^\infty \frac{e^{3k+1}}{k\ln 2}$$


```latex    
$$ \textup{La serie geométrica }\sum_{k=0}^\infty \frac{e^{3k+1}}{k\ln 2}$$
```

