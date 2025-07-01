import re
import random
import string
from colorama import Fore, Style, init

# Initialize colorama
init()

def check_password_strength(password):
    strength = 0
    suggestions = []

    # Check character types
    has_upper = bool(re.search(r"[A-Z]", password))
    has_lower = bool(re.search(r"[a-z]", password))
    has_digit = bool(re.search(r"[0-9]", password))
    has_special = bool(re.search(r"[@$!%*?&#^+=-_]", password))

    # Password conditions
    if len(password) < 4:
        return 0, ["Very Weak: Your password must be at least 4 characters long."]
    
    if (password.isdigit() or password.isalpha()) and len(password) < 4:
        return 0, ["Very Weak: Avoid using only numbers or only alphabets with fewer than 4 characters."]
    
    if (has_digit and has_lower or has_upper) and len(password) <= 4:
        return 2, ["Medium: Use more characters to strengthen your password."]
    
    if len(password) >= 8 and has_upper and has_lower and has_digit and has_special:
        return 5, []  # Very Strong
    
    if len(password) >= 8 and has_upper and has_lower and has_digit:
        return 4, ["Strong: Adding a special character will make it very strong."]
    
    if len(password) >= 8:
        return 3, ["Medium: Add a mix of uppercase, lowercase, numbers, and special characters."]
    
    return 1, ["Weak: Use a combination of uppercase, lowercase, numbers, and special characters."]

def generate_strong_password():
    new_password = [
        random.choice(string.ascii_uppercase),
        random.choice(string.ascii_lowercase),
        random.choice(string.digits),
        random.choice("@$!%*?&#^+=-_")
    ]
    while len(new_password) < 12:
        new_password.append(random.choice(string.ascii_letters + string.digits + "@$!%*?&#^+=-_") )
    random.shuffle(new_password)
    return "".join(new_password)

def main():
    print(Fore.CYAN + r"""
                             
              |  _ \|  _ \  
              | |_) | |_) |  
              |  __/|  __/  
              |_|   |_|     


    """ + Style.RESET_ALL)
    print("Author By: Gayathri Nalluri")
    print("GitHub: https://github.com/Gayathri2531\n")

    password = input("Enter your password: ")
    strength, suggestions = check_password_strength(password)

    if strength == 0:
        print(Fore.RED + "[Very Weak] Your password is too weak!" + Style.RESET_ALL)
    elif strength == 1:
        print(Fore.RED + "[Weak] Your password is weak." + Style.RESET_ALL)
    elif strength == 2:
        print(Fore.YELLOW + "[Medium] Your password is fairly strong." + Style.RESET_ALL)
    elif strength == 3:
        print(Fore.BLUE + "[Medium-Strong] Your password is decent but could be stronger." + Style.RESET_ALL)
    elif strength == 4:
        print(Fore.BLUE + "[Strong] Your password is strong!" + Style.RESET_ALL)
    elif strength == 5:
        print(Fore.GREEN + "[Very Strong] Your password is very strong!" + Style.RESET_ALL)

    if suggestions:
        print(Fore.CYAN + "\nSuggestions to improve your password:")
        for suggestion in suggestions:
            print("- " + suggestion)
        print(Style.RESET_ALL)

    if strength < 4:
        strong_password = generate_strong_password()
        print(Fore.MAGENTA + "\nSuggested Strong Password: " + strong_password + Style.RESET_ALL)

if __name__ == "__main__":
    main()
