

# PyTest Cheat Sheet



## Basic PyTest

### Writing and Running Tests

Create a new directory for the project and navigate into it



```bash
cd ~/pytest_example
mkdir -p ~/pytest_example
```

Create `math_operations.py`

```python
# Create a Python script with functions to test
echo 'def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

# math_operations.py
```

And a `test_math_operations.py`:

```python
# Create a test file
echo 'import pytest
from math_operations import add, subtract

def test_add():
    assert add(3, 4) == 7
    assert add(1, 2) == 3

def test_subtract():
    assert subtract(10, 5) == 5
    assert subtract(3, 2) == 1

# test_math_operations.py    
```



Then run `pytest`in that folder. Make a mistake in add and subtract and see what happens...



## PyTest with Fixtures

Create a new file `test_math_operations_with_fixtures.py`.

### Using Fixtures for Setup and Teardown

```python

# Create a new test file with fixtures
import pytest
from math_operations import add, subtract

@pytest.fixture
def numbers():
    a = 10
    b = 5
    return (a, b)

def test_add(numbers):
    a, b = numbers
    assert add(a, b) == 15

def test_subtract(numbers):
    a, b = numbers
    assert subtract(a, b) == 5
' > test_math_operations_with_fixtures.py

# Run the tests

```



Run tests with `pytest test_math_operations_with_fixtures.py`. Fixtures help us create persistent things, like mock databases and data, which are used in multiple tests.



## PyTest using mark.parameterize

### Using Parameterize to Run Tests with Multiple Sets of Data

Create a file `test_math_operations_parametrize.py`:

```python
import pytest
from math_operations import add, subtract

@pytest.mark.parametrize("a, b, expected", [
    (3, 4, 7),
    (1, 2, 3),
    (-1, -1, -2),
    (0, 0, 0)
])
def test_add(a, b, expected):
    assert add(a, b) == expected

@pytest.mark.parametrize("a, b, expected", [
    (10, 5, 5),
    (3, 2, 1),
    (-1, -1, 0),
    (0, 0, 0)
])
def test_subtract(a, b, expected):
    assert subtract(a, b) == expected


# Run the tests
```

Run with `pytest test_math_operations_parametrize.py`.

To run all the tests just do `pytest`.

## pytests-mock

You need to install the appropriate mocks library. For example for requests you install `requests` and `requests-mock`.

### Creating a Simple Function that Makes a Request

```bash
# Create a new directory for the project and navigate into it
mkdir -p ~/pytest_mocks_example
cd ~/pytest_mocks_example
```

Now create file `wiki_fetcher.py`:

```python
# Create a Python script with a function to fetch data from Wikipedia
import requests

def fetch_wikipedia_page(page):
    url = f"https://en.wikipedia.org/api/rest_v1/page/summary/{page}"
    response = requests.get(url)
    return response.json()

```

### Writing Tests with Mocks

Create `test_wiki_fetcher.py`:

```python

# Create a test file to mock the requests to Wikipedia
import pytest
import requests
import requests_mock
from wiki_fetcher import fetch_wikipedia_page

def test_fetch_wikipedia_page(requests_mock):
    page = "Python_(programming_language)"
    url = f"https://en.wikipedia.org/api/rest_v1/page/summary/{page}"
    
    # Mock response data
    mock_response = {
        "title": "Python (programming language)",
        "extract": "Python is an interpreted, high-level and general-purpose programming language."
    }
    
    # Mock the GET request to Wikipedia
    requests_mock.get(url, json=mock_response)
    
    response = fetch_wikipedia_page(page)
    
    assert response["title"] == "Python (programming language)"
    assert response["extract"] == "Python is an interpreted, high-level and general-purpose programming language."

# Run the tests

```

Test via `pytest test_wiki_fetcher.py`.

### Using a Fixture for Mocking

Create `test_wiki_fetcher_with_fixture.py`:

```python
# Create a test file with a fixture to mock requests
import pytest
import requests
import requests_mock
from wiki_fetcher import fetch_wikipedia_page

@pytest.fixture
def mock_requests(requests_mock):
    page = "Python_(programming_language)"
    url = f"https://en.wikipedia.org/api/rest_v1/page/summary/{page}"
    
    # Mock response data
    mock_response = {
        "title": "Python (programming language)",
        "extract": "Python is an interpreted, high-level and general-purpose programming language."
    }
    
    # Mock the GET request to Wikipedia
    requests_mock.get(url, json=mock_response)

def test_fetch_wikipedia_page_with_fixture(mock_requests):
    page = "Python_(programming_language)"
    response = fetch_wikipedia_page(page)
    
    assert response["title"] == "Python (programming language)"
    assert response["extract"] == "Python is an interpreted, high-level and general-purpose programming language."


# Run the tests

```

Now run the test with `pytest test_wiki_fetcher_with_fixture.py`.