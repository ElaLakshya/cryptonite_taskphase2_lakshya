# Let's see how the code is made

we are given the values of a, b, the list of ciphered text.

The text is ciphered in the manner that the unicode of the character is multiplied
by a given key and then multiplied by 311.

The values of key is as follows

```
p = 97
g = 31


a = randint(p-10, p)
b = randint(g-10, g)


u = generator(g, a, p)
v = generator(g, b, p)
key = generator(v, a, p)
b_key = generator(u, b, p)
shared_key = None
```

According to the following code,
```
if key == b_key:
    shared_key = key
else:
    print("Invalid key")
    return
```
program can move only if key==b_key

That means 
[key = generator(v, a, p)]==
[b_key = generator(u, b, p)] or in other words, ```(v^a)%p == (u^b)%p```

Replacing the values of v and u, we get 
```
(((g^b)%p)^a)%p == (((g^a)%p)^b)%p
```

Moreover, the text is encoded with XOR dynamic encrypryion.

```
def dynamic_xor_encrypt(plaintext, text_key):
    cipher_text = ""
    key_length = len(text_key)
    for i, char in enumerate(plaintext[::-1]):
        key_char = text_key[i % key_length]
        encrypted_char = chr(ord(char) ^ ord(key_char))
        cipher_text += encrypted_char
    return cipher_text
```

This function can reobtain it's original text by using the output provided, but reversed, and further reversing the output thus obtained.

The value of a and b is given.

The given list of numbers is ord(str)*key *311

So on dividing by 311, then key=12, we get an ordinal that we convert to character format.

### Role of XOR

What xor does is repeat the key on the plaintext provided and applies a function to encrypt it's code. The property of XOR is that it is reversible. that is, if you put the output back, it will rereturn the input

So the key_text plays the role of repeating the iteration for the given text series. We know our flag is of the format picoCTF{, so putting that as text_key, we are supposed to get the key needed to be run over to get the flag.

On doing so, we get the value "aedurtu". This is the key we need to run on the entire cipher text.

We should get the intended flag.

```
def generator(g, x, p):
    return(pow (g, x))%p

def dynamic_xor_encrypt2(plaintext):
    text_key="aedurtu"    
    cipher_text=""
    key_length = len(text_key)
    keylog=""
    for i, char in enumerate(plaintext[::-1]):
       key_char = text_key[i % key_length]
       keylog+=key_char
       encrypted_char = chr(ord(char) ^ ord(key_char))
       cipher_text += encrypted_char
    print(f"{cipher_text},")
    print(keylog)
```
The Keylog variable allows us to keep track of the repitition of characters.

### Given
p=97

g=31

a=94

b=29

cipher=[260307, 491691, 491691, 2487378, 2516301, 0, 1966764, 1879995, 1995687, 1214766, 0, 2400609, 607383, 144615, 1966764, 0, 636306, 2487378, 28923, 1793226, 694152, 780921, 173538, 173538, 491691, 173538, 751998, 1475073, 925536, 1417227, 751998, 202461, 347076, 491691]

```
v=generator(g,b,p)
key=generator(v,a,p)
print(key)

decipher=""

for c in cipher:
    decipher+=chr(c//311//key)
print(dynamic_xor_encrypt2(decipher))

```


## Output
```
93
aedurtuavxeiXLxz&c+FA{Z,"+Cja`,
picoCTF{picoCTF{picoCTF{picoCTF{pi
None

==== RESTART: C:/Users/ElaYTurbo/Desktop/TurboFile/Projects/Crypto/test2.py ====
93
picoCTF{custom_d2cr0pt6d_751a22dc},
aedurtuaedurtuaedurtuaedurtuaedurt
None
```
