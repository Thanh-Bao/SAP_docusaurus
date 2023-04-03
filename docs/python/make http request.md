```python

import requests

response = requests.get("https://jsonplaceholder.typicode.com/todos/10").json()

# {'userId': 1, 'id': 10, 'title': 'illo est ratione doloremque quia maiores aut', 'completed': True}

print(response['title'])

```
