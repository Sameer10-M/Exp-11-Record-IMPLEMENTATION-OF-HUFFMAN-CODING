# Exp-11--Record-IMPLEMENTATION-OF-HUFFMAN-CODING

## Name : Sameer Shariff M
## Reg No : 212224220085
## Date : 07-09-2026

Sure — here is a **complete lab-record version** with the algorithm steps, program, sample output, and result filled in.

## Huffman Coding

### Aim

To implement **Huffman Coding** to compress the data using Python.

### Software Required

1. Anaconda - Python 3.7

## Algorithm

### Step 1:

Get the input string from the user and calculate the **frequency of occurrence** of each character in the string.

### Step 2:

Create a node for each character and its frequency. Store all the nodes in a priority queue based on their frequencies.

### Step 3:

Remove the two nodes with the **lowest frequencies** from the priority queue and create a new node by combining them. Insert the new node back into the priority queue.

### Step 4:

Repeat Step 3 until only one node remains. This node becomes the **root of the Huffman tree**.

### Step 5:

Traverse the Huffman tree by assigning **0 to the left edge** and **1 to the right edge**. The resulting binary codes are the Huffman codes for each character.

## Program

```
# Step 1: Get the input string
input_string = "huffman coding"  # Example input string

# Step 2: Calculate frequency of each character in the input string
frequency = {}
for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1

# Step 3: Create tree nodes
nodes = [[char, freq] for char, freq in frequency.items()]

# Step 4: Main function to implement Huffman coding
while len(nodes) > 1:
    # Sort nodes based on frequency
    nodes = sorted(nodes, key=lambda x: x[1])

    # Pick two smallest nodes
    left = nodes.pop(0)
    right = nodes.pop(0)

    # Create a new node with combined frequency
    new_node = [[left, right], left[1] + right[1]]
    nodes.append(new_node)

# The final node is the Huffman tree
huffman_tree = nodes[0]

# Step 5: Generate Huffman codes
huffman_codes = {}

def generate_codes(tree, code=""):
    if isinstance(tree[0], str):  # If it's a leaf node
        huffman_codes[tree[0]] = code
    else:  # If it's an internal node, recurse
        generate_codes(tree[0][0], code + "0")
        generate_codes(tree[0][1], code + "1")

generate_codes(huffman_tree)

# Step 6: Print the characters and their Huffman codes
print("Character | Huffman Code")
print("-------------------------")
for char, code in huffman_codes.items():
    print(f"    {char}    |    {code}")

```

## Output

### Print the characters and its huffmancode

<img width="263" height="316" alt="image" src="https://github.com/user-attachments/assets/d26a95b0-67ed-47ea-a5d0-663627d25a2e" />


> **Note:** Huffman codes can differ between implementations when characters have equal frequencies, but the coding remains valid.

## Result

Thus, the **Huffman Coding algorithm was successfully implemented using Python to compress the given data**.
