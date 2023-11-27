---
title: "Python Dependency Management: pip and poetry"
date: "2023-11-27"
tags: ["Python"]
categories: ["posts"]
aliases: ["python-programming"]
# ShowToc: true
# TocOpen: true
ShowBreadCrumbs: true
draft: false
---

***Install package using pip***

```shell
python3 -m pip install iotcore
```

***Show package details using pip***

```shell
python3 -m pip show iotcore
```

***Uninstall package using pip***

```shell
python3 -m pip uninstall iotcore
```

***List installed packages using pip***

```shell
python3 -m pip list
```

***Upgrade a package using pip***

```shell
python3 -m pip install --upgrade iotcore
# or
python3 -m pip install -U iotcore
```

***New python project using poetry***

```shell
poetry new poeetry_demo
```

***Install new package using poetry***

```shell
poetry add arrow
```

***Show installed packages using poetry***

```shell
poetry show --tree
```
***Remove installed packages using poetry***

```shell
poetry remove arrow
```
Then,
```shell
poetry install --sync
```

***virtualenv in poetry***

Activate the virtualenv
```shell
poetry shell
```

To exit the virtualenv

```shell
exit
```

Or run with the poetry like;

```shell
poetry run python project/script.py
```

***Run python functions or scripts from poetry***

Create a new python script inside your project, maybe inside ```scripts/timer.py```.

```python
import time

def main():
    time.sleep(3)
    print("Timer expired")

if __name__=="__main__":
    main()
```

Now add this to your ```pyproject.toml``` file;

```toml
[tool.poetry.scripts]
timer = "scripts.timer:main"
```

Now this command can be invoked as follows;

```shell
poetry run timer
```