import random

def computer_guess():
    print("Piensa en un número entre 1 y 100. ¡La computadora intentará adivinarlo!")
    low = 1
    high = 100
    attempts = 0
    
    while True:
        guess = random.randint(low, high)  # La computadora hace una suposición
        attempts += 1
        print(f"\n¿Es {guess} tu número?")
        
        user_input = input("Responde con 'mayor', 'menor' o 'correcto': ").strip().lower()
        
        if user_input == "correcto":
            print(f"¡La computadora adivinó tu número {guess} en {attempts} intentos! 🎉")
            break
        elif user_input == "mayor":
            low = guess + 1
        elif user_input == "menor":
            high = guess - 1
        else:
            print("Entrada no válida. Escribe 'mayor', 'menor' o 'correcto'.")

computer_guess()
