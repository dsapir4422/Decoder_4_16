# Decoder_4_16
In this project we will show the design of a 4->16 binary decoder with pre-decoder and post-decoder. we will use logical effort to optimize the decoder for a more efficient architecture.

****
## Design and logical effort explained
The basic decoder architecture is 16 4-bits AND gates with 4 inputs for each gate, that gives us high fan-in. 
We can easily replace each of the 4 inputs AND gate with the following - 

<img width="301" alt="image" src="https://github.com/dsapir4422/Decoder_4_16/assets/87266625/ea76d749-ebb8-460e-81ab-f3a72eeb57a4">

Which will give us better fan-in.

For logical effort calculations we know that $LE=(R_{gate}*C_{gate})/(R_{inv}*C_{inv})$, and therefore $LE_{NAND2} = 4/3$, and $LE_{NOT} = 1$ - 

<img width="400" alt="Logical Effort for Simple Gates" src="https://github.com/dsapir4422/Decoder_4_16/assets/87266625/b87b88ab-1786-4459-9dbe-45eeac524636">

So, for an 4-input AND gate implemented as NAND4+NOT2, $LE=2 * 1 = 2$ and for our architecture $LE=(4/3)*(4/3)=1.78$

**Pre/Post-decoding concept**

Explained in "Logical Effort" book by Ivan Sutherland, we can see that between 2 inputs of a decoder we have a shared logic - 
<img width="300" alt="image" align="left" src="https://github.com/dsapir4422/Decoder_4_16/assets/87266625/226ed4af-fba9-4ebc-8120-7b57e4ab7e78">
<img width="310" alt="image" src="https://github.com/dsapir4422/Decoder_4_16/assets/87266625/2387c268-6b74-4910-a46f-95e2adce18c7">

So the basic idea is to actually build two 2->4 pre-decoding circuits and in such a case each one has $2^2$ possible output options. 
We AND each one of the A pre-decoder outputs with each one of B pre-decoder to reach 16 outputs.
And finally we ends up with 24 pairs of NAND+NOT gates - 

<img width="300" alt="image" src="https://github.com/dsapir4422/Decoder_4_16/assets/87266625/5f3fe424-0c70-4fcd-b587-6a7db085c3e3">


**Gates sizing**

We will calculate each gates stage sizing using the general equation - $C_{in,i} = \dfrac{(LE_i * b_i)}{(EF_i)} * C_{in,i+1}$ - 
<img width="600" alt="image" src="https://github.com/dsapir4422/Decoder_4_16/assets/87266625/cece800f-b0ee-454e-900a-f604cc034221">

## Design of logical gates
