## EXP-11 Huffman-Coding
### Aim :
To implement Huffman coding to compress the data using Python.

### Software Required :
1. Anaconda - Python 3.7

### Algorithm :
#### Step 1 :
Count the frequency of each character in the input string and store in a dictionary.
#### Step 2 :
Create leaf nodes for each character with its frequency and store them in a list.
#### Step 3 :
Build the Huffman tree: repeatedly merge the two nodes with the lowest frequencies into a new node until only one tree remains.
#### Step 4 :
Generate Huffman codes recursively: assign '0' for left branches and '1' for right branches, storing codes for each leaf character.
#### Step 5 :
Display the Huffman codes for all characters in a tabular format.
 
### Program :

``` Python
# Get the input String
input_string = "NITHYA"
frequency = {}
for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1

# Create tree nodes
nodes = [[char, freq] for char, freq in frequency.items()]
while len(nodes) > 1:
    nodes = sorted(nodes, key=lambda x: x[1])
    left = nodes.pop(0)
    right = nodes.pop(0)
    new_node = [[left, right], left[1] + right[1]]
    nodes.append(new_node)
huffman_tree = nodes[0]

# Calculate frequency of occurrence
huffman_codes = {}
def generate_codes(tree, code=""):
    if isinstance(tree[0], str):  # If it's a leaf node
        huffman_codes[tree[0]] = code
    else:  
        generate_codes(tree[0][0], code + "0")
        generate_codes(tree[0][1], code + "1")
generate_codes(huffman_tree)


# Print the characters and its huffmancode
print("Character | Huffman Code")
print("-------------------------")
for char, code in huffman_codes.items():
    print(f"    {char}    |    {code}")
```

### Output :
<img width="261" height="185" alt="image" src="https://github.com/user-attachments/assets/284ecdcf-31bc-4be2-87d9-ec05d8b30dc2" />

### Result :
Thus the huffman coding was implemented to compress the data using python programming.
