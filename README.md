import random
from collections import Counter

# Initialize tzoker numbers drawn in previous games
tzoker_numbers_drawn_1 = [9, 20, 20, 7, 3, 4, 7, 4, 20, 9, 9, 12, 7, 20]
tzoker_numbers_drawn_2 = [3, 8, 22, 36, 40, 6, 11, 21, 27, 41, 20, 25, 36, 44, 45, 18, 19, 20, 30, 33, 4, 8, 31, 35, 40, 7, 18, 29, 38, 39, 5, 12, 20, 22, 24, 23, 27, 28, 33, 17, 1, 10, 18, 29, 44, 1, 11, 14, 34, 38, 4, 6, 9, 13, 43, 15, 16, 29, 35, 42, 1, 17, 19, 25, 27, 7, 22, 23, 33, 44]

# Function to generate tzoker combinations based on user input
def generate_tzoker_combinations(num_combinations, tzoker_numbers_drawn_1, tzoker_numbers_drawn_2):
    # Count the frequency of each number in the drawn numbers lists
    freq_tzoker_numbers_1 = Counter(tzoker_numbers_drawn_1)
    freq_tzoker_numbers_2 = Counter(tzoker_numbers_drawn_2)

    # Generate combinations of tzoker balls
    combinations = []
    for i in range(num_combinations):
        # Predict one tzoker ball from the range 1-20 based on frequency
        tzoker_ball_1 = max(tzoker_ball_range_1, key=lambda x: freq_tzoker_numbers_1.get(x, 0))
        
        # Calculate available tzoker balls in range 5-45 after excluding drawn numbers
        available_tzoker_balls_2 = [num for num in tzoker_ball_range_2 if num not in tzoker_numbers_drawn_2]
        
        # Adjust sample size if there are fewer available tzoker balls than the desired sample size
        sample_size = min(5, len(available_tzoker_balls_2))
        
        # Predict five tzoker balls from the available range without repetitions
        tzoker_balls_2 = random.sample(available_tzoker_balls_2, sample_size)
        
        # Add one additional number from 1 to 20 based on frequency to the final result
        additional_number = max(tzoker_ball_range_1, key=lambda x: freq_tzoker_numbers_1.get(x, 0))

        # Add the combination to the list
        combinations.append((tzoker_ball_1, tzoker_balls_2, additional_number))
    
    return combinations

# Set the range of numbers for tzoker balls
tzoker_ball_range_1 = range(1, 21)
tzoker_ball_range_2 = range(5, 46)

# Set the number of combinations to generate
num_combinations = 6

# Generate tzoker combinations based on user input
combinations = generate_tzoker_combinations(num_combinations, tzoker_numbers_drawn_1, tzoker_numbers_drawn_2)

# Print the generated combinations
for i, (tzoker_ball_1, tzoker_balls_2, additional_number) in enumerate(combinations):
    print(f"Combination {i+1}: {tzoker_ball_1}, {', '.join(str(num) for num in tzoker_balls_2)}, {additional_number}")

