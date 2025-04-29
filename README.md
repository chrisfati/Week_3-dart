1. Encapsulation
class Patient:
    def __init__(self, name, age):
        self.__name = name        # private variable
        self.__age = age          # private variable

    def get_name(self):
        return self.__name

    def get_age(self):
        return self.__age

    def set_age(self, age):
        if age > 0:
            self.__age = age
        else:
            print("Invalid age")
   
3. Inheritance
class InPatient(Patient):  # Inherits from Patient
    def __init__(self, name, age, room_number):
        super().__init__(name, age)
        self.room_number = room_number

    def display(self):
        print(f"In-Patient: {self.get_name()}, Age: {self.get_age()}, Room: {self.room_number}")
   
4. Polymorphism (Method Overriding)
class OutPatient(Patient):
    def __init__(self, name, age, appointment_date):
        super().__init__(name, age)
        self.appointment_date = appointment_date

    def display(self):  # Method overridden
        print(f"Out-Patient: {self.get_name()}, Age: {self.get_age()}, Appointment: {self.appointment_date}")
   
5. Abstraction
from abc import ABC, abstractmethod

class MedicalService(ABC):
    @abstractmethod
    def provide_service(self):
        pass

class Surgery(MedicalService):
    def provide_service(self):
        print("Performing surgery...")

class Therapy(MedicalService):
    def provide_service(self):
        print("Providing therapy session...")


# Encapsulation Test
p1 = Patient("Alice", 30)
print(p1.get_name())  # Alice
p1.set_age(-5)        # Invalid age

# Inheritance + Polymorphism
in_patient = InPatient("Bob", 40, "Room 12")
out_patient = OutPatient("Eve", 25, "2025-05-10")
in_patient.display()
out_patient.display()

# Abstraction
service1 = Surgery()
service2 = Therapy()
service1.provide_service()
service2.provide_service()
