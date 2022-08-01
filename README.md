# StudentAgenda

![](https://www.gravatar.com/avatar/dad922129a743e062ddfd7d3c7c9016b?d=https://repl.it/public/images/evalbot/evalbot_39.png&s=256)

## Descripción
**Agenda de estudiante en Phyton**
La agenda permite guardar el nombre del estudiante y su calificación, al igual que genera un id automaticamente basado en el largo del arreglo.
Las funciones son las siguientes:
###Listar (*list*) :  
Muestra todos los alumnos registrados. Lo primero que se hace es leer el archivo .JSON con la instrucción open, después se almacena el resultado en una variable llamada "students", verificamos el largo de arreglo de los estudiantes que sea igual a 0 y si es igual a 0 mostramos el mensaje "Nothing to see here, son. Keep walking\n\n". De no mostrar el mensaje no ejecuta la siguiente instrucción, posteriormente recorre el arreglo de estudiantes y muestra los resultados con la instrucción print.
```python
def read_students():
    with open("students.json", "r") as students_json:
        students = json.load(students_json)
        if len(students) == 0:
          print("Nothing to see here, son. Keep walking\n\n")
          return
        for student in students:
          print(student["id"] + ".- \n Name: " + student["name"] + "\n Score:" + student["score"] + "\n________________________")
```
### Guardar (*save*) : 
Guarda todos los alumnos registrados. Lo primero que se hace es leer el archivo .JSON con la instrucción open, después se almacena el resultado en una variable llamada "students". Se crea una variable llamada name que almacena la entrada del usuario del nombre, posterior la variable score que almacena la calificación del estudiante y el id se almacenará automaticamente de acuerdo al largo del arreglo de students sumandole 1 para evitar enlaces. Students mostrará al codificador el objeto student que se va a adjuntar (append), con la instrucción open se va a almacenar al resultado en el archivo .JSON.
```python
def save_student():
    with open("students.json", "r") as students_json:
     students = json.load(students_json)  
     name = input('Student\'s name?\n')
     score = input('Student\'s score?\n')
     id = str(len(students) + 1)
     student = {"name": name, "score": score, "id": id}
     students.append(student)
    with open("students.json", "w") as students_json:
      json.dump(students, students_json)
```
### Borrar (*delete*):
Para borrar a un estudiante se inicializa la varible con indice 0 para cuando se ejecute el programa saber cuantos alumnos estan registrados.  Lo primero que se hace es leer el archivo .JSON con la instrucción open, después se almacena el resultado en una variable llamada "students". Se crea una variable llamada id en donde el usuario introduce el id a borrar. En la siguiente instrucción se imprime el id introducido y luego se recorre el arreglo students en donde se va a verificar si el id existe dentro del archivo .JSON y en caso de no ser así le va a aumentar un 1 a la variable indice.
```python
def delete_student():
    indice = 0
    with open("students.json", "r") as students_json:
      students = json.load(students_json)
      id = input('Id to Delete\n')
      print("Indice: " + id)
      for student in students:
        print(student['id'] == id)
        if student['id'] == id:
          students.pop(indice)
          with open("students.json", "w") as students_json:
            json.dump(students, students_json)
          return
        indice += 1
```
### Salir (*exit*):
Si la variable seleccionada es salir, el usuario verá un mensaje de salida. La función print bye sería ejecutada al hacer la elección y con la instrucción break se rompe el ciclo while del cuerpo del codigo. En caso de no ser así, ejecutará la instrucción seleccionada.
```python
         if selected == "exit":
            print_bye()
            break
          else:
            execute(selected)
```
### Función principal
La función principal imprime el menú de opciones basado en un arreglo unidimensional con 4 string, donde el usuario elige una opción. Se inicia un ciclo llamado while que inicialmente va a ser infinito (esto no es recomendado) se imprimiran las opciones con la opción print y se almacenará en la variable selected la palabra introducida por el usuario. Se verificará si la palabra introducida existe dentro del arreglo guardado en options, si está almacenada se va a ejecutar la función de salir, explicada anteriormente, en caso contrario se va a almacenar en la variable again y si el usuario quiere continuar (y) o no (n), si el usuario escribe "yes" o (y) que el programa continue, de no ser así saldra del programa con un mensaje de despedida. 
```python
def get_options():
    options = ['list', 'save', 'delete', 'exit']
    print("Choose an option")

    while True:
      print("*___________________________*")
      selected = input(' | '.join(options) + '\n\n>')
      if selected in options:
          if selected == "exit":
            print_bye()
            break
          else:
            execute(selected)
      else:
          print("Invalid option")
          print("> ")
      again = input('Continue? Type yes (y) or not(n) \n >')
      if again == 'yes' or again == 'y':
        continue
      else:
        print_bye()
        break
```
