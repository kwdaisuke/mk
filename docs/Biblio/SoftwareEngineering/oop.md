In the abstraction.py file, the Location and Country classes are defined. The Location class has two attributes, longitude and latitude, and the Country class has a name attribute and a location attribute that is an instance of the Location class. This is an example of abstraction, as the Country class is abstracting the concept of a location and representing it using the Location class.

```py title="abstraction.py" linenums="1"
class Location:
    def __init__(self, longitude, latitude):
        self.longitude = longitude
        self.latitude = latitude

class Country:
    def __init__(self, name, location):
        self.name = name
        self.location = location


location = Location
country = Country("Croatia", location)
```


In the composition.py file, the Location and Country classes are defined in a similar way, but the Country class does not have a location attribute that is an instance of the Location class. Instead, it has a location attribute that is an instance of the Location class created within the Country class's __init__ method. This is an example of composition, as the Country class is composed of an instance of the Location class.
```py title="composition.py" linenums="1"
class Location:
    def __init__(self, longitude, latitude):
        self.longitude = longitude
        self.latitude = latitude

class Country:
    def __init__(self, name):
        self.name = name
        self.location = Location()
```

In the inheritance.py file, the Country class is defined as a base class that has a name attribute, a map attribute, and a product method. The Tokyo, Paris, and Moscow classes are defined as subclasses of the Country class, and they each have longitude and latitude attributes and a modified __init__ method that calls the base class's __init__ method using the super() function. This is an example of inheritance, as the Tokyo, Paris, and Moscow classes inherit attributes and methods from the Country class.


```py title="inheritance.py" linenums="1"
class Country:
    def __init__(self, name):
        self.name = None
        self.map = None

    def product(self, a, b):
        return a*b

    def set_map(self):
        self.map = self.product(self.latitude, self.longitude)

class Tokyo(Country):
    def __init__(self,  longitude, latitude, name):
        super.__init__(name)
        self.longitude = longitude
        self.latitude = latitude

class Paris(Country):
    def __init__(self,  longitude, latitude, name):
        super.__init__(nam)
        self.longitude = longitude
        self.latitude = latitude     

class Moscow(Country):
    def __init__(self,  longitude, latitude, name):
        super.__init__(nam)
        self.longitude = longitude
        self.latitude = 
```

In the polymorphism.py file, the Country class is defined as a base class that has a name attribute and a map attribute. The child_class method is defined as a virtual method, which means that it is intended to be overridden in subclasses. The Japan, France, and Russia classes are defined as subclasses of the Country class, and they each override the child_class method. This is an example of polymorphism, as the child_class method behaves differently depending on which subclass it is called on.

```py title="polymorphism.py" linenums="1"
class Country:
    def __init__(self, name, map):
        self.name = None
        self.map = None

    def child_class
```