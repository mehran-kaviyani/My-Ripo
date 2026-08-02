# My-Ripo
import hashlib
import time

# Function to hash the password..
def hash_password(password ):
    return hashlib.sha256(password.encode()).hexdigest()

# Stored (hashed) password — this would normally be in a database
stored_password_hash = hash_password(" @15gf45Rhss")

# Maximum allowed attempts
MAX_ATTEMPTS = 3
attempts = 0

print("🔐 Welcome to the SmartLock System ")

while attempts < MAX_ATTEMPTS:
    user_input = input("Enter your password:  ")
    user_hash = hash_password(user_input)

    if user_hash == stored_password_hash:
        print("✅ Access granted. Welcome, M!")
        break
    else:
        attempts += 1
        print(f" it ❌ Incorrect password. Attempt {attempts}/{MAX_ATTEMPTS}")
        if attempts == MAX_ATTEMPTS:
            print("🚫 Too many failed attempts! System locked for 10 seconds.")
            time.sleep(10)
