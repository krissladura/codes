#CODE 1 - movie night

# Input: number of movies
num_movies = int(input("Enter the number of movies Desi has selected: "))

# Initialize variables to track the highest and lowest rating, and their respective movie names
highest_rating = -1  # Starting with a very low value
lowest_rating = 11  # Starting with a very high value
highest_rated_movie = ""
lowest_rated_movie = ""

# Variable to calculate the total sum of ratings
total_rating = 0

# Process each movie
for _ in range(num_movies):
    movie_name = input("Enter the movie name: ")
    movie_rating = float(input(f"Enter the rating for '{movie_name}': "))
    
    # Update total rating
    total_rating += movie_rating

    # Check for highest rating
    if movie_rating > highest_rating:
        highest_rating = movie_rating
        highest_rated_movie = movie_name

    # Check for lowest rating
    if movie_rating < lowest_rating:
        lowest_rating = movie_rating
        lowest_rated_movie = movie_name

# Calculate the average rating
average_rating = total_rating / num_movies

# Output results
print(f"{highest_rated_movie} is with highest rating: {highest_rating:.1f}")
print(f"{lowest_rated_movie} is with lowest rating: {lowest_rating:.1f}")
print(f"Average rating: {average_rating:.1f}")


#CODE 2 - username task
# Input: Initial username
username = input("Enter the initial username: ")

# Process commands
while True:
    command_line = input("Enter a command (or 'Registration' to stop): ")
    
    # Exit condition
    if command_line == "Registration":
        break
    
    # Parse command and arguments
    command_parts = command_line.split()
    command = command_parts[0]
    
    if command == "Letters":
        case_type = command_parts[1]
        if case_type == "Lower":
            username = username.lower()
        elif case_type == "Upper":
            username = username.upper()
        print(username)
    
    elif command == "Reverse":
        start_index = int(command_parts[1])
        end_index = int(command_parts[2])
        # Validate indices
        if 0 <= start_index < len(username) and 0 <= end_index < len(username) and start_index <= end_index:
            substring = username[start_index:end_index + 1]
            print(substring[::-1])  # Reverse the substring
        else:
            continue  # Skip invalid indices

    elif command == "Substring":
        substring = command_parts[1]
        if substring in username:
            username = username.replace(substring, "", 1)  # Replace the first occurrence
            print(username)
        else:
            print(f"The username {username} doesn't contain {substring}.")

    elif command == "Replace":
        char_to_replace = command_parts[1]
        username = username.replace(char_to_replace, "-")
        print(username)

    elif command == "IsValid":
        char_to_check = command_parts[1]
        if char_to_check in username:
            print("Valid username.")
        else:
            print(f"{char_to_check} must be contained in your username.")

# Exit message
print("Registration complete.")

#CODE 3 - number reader
# Input: a1, a2, n
a1 = int(input("Enter a1 (ASCII code): "))
a2 = int(input("Enter a2 (ASCII code): "))
n = int(input("Enter n: "))

# Generate ticket numbers
for char1_ascii in range(a1, a2):
    char1 = chr(char1_ascii)  # Convert ASCII code to character
    for digit2 in range(1, n):
        for digit3 in range(1, n // 2):
            char4 = char1_ascii  # ASCII representation of char1
            
            # Check conditions
            if char1_ascii % 2 != 0 and (digit2 + digit3 + char4) % 2 != 0:
                print(f"{char1}-{digit2}{digit3}{char4}")



#CODE 4 - COMPUTER PARTS FUNCITONS
# PC Parts Inventory
pc_parts = {
    "CPU": [
        {"name": "Intel Core i9-13900K", "price": 599.99, "stock": 10},
        {"name": "AMD Ryzen 9 7950X", "price": 549.99, "stock": 8},
    ],
    "GPU": [
        {"name": "NVIDIA RTX 4090", "price": 1599.99, "stock": 5},
        {"name": "AMD Radeon RX 7900 XTX", "price": 999.99, "stock": 6},
    ],
    "Motherboard": [
        {"name": "ASUS ROG STRIX Z790-E", "price": 399.99, "stock": 12},
        {"name": "MSI MAG B650 TOMAHAWK", "price": 259.99, "stock": 15},
    ],
    "RAM": [
        {"name": "Corsair Vengeance DDR5 32GB", "price": 149.99, "stock": 20},
        {"name": "G.SKILL Trident Z5 RGB 32GB", "price": 169.99, "stock": 18},
    ],
    "Storage": [
        {"name": "Samsung 980 PRO 2TB SSD", "price": 179.99, "stock": 25},
        {"name": "Western Digital Black 4TB HDD", "price": 129.99, "stock": 30},
    ],
    "Power Supply": [
        {"name": "Corsair RM850x 850W", "price": 129.99, "stock": 10},
        {"name": "EVGA SuperNOVA 750W", "price": 119.99, "stock": 12},
    ],
    "Case": [
        {"name": "NZXT H510 Elite", "price": 149.99, "stock": 8},
        {"name": "Lian Li PC-O11 Dynamic", "price": 169.99, "stock": 10},
    ],
    "Cooling": [
        {"name": "Noctua NH-D15", "price": 99.99, "stock": 15},
        {"name": "Corsair iCUE H150i Elite", "price": 159.99, "stock": 12},
    ],
    "Peripherals": [
        {"name": "Logitech G502 HERO Mouse", "price": 49.99, "stock": 25},
        {"name": "Razer BlackWidow Keyboard", "price": 129.99, "stock": 20},
    ],
    "Monitor": [
        {"name": "LG UltraGear 27GN950-B", "price": 799.99, "stock": 5},
        {"name": "Dell Alienware AW3423DW", "price": 1299.99, "stock": 3},
    ]
}

# Function to display all PC parts
def display_parts():
    print("\n--- PC Parts Inventory ---")
    for category, items in pc_parts.items():
        print(f"\nCategory: {category}")
        for part in items:
            print(f"  - {part['name']} | Price: ${part['price']} | Stock: {part['stock']}")
    print("\n")

# Function to add a new part
def add_part(category, name, price, stock):
    if category not in pc_parts:
        pc_parts[category] = []
    pc_parts[category].append({"name": name, "price": price, "stock": stock})
    print(f"\nAdded '{name}' to category '{category}'.")

# Function to remove a part
def remove_part(category, name):
    if category in pc_parts:
        for part in pc_parts[category]:
            if part["name"] == name:
                pc_parts[category].remove(part)
                print(f"\nRemoved '{name}' from category '{category}'.")
                return
        print(f"\nPart '{name}' not found in category '{category}'.")
    else:
        print(f"\nCategory '{category}' does not exist.")

# Function to search for a part
def search_part(name):
    print(f"\nSearching for '{name}'...")
    for category, items in pc_parts.items():
        for part in items:
            if part["name"].lower() == name.lower():
                print(f"Found '{name}' in category '{category}' | Price: ${part['price']} | Stock: {part['stock']}")
                return
    print(f"Part '{name}' not found.")

# Function to update stock for a part
def update_stock(category, name, stock):
    if category in pc_parts:
        for part in pc_parts[category]:
            if part["name"] == name:
                part["stock"] = stock
                print(f"\nUpdated stock for '{name}' in category '{category}' to {stock}.")
                return
        print(f"\nPart '{name}' not found in category '{category}'.")
    else:
        print(f"\nCategory '{category}' does not exist.")

# Function to calculate total inventory value
def calculate_inventory_value():
    total_value = 0
    for items in pc_parts.values():
        for part in items:
            total_value += part["price"] * part["stock"]
    print(f"\nTotal Inventory Value: ${total_value:.2f}")

# Example usage
display_parts()
add_part("CPU", "Intel Core i5-13600K", 319.99, 12)
remove_part("GPU", "NVIDIA RTX 4090")
search_part("Corsair Vengeance DDR5 32GB")
update_stock("Storage", "Samsung 980 PRO 2TB SSD", 30)
calculate_inventory_value()
display_parts()

#CODE 6 - WORLD RECORD ATTEMPT

# Вход за целевата височина
target_height = int(input())

# Инициализиране на стартовата височина (30 см под целевата височина)
current_height = target_height - 30

# Променливи за общия брой скокове и опитите на текущата височина
total_jumps = 0
failed_attempts = 0

# Цикъл за обработка на скоковете
while current_height <= target_height:
    jump_height = int(input())  # Височина на текущия скок
    total_jumps += 1  # Увеличаване на броя на скоковете

    if jump_height > current_height:
        # Успешен скок: повдигане на летвата с 5 см
        current_height += 5
        failed_attempts = 0  # Нулиране на броя на неуспешните опити
    else:
        # Неуспешен скок: увеличаване на броя на неуспешните опити
        failed_attempts += 1

        if failed_attempts == 3:
            # Провал след 3 неуспешни опита
            print(f"Tihomir failed at {current_height}cm after {total_jumps} jumps.")
            break
else:
    # Успех: Тихомир прескача целевата височина
    print(f"Tihomir succeeded, he jumped over {current_height}cm after {total_jumps} jumps.")


#CODE 7 - attempt to create an app(used a lot of research, hoping i did something good)
app = Flask(__name__)

pc_parts = {
    "CPU": [
        {"name": "Intel Core i9-13900K", "price": 599.99, "stock": 10},
        {"name": "AMD Ryzen 9 7950X", "price": 549.99, "stock": 8},
    ],
    "GPU": [
        {"name": "NVIDIA RTX 4090", "price": 1599.99, "stock": 5},
        {"name": "AMD Radeon RX 7900 XTX", "price": 999.99, "stock": 6},
    ]
}

@app.route('/')
def home():
    return render_template('index.html', parts=pc_parts)

@app.route('/add_part', methods=['POST'])
def add_part():
    data = request.json
    category = data['category']
    name = data['name']
    price = float(data['price'])
    stock = int(data['stock'])

    if category not in pc_parts:
        pc_parts[category] = []

    pc_parts[category].append({"name": name, "price": price, "stock": stock})
    return jsonify({"message": f"Added {name} to {category}."})

@app.route('/remove_part', methods=['POST'])
def remove_part():
    data = request.json
    category = data['category']
    name = data['name']

    if category in pc_parts:
        for part in pc_parts[category]:
            if part['name'] == name:
                pc_parts[category].remove(part)
                return jsonify({"message": f"Removed {name} from {category}."})
    return jsonify({"error": "Part not found."}), 404

@app.route('/search_part', methods=['GET'])
def search_part():
    name = request.args.get('name')
    for category, items in pc_parts.items():
        for part in items:
            if part['name'].lower() == name.lower():
                return jsonify({"category": category, "part": part})
    return jsonify({"error": "Part not found."}), 404

@app.route('/update_stock', methods=['POST'])
def update_stock():
    data = request.json
    category = data['category']
    name = data['name']
    stock = int(data['stock'])

    if category in pc_parts:
        for part in pc_parts[category]:
            if part['name'] == name:
                part['stock'] = stock
                return jsonify({"message": f"Updated stock for {name} in {category}."})
    return jsonify({"error": "Part not found."}), 404

@app.route('/calculate_inventory_value', methods=['GET'])
def calculate_inventory_value():
    total_value = sum(
        part['price'] * part['stock'] for items in pc_parts.values() for part in items
    )
    return jsonify({"total_value": total_value})

if __name__ == '__main__':
    app.run(debug=True)


#CODE 8 - HTML FORMAT CODE(used a lot of research)
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PC Parts Inventory</title>
</head>
<body>
    <h1>PC Parts Inventory</h1>
    <ul>
        {% for category, parts in parts.items() %}
            <li><strong>{{ category }}</strong>:
                <ul>
                    {% for part in parts %}
                        <li>{{ part['name'] }} - ${{ part['price'] }} (Stock: {{ part['stock'] }})</li>
                    {% endfor %}
                </ul>
            </li>
        {% endfor %}
    </ul>
</body>
</html>


#CODE
