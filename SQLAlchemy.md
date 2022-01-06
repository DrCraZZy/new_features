# SQLAlchemy

## Erstellen einer DB

Als erstes wird eine `database.py` Datei erstellt in der alle für das Erstellen einer DB grundlegende Eingenschaften definiert werden.

```python
from sqlalchemy import create_engine
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy.orm import sessionmaker

#in Falle einer anderen DB müssen hier die eingangs daten eingetragen werden
DATABASE_NAME = 'TheTransporter.sqlite'

engine = create_engine(f'sqlite:///{DATABASE_NAME}')
Session = sessionmaker(bind=engine)
Base = declarative_base()


def create_db():
    Base.metadata.create_all(engine)
```

Für das Estellen einer neuen Tabelle wird eine Klasse erstellt mit Eigenschaften und Methoden (wenn es benötigt wird)

```python
from sqlalchemy import Column, Integer, String, Date
from sqlalchemy.orm import relationship

from models.database import Base


class Customer(Base):
    __tablename__ = 'customer'

    id = Column(Integer, primary_key=True)
    name = Column(String)
    address = Column(String)
    inn = Column(String)
    email = Column(String)
    registration_date = Column(Date)
    # Tabelle order beinhaltet einen ForignKey zu der Tabelle customer
    # mit relationship zu KLASSE Order kann man eine Beziehung setzen
    order = relationship('Order') 

    def __init__(self, name: str, address: str, inn: str, email: str):
        self.name = name
        self.address = address
        self.inn = inn
        self.email = email

    def __repr__(self):
        return f'Customer [{self.name}, INN: {self.inn} Email: {self.email}]'
```

Als nächstes wird eine Modul erstellt in dem alle Klassen importiert werden und die Methond `create_db()` aus `database.py` aufgerufen.

```python
from models.database import create_db
from models.customer import Customer
from models.order import Order
from models.orders_live import OrderLive
from models.orders_archive import OrderArchive
from models.services import Services
from models.transporter import Transporter
from models.vehicles import Vehicles


def create_database():
    create_db()
```

```python
import os

from models.database import DATABASE_NAME
import create_database as db_creator

if __name__ == '__main__':
    db_is_created = os.path.exists(DATABASE_NAME)
    if not db_is_created:
        db_creator.create_database()
```
