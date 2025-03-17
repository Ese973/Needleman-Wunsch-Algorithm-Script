import numpy as np

# Define the sequences
seq1 = "GATTACTCACTC"
seq2 = "GTCGACGCATTTA"

# Define the scoring scheme
match_score = 3
mismatch_score = -3
gap_penalty = -2
gap_extension = -2

# Initialize the scoring matrix and the traceback matrix
n = len(seq1)
m = len(seq2)
score_matrix = np.zeros((n + 1, m + 1))
traceback_matrix = np.zeros((n + 1, m + 1), dtype=str)

# Initialize the first row and column of the scoring matrix
for i in range(1, n + 1):
    score_matrix[i][0] = gap_penalty + (i - 1) * gap_extension
    traceback_matrix[i][0] = "U"  # Up

for j in range(1, m + 1):
    score_matrix[0][j] = gap_penalty + (j - 1) * gap_extension
    traceback_matrix[0][j] = "L"  # Left

# Fill in the scoring matrix and traceback matrix
for i in range(1, n + 1):
    for j in range(1, m + 1):
        # Calculate the score for a match/mismatch
        if seq1[i - 1] == seq2[j - 1]:
            diagonal_score = score_matrix[i - 1][j - 1] + match_score
        else:
            diagonal_score = score_matrix[i - 1][j - 1] + mismatch_score

        # Calculate the score for a gap in seq1
        up_score = (
            score_matrix[i - 1][j] + gap_penalty
            if traceback_matrix[i - 1][j] != "U"
            else score_matrix[i - 1][j] + gap_extension
        )

        # Calculate the score for a gap in seq2
        left_score = (
            score_matrix[i][j - 1] + gap_penalty
            if traceback_matrix[i][j - 1] != "L"
            else score_matrix[i][j - 1] + gap_extension
        )

        # Choose the maximum score
        max_score = max(diagonal_score, up_score, left_score)

        # Update the score matrix and traceback matrix
        score_matrix[i][j] = max_score
        if max_score == diagonal_score:
            traceback_matrix[i][j] = "D"  # Diagonal
        elif max_score == up_score:
            traceback_matrix[i][j] = "U"  # Up
        else:
            traceback_matrix[i][j] = "L"  # Left

# Traceback to find the optimal alignment
aligned_seq1 = ""
aligned_seq2 = ""
i, j = n, m

while i > 0 or j > 0:
    if traceback_matrix[i][j] == "D":
        aligned_seq1 = seq1[i - 1] + aligned_seq1
        aligned_seq2 = seq2[j - 1] + aligned_seq2
        i -= 1
        j -= 1
    elif traceback_matrix[i][j] == "U":
        aligned_seq1 = seq1[i - 1] + aligned_seq1
        aligned_seq2 = "-" + aligned_seq2
        i -= 1
    else:
        aligned_seq1 = "-" + aligned_seq1
        aligned_seq2 = seq2[j - 1] + aligned_seq2
        j -= 1

# Print the results
print("Score Matrix:")
print(score_matrix)
print("\nTraceback Matrix:")
print(traceback_matrix)
print("\nOptimal Alignment:")
print(aligned_seq1)
print(aligned_seq2)
