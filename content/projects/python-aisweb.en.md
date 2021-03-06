+++
description = "A Python API Wrapper module for AIS from DECEA (Brazilian's Air Force)"
repository  = "https://github.com/carlosdamazio/pyportugol"
linkTitle   = "Python AISWEB"
slug        = "python-aisweb"
title       = "Python AISWEB"
+++


# Python AISWEB

This is an API Wrapper for the Brazilian Aeronautical Information Service from DECEA's AISWEB system. If you're a developer who wants to use this API and want to check the docs for usage, please contact DECEA (Departamento de Controle do Espaço Aéreo) to get your API Key in https://aisweb.decea.gov.br/.


# Installation
With pip installed, just install the package with it. Simple as that:
```bash
pip install python-aisweb
```

# Usage
```python
from python_aisweb import AISWEB

a = AISWEB('<API_KEY>', '<API_PASS>')

# Response comes in XML by default. If you want JSON responses, do as below:
response = a.<area_code>({'arg_key': 'arg_value'}, method='GET', response_type="JSON")

# The response, when JSON specified, is indented by 4.
print(response)
```
