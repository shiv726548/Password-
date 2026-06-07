import re

def check_password(password):
    score = 0

    if len(password) >= 8:
        score += 20

    if len(password) >= 12:
        score += 20

    if re.search(r"[A-Z]", password):
        score += 15

    if re.search(r"[a-z]", password):
        score += 15

    if re.search(r"\d", password):
        score += 15

    if re.search(r"[!@#$%^&*(),.?\":{}|<>]", password):
        score += 15

    common = ["password", "123456", "qwerty"]

    if password.lower() not in common:
        score += 20

    if score <= 30:
        strength = "Very Weak"
    elif score <= 60:
        strength = "Weak"
    elif score <= 80:
        strength = "Medium"
    elif score <= 100:
        strength = "Strong"
    else:
        strength = "Very Strong"

    return score, strength

password = input("Enter Password: ")
score, strength = check_password(password)

print(f"Score: {score}")
print(f"Strength: {strength}")
