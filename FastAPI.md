![FastAPI](https://fastapi.tiangolo.com/img/logo-margin/logo-teal.png)

#### Default Data

```json
dict_students = {
    1:
    {
        "name": "Joseph",
        "age": 23,
        "location": "NYC"
    },
    2:
    {
        "name": "Jake",
        "age": 22,
        "location": "Saratoga"
    }
}
```

## Initialize Object - "_app_"

```python
app = FastAPI()
this
```

_Used along with the '@' to decorate requests_

### HTTP Commands

```Python
@app.get("/get-student") # Retreives information
@app.post("make-student") # Sends information
@app.put("update-student") # Updates infomration
@app.delete("delete-student") # Deltes information
```

## Paths

#### Import

```python
from typing import Annotated
from fastapi import Path
```

### Path Parameters

```Python
@app.get("/get_student/{student_id}")
def get_student(student_id: int):
	return students[student_id]
```

- **{}** are used to interpolate **dynamic** variables
- interpolated variable must be includes as an **input** to the function
- **Type hinting** must be used
  Used to better document parameters used in the path. Annotated module allows for addition of metadata to type hints

#### Path Parameters

- Default -> Used if you want to make the parameter optional
- Title -> Adds a one liner to explain the parameter
- Description -> Allows for more information to be added
- gt(han)/lt & ge(qual)/le-> Specify validation values

#### Example

```Python

```

## Queries

#### Import

```python
from typing import Annotated
from fastapi import Query
```

### Query Parameters

```python
@app.get("/student_query")
def get_student_by_name(name: str):
	if res:=[{id:v} for id, v in dict_students.items() if v['name'] == name]:
		return res[0]
	else:
		return {"Data": "Not Avaliable"}
```

- Does not require any interpolation in the path
- Utilized

### Posts

You will need a class to define structure to be used

```python
class Student(BaseModel):
    name: str
    age: int
    location: str
```

Example

```python
@app.post("/create_student")
def create_student(student: Student):
    dict_students[new_id := (max(dict_students) + 1)] = student
    return HTTPException(201, detail=f"id:{new_id}\nValues:{student}")
```

### Puts

You will need a new class that allows attributes to be optional

```python
class UpdatedStudent(BaseModel):
    name: Optional[str] = None
    age: Optional[int] = None
    location: Optional[str] = None
```

Example

```python
@app.put("/update_student")
def update_student(
    student_id: Annotated[int, Query(description="The id of the student to update")],
    student: UpdatedStudent,
):
    if data := dict_students.get(student_id):
        update_data = student.dict(exclude_unset=True)
        for var_name, value in update_data.items():
            if value:
                data[var_name] = value
        dict_students[student_id] = data
        return dict_students[student_id]
    raise HTTPException(status_code=404, detail="There is no student")
```

### Deletes

```python
@app.delete("/delete_student")
def delete_student(
    student_id: Annotated[int, Query(
        description="Student ID of student to delete")]
):
    if student_id in dict_students:
        del dict_students[student_id]
        return HTTPException(
            200, detail=f"Student id {student_id} successfully deleted."
        )
    return HTTPException(404, detail=f"Student id {student_id} was not found.")
```

### Running API

Utilize [[Uvicorn]] to run bash commands


### Title
