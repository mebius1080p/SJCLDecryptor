# SJCL Decryptor (C#)
## Description
This is SJCL decrypt library in C# version.  
The code is based on SJCL itself. (direct porting)  
So, you can find very similar code in the .cs file.
This version is compatible with SJCL 2012/7/25 version.

I had been googling for the way to decrypt SJCL JSON string in C#,
 and reached to StackOverFlow's post.
But with Bouncy Castle, I couldn't decrypt JSON string (and maybe you too).  
So, I made this library.  
This library require SJCL Helper library by turtur.  
PBKDF2HMACSHA256.cs and BinaryNotationConverter.cs.  
Thanks turtur!
## About 2 files
This library has 2 files.  
SJCLDecryptor.cs is main library.  
SJCLAESTables.cs is modified pre-computed table by Bouncy Castle.  
I have modified this table because SJCL pre-computed table is
 different from Boucy Castle's one.
## Prepare
1. Add these library (4 files) to your project.
2. Add reference "System.Runtime.Serialization". (for decoding JSON)
3. Write "using MebiusLib" to your cs file.(or modify namespace)

## How to use
```
string json = "{"iv":xxx...}"; //JSON string from sjcl  
string password = "password"; //password string  
SJCLDecryptor sd = new SJCLDecryptor(json, password);  
string decodedString = sd.Plaintext;
```
## Attention
I didn't check behavior with authentication tag because I always use sjcl with ["adata":""].  
If you want CCM's authentication functionality, you may need to modify this library.