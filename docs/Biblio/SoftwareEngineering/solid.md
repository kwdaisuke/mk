```py
"""
Dependency Inversion Principle
Dependency should be on abstractions not concretions
A. High-level modules should not depend upon low-level modules. Both should depend upon abstractions.
B. Abstractions should not depend on details. Details should depend upon abstractions.
There comes a point in software development where our app will be largely composed of modules. 
When this happens, we have to clear things up by using dependency injection. 
High-level components depending on low-level components to function.
"""


class Database:
    def __init__(self, name):
        self.name = name

    def connection_name(self):
        print(self.name)

    def get_table(self):
        fetch = func(self.name)
        return fetch

    def get_structure(self):
        pass
        
    def get_view(self, table, query):
        table = get_table()
        view = query(table)

# Inheritance: is-a-relationship
class Structured(Database):
    def __init__(self):
        pass

# Aggregation: has-a-relationship
class Unstructured:
    def __init__(self, database: Database):
        self.database = database


"""
High-level modules should not depend on low-level level modules. It should depend upon its abstraction.
"""
```

Interface Segregation
```py
"""
Interface Segregation Principle
Make fine grained interfaces that are client specific
Clients should not be forced to depend upon interfaces that they do not use.
This principle deals with the disadvantages of implementing big interfaces.
"""

class DataBase:
    def get_schema(self):
        raise NotImplementedError

class BigTable(Database):
    def get_schema(self):
        pass

class Cassandra(Database):
    def get_schema(self):
        pass 

class Spanner(Database):
    def get_schema(self):
        pass
```


```py
"""
Liskov Substitution Principle
A sub-class must be substitutable for its super-class.
The aim of this principle is to ascertain that a sub-class can assume the place of its super-class without errors. 
If the code finds itself checking the type of class then, it must have violated this principle.
"""
class Database:
    def __init__(self, name):
        self.name = name
        
        
    def connection_name(self):
        print(self.name)
    
    def get_table(self):
        fetch = func(self.name)
        return fetch

    def get_structure(self):
        pass
        
    def get_view(self, table, query):
        table = get_table()
        view = query(table)

class BigTable(Database):
    def get_view(self, table, query, index):
        table = get_table()
        view = query(table, index)

class Cassandra(Database):
    def get_view(self, table, query, index):
        table = get_table()
        view = query(table, index)

class Spanner(Database):
    def get_view(self, table, query, key):
        table = get_table()
        view = query(table, key)

```

```py
"""
Open-Closed Principle
Software entities(Classes, modules, functions) should be open for extension, not modification.
"""

class Database:
    def __init__(self, name):
        self.name = name
        
        
    def connection_name(self):
        print(self.name)
    
    def get_table(self):
        fetch = func(self.name)
        return fetch

databases = [
    Database("BigTable"),
    Database("Cassandra")
]

def database_structure(databases: list):
    for database in databases:
        if database.name == "BigTable" or "Cassandra":
            print("Unstructured")
        else:
            continue 

"""
This method is imcompatible if the database is for structured
"""

class Database:
    def __init__(self, name):
        self.name = name
        
    def connection_name(self):
        print(self.name)
    
    def get_structure(self):
        pass

class BigTable(Database):
    def get_structure(self):
        print("Unstructured")

class Cassandra(Database):
    def get_structure(self):
        print("Unstructured")

class Spanner(Database):
    def get_structure(self):
        print("Structured")


databases = [
    Database("BigTable"),
    Database("Cassandra"),
    Database("Spanner")
]

def database_structure(databases: list):
    for database in databases:
        database.get_structure()

"""
This allows the extensions
"""
```