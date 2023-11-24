import sqlite3

# Создаем подключение к базе данных
conn = sqlite3.connect('inventory.db')
c = conn.cursor()

# Создаем таблицу для хранения инвентаря
c.execute('''CREATE TABLE IF NOT EXISTS inventory 
             (id INTEGER PRIMARY KEY, 
             name TEXT, 
             description TEXT, 
             price REAL, 
             quantity INTEGER, 
             category TEXT)''')

# Добавление товара в инвентарь
def add_product():
    name = input("Введите название товара: ")
    description = input("Введите описание товара: ")
    price = float(input("Введите цену товара: "))
    quantity = int(input("Введите количество товара на складе: "))
    category = input("Введите категорию товара: ")
    c.execute("INSERT INTO inventory (name, description, price, quantity, category) VALUES (?, ?, ?, ?, ?)", 
              (name, description, price, quantity, category))
    conn.commit()
    print("Товар успешно добавлен в инвентарь.")

# Удаление товара из инвентаря
def remove_product():
    product_id = input("Введите уникальный идентификатор товара для удаления: ")
    c.execute("DELETE FROM inventory WHERE id=?", (product_id,))
    conn.commit()
    print("Товар успешно удален из инвентаря.")

# Редактирование информации о товаре
def edit_product():
    product_id = input("Введите уникальный идентификатор товара для редактирования: ")
    column = input("Введите название поля, которое нужно отредактировать (name, description, price, quantity, category): ")
    new_value = input(f"Введите новое значение для поля \"{column}\": ")
    c.execute(f"UPDATE inventory SET {column}=? WHERE id=?", (new_value, product_id))
    conn.commit()
    print("Информация о товаре успешно отредактирована.")

# Главное меню
def main_menu():
    while True:
        print("\n1. Добавить товар в инвентарь")
        print("2. Удалить товар из инвентаря")
        print("3. Редактировать информацию о товаре")
        print("4. Выйти из программы")
        choice = input("Выберите действие (1-4): ")
        
        if choice == "1":
            add_product()
        elif choice == "2":
            remove_product()
        elif choice == "3":
            edit_product()
        elif choice == "4":
            break
        else:
            print("Некорректный выбор, пожалуйста, выберите снова.")

# Запуск программы
main_menu()

# Закрытие подключения к базе данных
conn.close()
