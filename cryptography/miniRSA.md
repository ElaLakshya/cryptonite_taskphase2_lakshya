# Encrypting this

I had to study a little about RSA to do this. There is a public and a private key. Everyone has one. We send an encrypted file using our private key encryption and send it to the reciever usimg their public key.

To solve this challenge,

We know n= product of two prime numbers, e is the exponent the the ciphered text is raised to and c is the ciphered text

The formula used in this is

```c= (m^3) mod n```

Since we can see n is very greater than c and the value of e is very small as well, we can assume ```c=m^3```

Therefore, ```m=c^1/3```

m=(2205316413931134031074603746928247799030155221252519872649649212867614751848436763801274360463406171277838056821437115883619169702963504606017565783537203207707757768473109845162808575425972525116337319108047893250549462147185741761825125)^1/3

=13016382529449106065894479374027604750406953699090365388202874238148389207291005

So this is a long int, let's convert it into bytes.
```
long = 13016382529449106065894479374027604750406953699090365388202874238148389207291005

size = (long_integer.bit_length() + 7) // 8 #(To keep atleast one size ahead)

byte = int.to_bytes(size, byteorder='big')

print(byte)
```

We get **picoCTF{n33d_a_lArg3r_e_606ce004}**
