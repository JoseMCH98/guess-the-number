import random    

def computer_guess(x): # here we are defining our function
    low = 1 # the lowest number the computer can guess in this scenario
    high = x # this represents the maximum possible number
    feedback = "" # starts empty since no feedback has been provided yet
    attempts = 0 # number of attempts
    
    while feedback != "c": # this is the beginning of our loop
        try: # "try and except" are going to be our control flow statements
            if low != high: # if low is not equal to high 
                guess = random.randint(low, high) # the computer generates a number between "low" and "high" 
                attempts += 1 # here we are adding +1 for every failed attempt
            else: # this happens when low and high are the same, meaning there's only one possible number left to guess
                guess = low
            feedback = input(f"Is {guess} too high (H), too low (L), or correct (C)? ").lower() 
            # feedback started empty, now we are assigning it a value. 
            # We use "input()" so the player can tell the computer if the guess is too high, too low, or correct.
            # ".lower()" is used to prevent errors since in Python, uppercase and lowercase letters have different values.

            if feedback not in ["h", "l", "c"]: # this ensures the code doesn't break due to invalid input
                print("Please provide valid input (H, L, C).") # message prompting the user to enter valid input
                continue # this makes sure the user provides valid input before continuing
            
            if feedback == "h": # if feedback is "h" (too high)
                if guess == low: # if guess is equal to low (example: 1 == 1)
                    print(f"Your number has been guessed! :) {guess}") 
                    # This prevents an infinite loop if the user provides false feedback.
                    continue
                high = guess - 1 
                # This is one of the most important parts of the code. 
                # Example: if your number is "11" and you say "h" (too high), 
                # the computer will subtract 1 from the guess, making the new highest possible number "10". 
                # This allows the game to run properly and prevents an infinite loop.
            elif feedback == "l": # if feedback is "l" (too low)
                if guess == high:
                    print(f"Your number has been guessed! :) {guess}") 
                    # This prevents an infinite loop if the user provides false feedback.
                    continue
                low = guess + 1 # works the same way as "high = guess - 1", but for lower values
                
        except ValueError: # prevents the code from crashing if the user enters something that isn't "h", "l", or "c"
            print("Please provide valid input.") # error message 
    
    print(f"Congratulations! The computer has guessed your secret number {guess} in {attempts} attempts!") 
    # Congratulatory message when the number is guessed

computer_guess()

