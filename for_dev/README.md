# Tools for development

## Python Scripts
There are some python scripts to test the addon.

- `regist_without_installing.py`: Script to use the addon without installing it in Blender.
- `test.py`: Script to check if the addon can reconstract .uasset files.
- `lint.py`: Script to run pylint

## Flake8
[Flake8](https://flake8.pycqa.org/en/latest/) is a tool for style guide enforcement.<br>
It will check if you are following [PEP8](https://peps.python.org/pep-0008/).<br>
Install it with `pip install flake8`.<br>
Then, type `flake8` in `./Blender-Uasset-Addon`.<br>
You should get no messages from flake8.

## pydocstyle
[pydocstyle](http://www.pydocstyle.org/en/stable/) is a tool for docstring style enforcement.<br>
It will check if you are following [Google Python Style Guide](https://google.github.io/styleguide/pyguide.html) for docstrings.<br>
Install it with `pip install pydocstyle`.<br>
Then, type `pydocstyle` in `./Blender-Uasset-Addon`.<br>
You should get no messages from pydocstyle.

## Pylint
[Pylint](https://pylint.pycqa.org/en/latest/) is a static code analyser.<br>
It can rate your scripts.<br>
Install it with `pip install pylint`.<br>
Then, type `python for_dev\lint.py --path=addons\blender_uasset_addon` in `./Blender-Uasset-Addon`.<br>
You will get results like `PyLint Passed | Score:...`.<br>
The score should be more than 7.<br>

## pytest-blender
[pytest-blender](https://github.com/mondeja/pytest-blender) is a pytest plugin for Blender testing.<br>
You can use bpy with pytest.<br>
First, install requirements in your python environment like this.<br>

```
pip install pytest pytest-blender pytest-cov
```

Then, install pytest and pytest-cov in Blender's python environment like this.<br>
```
REM This is for Windows. See pytest-blender's document for linux and mac.
set BLENDER=C:\Program Files\Blender Foundation\Blender 3.0
set PYTHON_PATH=%BLENDER%\3.0\python\bin\python.exe
set SITE_PACK=%BLENDER%\3.0\python\lib\site-packages

"%PYTHON_PATH%" -m ensurepip
"%PYTHON_PATH%" -m pip install pytest pytest-cov -t "%SITE_PACK%" --upgrade
```

And then, you can use pytest with bpy.
```
set BLENDER_EXE=C:\Program Files\Blender Foundation\Blender 3.0\blender.exe
pytest tests\ -svv --blender-executable "%BLENDER_EXE%" --cov-report html --cov-report term:skip-covered
```

## Github Actions
[Github Actions](https://docs.github.com/en/actions) is an automation tool for development workflows.<br>
You can run scripts on remote servers for your repositories.<br>
There are 2 workflows for the addon.

- CI: Run flake8, pydocstring, pylint, and pytest to check your codes.
- packaging: Pack only necessary files and upload them to the release page.

See here if you want to use the workflows.<br>
[How to Build With Github Actions · matyalatte/Blender-Uasset-Addon Wiki](https://github.com/matyalatte/Blender-Uasset-Addon/wiki/How-to-Build-with-Github-Actions)

