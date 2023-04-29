import re

def prepare_message(message):
    """Prepares the message by converting to uppercase and removing non-alphabetic characters."""
    message = message.upper()
    message = re.sub(r'[^A-Z]', '', message)
    return message

def generate_playfair_table(keyword):
    """Generates the Playfair table using the given keyword."""
    # Convert the keyword to uppercase and remove duplicate letters
    keyword = keyword.upper()
    keyword = ''.join(sorted(set(keyword), key=keyword.index))
    
    # Create the initial Playfair table with the keyword
    table = [list(keyword)]
    
    # Fill the remaining cells with the remaining letters of the alphabet
    alphabet = 'ABCDEFGHIKLMNOPQRSTUVWXYZ'
    for letter in alphabet:
        if letter not in keyword:
            table[-1].append(letter)
            if len(table[-1]) == 5:
                table.append([])
    
    return table

def get_char_positions(table, char):
    """Gets the row and column positions of a character in the Playfair table."""
    row = None
    col = None
    for i in range(5):
        for j in range(5):
            if table[i][j] == char:
                row = i
                col = j
                break
        if row is not None:
            break
    
    return row, col

def decrypt_playfair(message, keyword):
    """Decrypts a Playfair cipher message using the given keyword."""
    # Prepare the message and generate the Playfair table
    message = prepare_message(message)
    table = generate_playfair_table(keyword)
    
    # Split the message into pairs of letters and decrypt each pair
    pairs = re.findall(r'(?i)([A-Z])([A-Z])', message)
    plaintext = ''
    for pair in pairs:
        char1, char2 = pair
        row1, col1 = get_char_positions(table, char1)
        row2, col2 = get_char_positions(table, char2)
        if row1 == row2:
            plaintext += table[row1][(col1 - 1) % 5] + table[row2][(col2 - 1) % 5]
        elif col1 == col2:
            plaintext += table[(row1 - 1) % 5][col1] + table[(row2 - 1) % 5][col2]
        else:
            plaintext += table[row1][col2] + table[row2][col1]
    
    return plaintext

# Example usage
message = 'KXJEY UREBE ZWEHE WRYTU HEYFS KREHE GOYFI WTTTU OLKSY CAJPO BOTEI ZONTX BYBNT GONEY CUZWR GDSON SXBOU YWRHE BAAHY USEDQ'
keyword = 'PLAYFAIR'
plaintext = decrypt_playfair(message, keyword)
print(plaintext)
