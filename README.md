# three
 projectzoker
 import random

# Set the number of combinations to generate
num_combinations = 6

# Set the range of numbers for tzoker balls
tzoker_ball_range_1 = range(1, 20)
tzoker_ball_range_2 = range(5, 45)

# Update these lists with the tzoker numbers drawn in previous games
tzoker_numbers_drawn_1 = [9, 20, 20, 7, 3, 4, 7, 4, 20, 9, 9, 12, 7, 20]
tzoker_numbers_drawn_2 = [3, 8, 22, 36, 40, 6, 11, 21, 27, 41, 20, 25, 36, 44, 45, 18, 19, 20, 30, 33, 4, 8, 31, 35, 40, 7, 18, 29, 38, 39, 5, 12, 20, 22, 24, 23, 27, 28, 33, 17, 1, 10, 18, 29, 44, 1, 11, 14, 34, 38, 4, 6, 9, 13, 43, 15, 16, 29, 35, 42, 1, 17, 19, 25, 27, 7, 22, 23, 33, 44]

# Generate combinations of tzoker balls
for i in range(num_combinations):
    # Combine the tzoker balls drawn in previous games with the range of tzoker balls
    available_tzoker_balls_1 = list(set(tzoker_ball_range_1) - set(tzoker_numbers_drawn_1))
    available_tzoker_balls_2 = list(set(tzoker_ball_range_2) - set(tzoker_numbers_drawn_2))
    
    # Predict one tzoker ball from the range 1-20
    tzoker_ball_1 = random.choice(available_tzoker_balls_1)
    
    # Predict five tzoker balls from the range 5-45 without repetitions
    sample_size = min(5, len(available_tzoker_balls_2))  # Adjust sample size if available tzoker balls are less than 5
    tzoker_balls_2 = random.sample(available_tzoker_balls_2, sample_size)
    
    # Add one additional number from 1 to 20 to the final result
    additional_number = random.choice(list(set(tzoker_ball_range_1) - set([tzoker_ball_1])))

    # Print the predicted tzoker balls with the additional number
    print(f"Combination {i+1}: {tzoker_ball_1}, {', '.join(str(num) for num in tzoker_balls_2)}, {additional_number}")

