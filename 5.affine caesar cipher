def gcd(a, b):
    while b:
        a, b = b, a % b
    return a

def is_allowed(a):
    return gcd(a, 26) == 1

def affine_caesar_cipher(a, b, plaintext):
    ciphertext = ""
    for p in plaintext:
        if p.isalpha():
            if p.islower():
                p = ord(p) - ord('a')
                c = (a * p + b) % 26
                c = chr(c + ord('a'))
            else:
                p = ord(p) - ord('A')
                c = (a * p + b) % 26
                c = chr(c + ord('A'))
        else:
            c = p
        ciphertext += c
    return ciphertext

# Test the affine Caesar cipher for a = 2 and b = 3
plaintext = "hello world"
a = 2
b = 3
ciphertext = affine_caesar_cipher(a, b, plaintext)
print("Plaintext:", plaintext)
print("Ciphertext:", ciphertext)

# Check which values of a are allowed
for a in range(1, 26):
    if is_allowed(a):
        print("a =", a, "is allowed")
    else:
        print("a =", a, "is not allowed")
