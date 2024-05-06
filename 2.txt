import collections
pets = {
    1: {
        "Мухтар": {
            "Вид питомца": "Собака",
            "Возраст питомца": 9,
            "Имя владельца": "Павел"
            },
            },
     2: {
         "Каа": {
             "Вид питомца": "желторотый питон",
             "Возраст питомца": 19,
             "Имя владельца": "Саша"
              },
              }
              }
def get_pet(ID):
    return pets.get(ID, False)
def get_suffix(age):
    if age % 10 == 1 and age != 11:
        return "год"
    elif age % 10 in [2, 3, 4] and age not in [12, 13, 14]:
        return "года"
    else:
        return "лет"
def pets_list():
    for pet_id, pet_info in pets.items():
        for pet_name, pet_data in pet_info.items():
            print(f"ID: {pet_id}, Питомец: {pet_name}, Вид: {pet_data['Вид питомца']}, Возраст: {pet_data['Возраст питомца']} {get_suffix(pet_data['Возраст питомца'])}, Владелец: {pet_data['Имя владельца']}")
        def create():
            last = collections.deque(pets, maxlen=1)[0]
            name = input("Введите кличку питомца: ")
            pet_type = input("Введите вид питомца: ")
            age = int(input("Введите возраст питомца: "))
            owner = input("Введите имя владельца: ")
            last += 1
            pets[last] = {name: {"Вид питомца": pet_type, "Возраст питомца": age, "Имя владельца": owner}}
            print("Запись успешно добавлена!")
def read():
    ID = int(input("Введите ID питомца: "))
    pet = get_pet(ID)
    if pet:
        pet_name = list(pet.keys())[0]
        pet_data = pet[pet_name]
        suffix = get_suffix(pet_data["Возраст питомца"])
        print(f"Это {pet_data['Вид питомца']} по кличке \"{pet_name}\". Возраст питомца: {pet_data['Возраст питомца']} {suffix}. Имя владельца: {pet_data['Имя владельца']}")
    else:
        print("Питомец с указанным ID не найден!")                
def update():
    ID = int(input("Введите ID питомца для обновления информации: "))
    pet = get_pet(ID)
    if pet:
        pet_name = list(pet.keys())[0]
        pet_data = pet[pet_name]
        print(f"Текущая информация о питомце {pet_name}: {pet_data}")
        pet_type = input("Введите новый вид питомца (оставьте пустым, чтобы оставить без изменений): ")
        age = input("Введите новый возраст питомца (оставьте пустым, чтобы оставить без изменений): ")
        owner = input("Введите новое имя владельца (оставьте пустым, чтобы оставить без изменений): ")
        if pet_type:
            pet_data["Вид питомца"] = pet_type
            if age:
                pet_data["Возраст питомца"] = int(age)
                if owner:
                    pet_data["Имя владельца"] = owner
                    print("Информация о питомце успешно обновлена!")
                else:
                    print("Питомец с указанным ID не найден!") 
def delete():
    ID = int(input("Введите ID питомца для удаления: "))
    pet = get_pet(ID)
    if pet:
        pet_name = list(pet.keys())[0]
        del pets[ID]
        print(f"Информация о питомце {pet_name} успешно удалена!")
    else:
        print("Питомец с указанным ID не найден!")
        while True:
            print("\nДоступные команды:")
            print("1. Добавить запись о питомце (create)")
            print("2. Отобразить информацию о питомце (read)")
            print("3. Обновить информацию о питомце (update)")
            print("4. Удалить запись о питомце (delete)")
            print("5. Отобразить список всех питомцев (list)")
            print("6. Остановить программу (stop)")
            command = input("Введите команду: ")
            if command == "create":
               create()
            elif command == "read":
               read()
            elif command == "update":
               delete()
            elif command == "list":
               pets_list()
            elif command == "stop":
               print("Программа завершена.")
            break
        
                                
           
     
              






               












     










































































