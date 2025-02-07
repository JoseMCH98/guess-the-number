import random

def computer_guess(x):
    low = 1
    high = x
    feedback = ""
    attempts = 0
    
    while feedback != "c":
        try:
            if low != high:
                guess = random.randint(low, high)
                attempts += 1 
            else:
                guess = low
            feedback = input(f"Is {guess} too high (H), too low (L), or correct (C)? ").lower()
            
            if feedback not in ["h", "l", "c"]:
                print("Please provide valid input (H, L, C).")
                continue
            
            if feedback == "h":
                if guess == low:
                    print(f"Your number has been guessed! :) {guess}")
                    continue
                high = guess - 1
            elif feedback == "l":
                if guess == high:
                    print(f"Your number has been guessed! :) {guess}")
                    continue
                low = guess + 1 
        except ValueError:
            print("Please provide valid input.")
    
    print(f"Congratulations! The computer has guessed your secret number {guess} in {attempts} attempts!")

computer_guess()
