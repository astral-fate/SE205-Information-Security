I'll explain this key generation process step by step in a simple way, using tables to make it easier to follow.

## Key Generation Process Explained

### Step 1: Starting with the Initial Key
We begin with a 10-bit key: 1010000010

| Position | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|----------|---|---|---|---|---|---|---|---|---|----|
| Bit      | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 0  |

### Step 2: Apply Permutation P10
The P10 permutation rearranges the bits according to this pattern: [3, 5, 2, 7, 4, 10, 1, 9, 8, 6]

This means:
- Position 1 in the new key gets the bit from position 3 in the original key
- Position 2 in the new key gets the bit from position 5 in the original key
- And so on...

| Original Position | 3 | 5 | 2 | 7 | 4 | 10 | 1 | 9 | 8 | 6 |
|-------------------|---|---|---|---|---|----|---|---|---|---|
| Bit from Original | 1 | 0 | 0 | 0 | 0 | 0  | 1 | 1 | 0 | 0 |

So after P10, our key becomes: 1000011000

### Step 3: Split and Left Shift
We split this 10-bit key into two 5-bit halves:
- Left half: 10000
- Right half: 11000

Then we perform a left shift (LS-1) on each half:
- Left half after LS-1: 00001 (rotate left by 1)
- Right half after LS-1: 10001 (rotate left by 1)

### Step 4: Combine After LS-1
We combine the two halves: 00001 + 10001 = 0000110001

### Step 5: Apply Permutation P8
P8 permutation takes 8 specific bits from our 10-bit key according to this pattern: [6, 3, 7, 4, 8, 5, 10, 9]

| Position in 10-bit key | 6 | 3 | 7 | 4 | 8 | 5 | 10 | 9 |
|------------------------|---|---|---|---|---|---|----|---|
| Bit from 10-bit key    | 1 | 0 | 1 | 0 | 0 | 1 | 0  | 0 |

This gives us the first subkey: 10100100

### Step 6: Perform Second Left Shift (LS-2)
We go back to our key from after the first LS-1 (0000110001) and split it again:
- Left half: 00001
- Right half: 10001

Then we perform LS-2 (left shift by 2 positions):
- Left half after LS-2: 00100 (rotate left by 2)
- Right half after LS-2: 00110 (rotate left by 2)

### Step 7: Combine After LS-2
We combine the two halves: 00100 + 00110 = 0010000110

### Step 8: Apply P8 Again
We apply P8 to this new 10-bit key:

| Position in 10-bit key | 6 | 3 | 7 | 4 | 8 | 5 | 10 | 9 |
|------------------------|---|---|---|---|---|---|----|---|
| Bit from 10-bit key    | 0 | 1 | 0 | 0 | 0 | 0 | 1  | 1 |

This gives us the second subkey: 01000011

### Final Result
- First subkey (K1): 10100100
- Second subkey (K2): 01000011

These subkeys are what would be used in the encryption/decryption process.
