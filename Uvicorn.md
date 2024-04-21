## Initialize web server
```bash
uvicorn filename:app --reload
```
Arguments
- **filename** -> Name of python file (without .py)
- **app** -> Name of the FastAPI object instance
- --**reload** -> Reloads the page automatically after http request