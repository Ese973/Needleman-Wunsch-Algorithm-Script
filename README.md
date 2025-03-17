# Needleman-Wunsch-Algorithm-Tool

Here is a tool desinged to generate an optimal sequence alignment between two DNA sequences. Input parameters should be both sequences (seq1 and seq2), a match score, a mismatch score, a gap penalty, and a gap extension penalty. The script will intialize a scoring matrix and a traceback matrix so the alignment can to be done by hand. For the traceback matrix, letters represent the movement of the traceback with "D" = diagonal, "L" = left, and "U" = up. Traceback starts at the bottom right corner of the scoring matrix and multiple paths could be possible to generate more than one optimal alignment. The scores of multiple alignments will be the exact same. Please note that this is still a working model with future work looking to show multiple optimal aligments all at once. 

<img width="633" alt="Screenshot 2025-03-17 at 9 48 30 AM" src="https://github.com/user-attachments/assets/c23e9469-15b6-4f20-a712-6a93700c66c2" />
