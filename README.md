import re

def check_password_strength(password):
    """
    Function to check the strength of a password based on the following criteria:
    - Length (minimum 8 characters)
    - Presence of uppercase and lowercase letters
    - Presence of digits
    - Presence of special characters
    """
    # Password strength counters
    strength = 0
    feedback = []
    
    # Check for password length
    if len(password) < 8:
        feedback.append("Password should be at least 8 characters long.")
    else:
        strength += 1

    # Check for presence of lowercase characters
    if re.search(r'[a-z]', password):
        strength += 1
    else:
        feedback.append("Password should include lowercase letters.")
    
    # Check for presence of uppercase characters
    if re.search(r'[A-Z]', password):
        strength += 1
    else:
        feedback.append("Password should include uppercase letters.")
    
    # Check for presence of digits
    if re.search(r'[0-9]', password):
        strength += 1
    else:
        feedback.append("Password should include at least one number.")
    
    # Check for presence of special characters
    if re.search(r'[!@#$%^&*(),.?":{}|<>]', password):
        strength += 1
    else:
        feedback.append("Password should include at least one special character.")
    
    # Provide feedback based on strength score
    if strength == 5:
        return "Password is Strong!", feedback
    elif strength >= 3:
        return "Password is Medium Strength", feedback
    else:
        return "Password is Weak", feedback

def main():
    """
    Main function to test the password strength checker with a predefined password
    """
    print("Password Strength Checker Tool")

    # Test with the given password
    password = "$uh@ib+&#0567"
    print(f"Testing password: {password}")
    
    strength, feedback = check_password_strength(password)
    print(f"Password Strength: {strength}")
    
    if feedback:
        print("Suggestions to improve the password:")
        for suggestion in feedback:
            print(f"- {suggestion}")

if _name_ == "_main_":
    main()# prodigy_cs_03
