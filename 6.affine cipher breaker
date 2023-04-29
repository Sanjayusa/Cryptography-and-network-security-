def mod_inverse(a, m):
    """
    Calculates the modular multiplicative inverse of a mod m using the extended Euclidean algorithm.
    """
    if a < 0:
        a += m
    x, y, gcd = 0, 1, m
    while a != 0:
        q, r = gcd // a, gcd % a
        gcd, a = a, r
        x, y = y - q * x, x
    if gcd == 1:
        return y % m
    else:
        return None

def affine_break(ciphertext, first_most_freq, second_most_freq):
    """
    Breaks an affine cipher when given the most frequent letter and the second most frequent letter of the ciphertext.
    """
    alphabet = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
    freq_dict = {}
    for letter in ciphertext:
        if letter in freq_dict:
            freq_dict[letter] += 1
        else:
            freq_dict[letter] = 1
    sorted_freq = sorted(freq_dict.items(), key=lambda x: x[1], reverse=True)
    a = (alphabet.index(first_most_freq) - alphabet.index(second_most_freq)) * mod_inverse(alphabet.index('E') - alphabet.index('A'), 26) % 26
    b = alphabet.index(first_most_freq) - a * alphabet.index('A')
    plaintext = ''
    for letter in ciphertext:
        if letter in alphabet:
            plaintext += alphabet[(mod_inverse(a, 26) * (alphabet.index(letter) - b)) % 26]
        else:
            plaintext += letter
    return plaintext

#
