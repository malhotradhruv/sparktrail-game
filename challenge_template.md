# Challenge Template

## Title
C1: Caustic Mirror

## Story
A corrupted photon bounces through a caustic mirror array, twisting its signal as it reflects across fractured optics.

## Challenge Description
Players receive a damaged binary packet from a mirror node. They must restore the original signal by applying the correct transformation rule and recover the first fragment of the flag.

## Input
- File type: `binary.txt`
- Sample data:
  ```
  11010011
  ```

## Rules Applied
- `R1: REFLECT` → invert bits
- Use the rulebook's reflection rule to return the signal to its original form.

## Solving Path
1. Identify that the corrupted data is a binary stream.
2. Recognize the challenge title and optics theme as pointing to `REFLECT`.
3. Invert each bit in the input.
4. Extract the partial flag fragment from the corrected output.

## Wrong Approaches
- Trying a Caesar shift on binary data.
- Treating the input as text instead of bits.
- Applying XOR merge or merge operations prematurely.

## Expected Solve Time
10-15 minutes

## Output
- Partial flag: `SPK{M1RR0R}`
- Hidden Roman numeral: `I`
