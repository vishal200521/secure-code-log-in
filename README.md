import hashlib

users = {}

def hash_password(password):
    return hashlib.sha256(password.encode()).hexdigest()

def register():
    username = input("📝 Enter a new username: ")
    if username in users:
        print("⚠️ Username already exists.")
    else:
        password = input("🔐 Enter a password: ")
        users[username] = hash_password(password)
        print("✅ Registration successful.")

def login():
    username = input("👤 Enter username: ")
    password = input("🔑 Enter password: ")
    hashed = hash_password(password)

    if username in users and users[username] == hashed:
        print("✅ Login successful")
    else:
        print("❌ Invalid credentials")

def main():
    while True:
        print("\n=== Secure Login System ===")
        print("1. Register")
        print("2. Login")
        print("3. Exit")
        choice = input("Enter choice (1/2/3): ")

        if choice == '1':
            register()
        elif choice == '2':
            login()
        elif choice == '3':
            print("👋 Exiting...")
            break
        else:
            print("❌ Invalid option. Try again.")

if __name__ == "__main__":
    main()
