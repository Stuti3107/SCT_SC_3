# SCT_SC_3
import re

def assess_password_strength(password):
    score = 0
    criteria = {
        "length": len(password) >= 8,
        "uppercase": any(char.isupper() for char in password),
        "lowercase": any(char.islower() for char in password),
        "number": any(char.isdigit() for char in password),
        "special_char": bool(re.search(r"[!@#$%^&*(),.?\":{}|<>]", password)),
    }
    
    score = sum(criteria.values())
    
    strength_levels = ["Very Weak", "Weak", "Moderate", "Good", "Strong", "Very Strong"]
    
    return strength_levels[score], criteria

# Example usage
password = input("Enter a password: ")
strength, details = assess_password_strength(password)
print(f"Password Strength: {strength}")
print("Criteria met:")
for key, value in details.items():
    print(f"{key.capitalize()}: {'✔' if value else '✘'}")
