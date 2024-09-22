import numpy as np
import matplotlib.pyplot as plt

# Function to simulate a dice roll
def roll_dice():
    return np.random.randint(1, 7)

# Monte Carlo simulation function
def monte_carlo_simulation(num_trials):
    results = []
    for _ in range(num_trials):
        result = roll_dice()
        results.append(result)
    
    return results

# Main function
def main():
    num_trials = 10000  # Number of trials
    results = monte_carlo_simulation(num_trials)

    # Calculate probabilities
    probabilities = [results.count(i) / num_trials for i in range(1, 7)]
    
    # Display results
    print("Probabilities of rolling each number (1-6):")
    for i, prob in enumerate(probabilities, start=1):
        print(f"{i}: {prob:.2f}")

    # Plotting the results
    plt.bar(range(1, 7), probabilities, color='blue', alpha=0.7)
    plt.xlabel('Dice Face')
    plt.ylabel('Probability')
    plt.title('Probability Distribution of Dice Rolls (Monte Carlo Simulation)')
    plt.xticks(range(1, 7))
    plt.ylim(0, 1)
    plt.grid(axis='y')
    plt.show()

if __name__ == "__main__":
    main()
