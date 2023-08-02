## Task :
A notorious organization, "The Enigma Syndicate," has sent encrypted messages detailing a dark conspiracy. Participants must tackle their binary cryptogram using powerful reverse engineering tool to reveal the sinister plot. Unravel the enigma, stop the conspiracy, and become the ultimate codebreaker in this thrilling CTF challenge!

[Engima_Binary](Resources%20provided/Enigma_Binary)

## Points :250

## Solution :
<ol>
  <li>Download and install Ghidra</li>
  <li>Create a new Project and add the Enigma file to it</li>
  <li>Double click on it and wait for it to decompile and anlyze the file</li>
  <li>Analyze the source code (specifically the main () function) <b>you should notice a strcmp and a string  "error" and a if block next to it</b></li>
  <li><pre>
    iVar1 = strcmp(*(char **)(param_2 + 8),"error");
        if (iVar1 == 0) {
      local_b8 = 0x3533453235333833;
      local_b0 = 0x4432423037334133;
      local_a8 = 0x3135363142314531;
      local_a0 = 0x3531373033343735;
      local_98 = 0x3934373542353736;
      local_90 = 0x3331363032353631;
      local_88 = 0x4630433344344335;
      local_80 = 0x3730413445344435;
      local_78 = 0x3031333537343235;
      local_70 = 0x3041354433;
      uStack_6b = 0x453430;
      uStack_68 = 0x38314134;
      local_63 = 0x5f746572636573;
      uStack_5c = 0x79656b;
      local_48 = 0x2a;
      local_50 = 0x2a;
      local_58 = auStack_f8;
      for (local_40 = 0; local_40 < local_48; local_40 = local_40 + 1) {
        __isoc99_sscanf((long)&local_b8 + local_40 * 2,"%2hhx",local_58 + local_40);
      }
      local_58[local_48] = 0;
      xor_cipher(local_58,local_48,&local_63,10);
      fprintf(stderr,"Decrypted Flag: %s\n",local_58);
      return 1;
    }
    
  </pre></li>
  <li>All this code does is check wether or not the program  has the argument "error" when executed.If it has it simply decrypts and prints the Flag   </li>
  <li>So finally we get the Flag by executing the binary like this  <pre> ./Enigma_Binary error</pre></li>
</ol>

```bash
./Enigma_Binary "error"
Decrypted Flag: KPMG_CTF{be441ba8020e7ea99cd879b156db1e79}
```

Alternative Method to Solve using [Binary Ninja Cloud](https://cloud.binary.ninja/) -> [Binary Cryptography - Unravel the Engima](https://github.com/shashankk90/Writeups/blob/master/KPMG/Binary%20Cryptogram%20-%20Unravel%20the%20Enigma.md)