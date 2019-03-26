# Spindex
#### About
A project to catch, store, and document all every pattern of Spinda (i.e. catch a Spinda of every single personality value.)

#### General Method
- Script running on my Emerald save.
- Farms money somehow (Hardest part)
- Buys many repeat balls
- Goes to desert encounters wild pokemon.
- Records if it was a Spinda or not, and if it was a duplicate Spinda (for interesting data analysis later).
- If its a non-duplicate Spinda, keep throwing repeat balls until it is caught.
- Once caught add its PV to the bitmap and name the Spinda the Hexadecimal form of its PV.
- Rinse and repeat until max # of pokemon are in boxes.
- Have these pokemon be dumped from save file.
- Continue until out of repeat balls.

#### Storage Req.
- Gen 3 PKM files are $100$ bytes.
- Personality values are $32$ bit integers. This means $2^{32}=4294967296$ Spindas, one for each personality value.

$$2^{32}100 \text{ B}\approx429.49673\text{ GB}\approx430\text{ GB}$$

#### Tracking Duplicates
To track duplicates, immediately store PV of each caught Spinda in a **bitmap**. Whenever a new Spinda is caught, we check its personality value against the bitmap and

#### Probability of Duplicates
If we record how many duplicates and it doesn't agree with calculations based on perfect RNG to within some sigma, we can say with the same certainty that the Higgs Boson was found that the PRNG of Pokémon Emerald running on the Nintendo Gameboy Advance is flawed. A huge surprise I know.

#### Encryption Constant
In newer pokemon titles (generation VI and further), Spinda's spots are no longer determined by its PV but by a value known as it's **Encryption Constant**. This is not a problem for us however, as the encryption constant of pokemon transferred from older titles (Gen III to V)  to newer ones (Gen VI and above) is simply set to their PV upon transfer. Thus the spots of our 4.2 billion Spinda are still totally determined by their PV, and those 4.2 billion Spinda still represent all possible Spinda pattern configurations (since the encryption constant is also a 32 bit integer).

#### Visual Duplicates
In practice there are a bit fewer than $2^{32}$ different observable Spinda patterns because of the possibility of some of the spots overlapping with each other. Finding which personality values correspond with this probably isn't too difficult, but it would depend on which game the Spinda is being rendered in and how it displays its spots. As such, we simply make it our goal to catch all PV's of Spinda to deal with different spot rendering schemes as well as the odd hole in our Spindex where those overlapping Spinda would be.
