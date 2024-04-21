
> [!Abstract]
> Used to work with file and folder paths

<a href="https://docs.python.org/3/library/pathlib.html">
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/Python-logo-notext.svg/1920px-Python-logo-notext.svg.png" alt = "Python Logo" width="50" height="50">
</a>

## Path
Class used to cast a string to a Path object. Many methods involving Path can interact with non Path objects because it will return a Path object.

```python
from pathlib import Path

string_path = "/Users/jbokan/data"
path = Path(string_path)
```

### Joining Paths
Usage of the forward-slash "/" will append the path and create a new Path object. This operation can be chained.
```python
full_path = path / 'user' / 'demographics' / 'fy20q1.csv'
```

### Useful Path methods
| Method | Parameters | Purpose | Return Type |
| ---- | ---- | ---- | ---- |
| Path.exists() |  | Check if path exists on host computer | Bool |
| Path.is_file() |  | Check if path is to a regular file | Bool |
| Path.is_dir() |  | Check if path is to a regular directory | Bool |
| Path.glob() | pattern (regexp) | Returns files and directories matching pattern  | List/Tuple |
|  |  |  |  |