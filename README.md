# StudentAgenda

![](https://www.gravatar.com/avatar/dad922129a743e062ddfd7d3c7c9016b?d=https://repl.it/public/images/evalbot/evalbot_39.png&s=256)

## Descripción
**Agenda de estudiante en Phyton**
La agenda permite guardar el nombre del estudiante y su calificación, al igual que genera un id automaticamente basado en el largo del arreglo.
Las funciones son las siguientes:
- Listar (*list*) :  

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
- Guardar (*save*) : 
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
- Borrar (*delete*):
```python

```

- Salir (*exit*):
```python

```
