basic

def f(\*args, \*\*kwargs):

x = args\[0\]

y = kwargs.get('y')

print (f"x: {x}, y: {y}")

*args: 位置输入

**kwargs:关键字输入

https://rszalski.github.io/magicmethods/

class

\_\_main\_\_

\_\_str\_\_

类的继承

class Pet(object):

def \_\_init\_\_(self,species,name):

self.species = species

self.name=name

def \_\_str\_\_(self):

return f"{self.species} named {self.name}"

def change\_name(self,new\_name):

self.name = new_name

class Dog(Pet):

def \_\_init\_\_(self,name,breed):

super().\_\_init\_\_(species='dog',name=name)

self.breed = breed

def \_\_str\_\_(self):

return f"{self.breed} named {self.name}"

class Dog(Pet):

def \_\_init\_\_(self, name, breed):

super().\_\_init\_\_(species="dog", name=name)

self.breed = breed

def \_\_str\_\_(self):

return f"{self.breed} named {self.name}"

@classmethod

def from_dict(cls, d):

return cls(name=d\["name"\], breed=d\["breed"\])

@staticmethod

def is_cute(breed):

return True  # all animaals are cute! @abstractmetho