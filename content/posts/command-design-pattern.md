---
title: "How to implement command design pattern in python?"
date: "2021-12-08"
# description: "Implementation of command design pattern in python"
# tags: ["Tutorial", "Python", "Pattern"]
categories: ["posts"]
# series: ["Themes Guide"]
aliases: ["migrate-from-jekyl"]
# ShowToc: true
# TocOpen: true
ShowBreadCrumbs: true
draft: false
---


```python:title=src/interface.py

import abc


class CalcCmdAbs(metaclass=abc.ABCMeta):
    def __init__(self, *args, **kwargs):
        self._args = args
        self._kwargs = kwargs

    @property
    @abc.abstractmethod
    def name(self):
        raise NotImplemented()

    def execute(self):
        raise NotImplemented()
```



```python:title=src/commands.py

from .interface import CalcCmdAbs

OPERATORS = list()


def register_operator(cls):
    OPERATORS.append(cls)
    return cls


@register_operator
class AddCmd(CalcCmdAbs):
    name = "add"

    def __init__(self, a, b):
        super().__init__(a, b)
        self.a = a
        self.b = b

    def execute(self):
        return self.a + self.b


@register_operator
class SubtractCmd(CalcCmdAbs):
    name = "subtract"

    def __init__(self, a, b):
        super().__init__(a, b)
        self.a = a
        self.b = b

    def execute(self):
        return self.a - self.b


class NoneCmd(CalcCmdAbs):
    name = "None Command"

    def execute(self):
        print("Invalid Command")

```


```python:title=src/utils.py

from .commands import OPERATORS, NoneCmd


def get_commands() -> dict:
    return dict([cmd.name, cmd] for cmd in OPERATORS)


def parse_commands(commands: dict, operation: str, *args):
    command = commands.setdefault(operation, NoneCmd)
    return command(*args)

```


```python:title=src/tests.py

import unittest

from .utils import get_commands, parse_commands


class TestCase(unittest.TestCase):

    def setUp(self) -> None:
        self.commands = get_commands()

    def test_addition(self):
        command = parse_commands(self.commands, "add", 1, 1)
        self.assertEqual(command.execute(), 2, "Addition fail")

    def test_subtraction(self):
        command = parse_commands(self.commands, "subtract", 1, 1)
        self.assertEqual(command.execute(), 0, "Subtraction fail")

```