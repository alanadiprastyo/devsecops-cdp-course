Use Pylint for Code Quality Analysis
================================

Learn how to run Code Quality scans on Python code using Pylint
------------------------------------------------

In this scenario, you will learn how to run code quality scan on Python source code.

You will need to download the source code, install the tool, run the scan on the code and analyze the results of Pylint.

Download the source code
----------

We will do all the exercises locally first in DevSecOps-Box, so let’s start the exercise.

First, we need to download the source code of the project from our git repository.

```
git clone https://gitlab.practical-devsecops.training/pdso/django.nv webapp
cd webapp
```

Install Pylint Tool
----------

> Pylint is a static code analysis tool for Python which looks for programming errors, helps enforce a coding standard, sniffs out code smells and offers simple refactoring suggestions.
> 
> You can find more details about the project at https://github.com/PyCQA/pylint.

Let’s install pylint on the system to perform static analysis.

```
pip3 install pylint
pylint --help
```

Run Pylint
----------

We will run a simple pylint scan on our project:

```
pylint taskManager/*.py
```
output
```
************* Module taskManager
taskManager/__init__.py:1:0: C0103: Module name "taskManager" doesn't conform to snake_case naming style (invalid-name)
************* Module taskManager.forms
taskManager/forms.py:18:0: E0401: Unable to import 'django' (import-error)
taskManager/forms.py:19:0: E0401: Unable to import 'django.contrib.auth.models' (import-error)
taskManager/forms.py:73:4: C0115: Missing class docstring (missing-class-docstring)
taskManager/forms.py:73:4: R0903: Too few public methods (0/2) (too-few-public-methods)
taskManager/forms.py:71:0: R0903: Too few public methods (0/2) (too-few-public-methods)
taskManager/forms.py:78:0: R0903: Too few public methods (0/2) (too-few-public-methods)
taskManager/forms.py:84:0: R0903: Too few public methods (0/2) (too-few-public-methods)
taskManager/forms.py:18:0: C0411: third party import "from django import forms" should be placed before "from taskManager.models import P
roject, Task" (wrong-import-order)
taskManager/forms.py:19:0: C0411: third party import "from django.contrib.auth.models import User" should be placed before "from taskMana
ger.models import Project, Task" (wrong-import-order)
************* Module taskManager.models
taskManager/models.py:1:0: C0114: Missing module docstring (missing-module-docstring)
taskManager/models.py:17:0: E0401: Unable to import 'django.contrib.auth.models' (import-error)
taskManager/models.py:19:0: E0401: Unable to import 'django.utils' (import-error)
taskManager/models.py:20:0: E0401: Unable to import 'django.db' (import-error)
taskManager/models.py:23:0: C0115: Missing class docstring (missing-class-docstring)
taskManager/models.py:23:0: R0903: Too few public methods (0/2) (too-few-public-methods)
taskManager/models.py:29:0: C0115: Missing class docstring (missing-class-docstring)
taskManager/models.py:45:4: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/models.py:48:4: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/models.py:51:4: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/models.py:61:0: C0115: Missing class docstring (missing-class-docstring)
taskManager/models.py:78:4: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/models.py:81:4: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/models.py:84:4: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/models.py:88:0: C0115: Missing class docstring (missing-class-docstring)
taskManager/models.py:88:0: R0903: Too few public methods (1/2) (too-few-public-methods)
taskManager/models.py:99:0: C0115: Missing class docstring (missing-class-docstring)
taskManager/models.py:99:0: R0903: Too few public methods (1/2) (too-few-public-methods)
************* Module taskManager.settings
taskManager/settings.py:1:0: C0114: Missing module docstring (missing-module-docstring)
************* Module taskManager.taskManager_urls
taskManager/taskManager_urls.py:1:0: C0103: Module name "taskManager_urls" doesn't conform to snake_case naming style (invalid-name)
taskManager/taskManager_urls.py:1:0: C0114: Missing module docstring (missing-module-docstring)
taskManager/taskManager_urls.py:15:0: E0401: Unable to import 'django.conf.urls' (import-error)
************* Module taskManager.tests
taskManager/tests.py:1:0: C0114: Missing module docstring (missing-module-docstring)
taskManager/tests.py:3:0: E0401: Unable to import 'django.utils' (import-error)
taskManager/tests.py:4:0: E0401: Unable to import 'django.test' (import-error)
taskManager/tests.py:8:0: C0115: Missing class docstring (missing-class-docstring)
taskManager/tests.py:6:0: W0611: Unused User imported from models (unused-import)
************* Module taskManager.urls
taskManager/urls.py:1:0: C0114: Missing module docstring (missing-module-docstring)
taskManager/urls.py:15:0: E0401: Unable to import 'django.conf.urls' (import-error)
taskManager/urls.py:16:0: E0401: Unable to import 'django.contrib' (import-error)
************* Module taskManager.views
taskManager/views.py:796:0: C0301: Line too long (107/100) (line-too-long)
taskManager/views.py:802:0: C0301: Line too long (166/100) (line-too-long)
taskManager/views.py:1:0: C0114: Missing module docstring (missing-module-docstring)
taskManager/views.py:20:0: E0401: Unable to import 'django.shortcuts' (import-error)
taskManager/views.py:21:0: E0401: Unable to import 'django.http' (import-error)
taskManager/views.py:22:0: E0401: Unable to import 'django.utils' (import-error)
taskManager/views.py:23:0: E0401: Unable to import 'django.template' (import-error)
taskManager/views.py:24:0: E0401: Unable to import 'django.db' (import-error)
taskManager/views.py:26:0: E0401: Unable to import 'django.views.decorators.csrf' (import-error)
taskManager/views.py:28:0: E0401: Unable to import 'django.contrib' (import-error)
taskManager/views.py:29:0: E0401: Unable to import 'django.contrib.auth' (import-error)
taskManager/views.py:30:0: E0401: Unable to import 'django.contrib.auth' (import-error)
taskManager/views.py:31:0: E0401: Unable to import 'django.contrib.auth.models' (import-error)
taskManager/views.py:32:0: E0401: Unable to import 'django.contrib.auth' (import-error)
taskManager/views.py:39:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:48:12: R1705: Unnecessary "else" after "return" (no-else-return)
taskManager/views.py:74:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:83:12: R1705: Unnecessary "else" after "return" (no-else-return)
taskManager/views.py:112:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:126:12: R1705: Unnecessary "else" after "return" (no-else-return)
taskManager/views.py:155:12: R1705: Unnecessary "else" after "return" (no-else-return)
taskManager/views.py:170:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:177:8: R1705: Unnecessary "else" after "return" (no-else-return)
taskManager/views.py:174:8: W0612: Unused variable 'proj' (unused-variable)
taskManager/views.py:206:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:206:13: W0613: Unused argument 'request' (unused-argument)
taskManager/views.py:220:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:224:4: R1705: Unnecessary "else" after "return" (no-else-return)
taskManager/views.py:220:25: W0613: Unused argument 'request' (unused-argument)
taskManager/views.py:240:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:242:4: R1705: Unnecessary "else" after "return" (no-else-return)
taskManager/views.py:273:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:278:4: R1705: Unnecessary "else" after "return" (no-else-return)
taskManager/views.py:288:29: R1719: The if expression can be replaced with 'test' (simplifiable-if-expression)
taskManager/views.py:299:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:299:16: W0613: Unused argument 'request' (unused-argument)
taskManager/views.py:311:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:311:18: W0613: Unused argument 'request' (unused-argument)
taskManager/views.py:322:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:324:4: R1705: Unnecessary "else" after "return" (no-else-return)
taskManager/views.py:350:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:354:4: R1705: Unnecessary "else" after "return" (no-else-return)
taskManager/views.py:376:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:376:19: W0613: Unused argument 'request' (unused-argument)
taskManager/views.py:385:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:390:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:398:16: R1705: Unnecessary "else" after "return" (no-else-return)
taskManager/views.py:421:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:466:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:479:4: R1705: Unnecessary "else" after "return" (no-else-return)
taskManager/views.py:491:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:511:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:515:4: R1705: Unnecessary "else" after "return" (no-else-return)
taskManager/views.py:530:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:531:4: R1705: Unnecessary "else" after "return" (no-else-return)
taskManager/views.py:554:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:560:4: R1705: Unnecessary "else" after "return" (no-else-return)
taskManager/views.py:581:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:581:16: W0613: Unused argument 'request' (unused-argument)
taskManager/views.py:593:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:593:26: W0613: Unused argument 'project_id' (unused-argument)
taskManager/views.py:628:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:640:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:655:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:661:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:678:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:684:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:685:4: R1705: Unnecessary "else" after "return" (no-else-return)
taskManager/views.py:703:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:711:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:740:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:780:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:790:0: R1721: Unnecessary use of a comprehension (unnecessary-comprehension)
taskManager/views.py:791:16: C0103: Variable name "x" doesn't conform to snake_case naming style (invalid-name)
taskManager/views.py:814:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:837:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:18:0: W0611: Unused import codecs (unused-import)
************* Module taskManager.wsgi
taskManager/wsgi.py:13:0: E0401: Unable to import 'django.core.wsgi' (import-error)
taskManager/wsgi.py:13:0: C0413: Import "from django.core.wsgi import get_wsgi_application" should be placed at the top of the module (wrong-import-position)

------------------------------------------------------------------
Your code has been rated at 6.37/10 (previous run: 6.37/10, +0.00)
```

Seems there’s alot which can be improved in this code.

If you want to save the output as a JSON file, you can use -f json.

```
pylint taskManager/*.py -f json | tee output.json
```
The output of the pylint tool will be saved in JSON formatted file output.json.

If you open the file, you can see that the pylint has found several errors such as Missing function/method, unused argument, and so on.

However, there seems to be quite a bit of noise(false positives) in the results.

Reduce False Positives
----------

As we have seen in bandit exercise, we can reduce false positives using .pylintrc file and direct the pylint to skip specific checks during the scan.

Let’s create the file using the nano text editor and start adding the content.

```
nano .pylintrc
.....
[MASTER]
disable=missing-module-docstring,import-error
```
You can save the file using Ctrl+O and exit the editor using Ctrl+X key combination. Let’s run the scan once again to see what’s changed.

```
pylint taskManager/*.py
```

output
```
...[SNIP]...
taskManager/views.py:740:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:780:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:790:0: R1721: Unnecessary use of a comprehension (unnecessary-comprehension)
taskManager/views.py:791:16: C0103: Variable name "x" doesn't conform to snake_case naming style (invalid-name)
taskManager/views.py:814:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:837:0: C0116: Missing function or method docstring (missing-function-docstring)
taskManager/views.py:18:0: W0611: Unused import codecs (unused-import)
************* Module taskManager.wsgi
taskManager/wsgi.py:13:0: C0413: Import "from django.core.wsgi import get_wsgi_application" should be placed at the top of the module (wrong-import-position)

------------------------------------------------------------------
Your code has been rated at 8.41/10 (previous run: 6.37/10, +2.03)
```

Right now, our code is rated at 8.41/10, earlier it was previous run: 6.37/10

That’s a good jump from the quality perspective .pylintrc

