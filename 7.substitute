ciphertext = "53‡‡†305))6*;4826)4‡.)4‡);806*;48†8¶60))85;;]8*;:‡*8†83(88)5*†;46(;88*96*?;8)*‡(;485);5*†2:*‡(;4956*2(5*—4)8¶8*;4069285);)6†8)4‡‡;1(‡9;48081;8:8‡1;48†85;4)485†528806*81 (‡9;48;(88;4(‡?34;48)4‡;161;:188;‡?"

# Frequencies of all characters in the ciphertext
char_freq = {}
for char in ciphertext:
    if char in char_freq:
        char_freq[char] += 1
    else:
        char_freq[char] = 1

# Character that appears most frequently in the ciphertext
most_freq_char = max(char_freq, key=char_freq.get)

# Character that appears second most frequently in the ciphertext
char_freq[most_freq_char] = 0
second_most_freq_char = max(char_freq, key=char_freq.get)

# Decipher 'e' character
e_char = chr(ord(most_freq_char) ^ ord('e') ^ ord(second_most_freq_char))

# Decipher 't' character
t_char = chr(ord('h') ^ ord(most_freq_char) ^ ord(e_char))

# Decipher 'h' character
h_char = chr(ord('t') ^ ord(most_freq_char) ^ ord(e_char))

# Replace the three characters with their decrypted versions
decrypted_ciphertext = ""
for char in ciphertext:
    if char == most_freq_char:
        decrypted_ciphertext += 'e'
    elif char == t_char:
        decrypted_ciphertext += 't'
    elif char == h_char:
        decrypted_ciphertext += 'h'
    else:
        decrypted_ciphertext += char

# Print the decrypted ciphertext
print(decrypted_ciphertext)
