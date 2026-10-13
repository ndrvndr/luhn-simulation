# Luhn Algorithm Simulation

An interactive, single-page simulation of the Luhn algorithm. Type a number and see which digits are doubled, what the total is, and why the number is valid or not.

**Live demo:** [ndrvndr.github.io/luhn-simulation](https://ndrvndr.github.io/luhn-simulation/)

**Article:** [andreavindra.is-a.dev/blog/luhn-algorithm-typescript-experiments](https://andreavindra.is-a.dev/blog/luhn-algorithm-typescript-experiments)

## Features

- **Validate mode:** shows the calculation for every digit, counted from the right, with the doubled digits highlighted.
- **Generate mode:** computes the check digit for a number that does not have one yet.
- **Built-in examples**, including `42093` and `42903`. They differ by a swap of `09` and `90`, a mistake that Luhn cannot detect, so both pass.
- **Private by design:** everything runs in your browser and nothing is sent anywhere.
- **Responsive**, with light and dark themes that follow your system setting.

## How the Luhn algorithm works

To validate a number:

1. Start from the rightmost digit (the check digit) and move left.
2. Do not double the rightmost digit. Double every second digit after it.
3. If a doubled value is greater than 9, subtract 9.
4. Add up all the resulting digits.
5. If the total is divisible by 10 (total mod 10 = 0), the number is valid.

To generate a check digit, apply the same steps to the payload, but start by doubling its rightmost digit. The check digit is `(10 - (sum mod 10)) mod 10`.

## Run locally

There is no build step and no dependencies. Open `index.html` in your browser, or serve the folder with Bun:

```bash
bunx serve
```

Then open the address printed in the terminal (usually http://localhost:3000).

## Project structure

```
.
├── index.html   # the whole app: HTML, CSS, and JavaScript in one file
└── README.md
```

## Companion script

The error-detection experiments comparing Luhn, Damm, and Verhoeff are in a single TypeScript file:
[luhn-damm-verhoeff-compare.ts](https://gist.github.com/ndrvndr/132d8d2c98abec6e348da7c12784e748)

```bash
bun luhn-damm-verhoeff-compare.ts
```

## Disclaimer

This project is for learning. Luhn is a typo check, not a security mechanism, and passing it does not mean a number is real. Do not enter real card numbers. If you need examples, use the test numbers published by payment providers, such as `4242 4242 4242 4242`.
