# Java

Analysing the source code provided, we can see that 

The password that the user inputs should be 
start with picoCTF{.

We can see that there is a buffer defined which is input 
between specific intervals by reshuffling the inputted password.

So let's focus on the shuffling part of the program.

```
 public boolean checkPassword(String password) {
        if (password.length() != 32) {
            return false;
        }
        char[] buffer = new char[32];
        int i;
        for (i=0; i<8; i++) {
            buffer[i] = password.charAt(i);
        }
        for (; i<16; i++) {
            buffer[i] = password.charAt(23-i);
        }
        for (; i<32; i+=2) {
            buffer[i] = password.charAt(46-i);
        }
        for (i=31; i>=17; i-=2) {
            buffer[i] = password.charAt(i);
        }
        String s = new String(buffer);
        return s.equals("jU5t_a_sna_3lpm18g947_u_4_m9r54f");
    }
```

We can see that iteration occurs on the fixed intervals with a simple 
shuffling code for each which is reversible.

For example, pass=abcdefghij , buffer=""

till "d", buffer=pass, till h, beffer=pass[h-..] etc

This way password will eventually look like abcdhgfe... same way if we input this 
new thing back, it will be abcdefh again.

Same way this program works.

So we can make this program to edit and print the buffer 
value after the password checking. Since the program checks the password to be

picoCTF{jU5t_a_sna_3lpm18g947_u_4_m9r54f}, we should input something that makes the shuffling look like this.

So as we discussed, we can reverse by inputting the same string.

On passing picoCTF{jU5t_a_sna_3lpm18g947_u_4_m9r54f}

We get jU5t_a_s1mpl3_an4gr4m_4_u_79958f

Hence the answer

**picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_79958f}**
