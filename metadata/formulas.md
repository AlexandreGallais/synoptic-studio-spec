# Formulas

> [Home](../README.md) › [Metadata](README.md) › Formulas

| Version | Date | Status | Change |
| --- | --- | --- | --- |
| 1 | 2026-11-22 | Draft | Creation of the file, from research T6 |

How the two formulas of a [conversion](entities/11-conversion.md) are written and computed: `to_default` and `from_default`, each a formula in `x`. Every rule of this file comes from the advice of research T6 (`research/t6-recherche-documentaire-conversions-d-unites-tout/rapport.md`, 3.6 to 3.13 and 6, decision 3) and is **proposed**, until the Product Owner validates it.

## Where it is used

| Where | What it takes from here |
| --- | --- |
| [Conversion](entities/11-conversion.md) | The two strings `to_default` and `from_default` follow this syntax. |
| [Quantity](entities/14-quantity.md), its file | The checks of the catalogue below run on every quantity file, shipped or added by the user. |
| [MD-08 · Units](../screens/metadata.md#md-08--units) | The column Formula shows `from_default` of each unit. |
| Presets and typed values (decision 0051) | A value is shown with `from_default` and kept with `to_default`; a difference is computed from them (decision 0050). |

## What a formula holds

| Element | Written | Note |
| --- | --- | --- |
| The variable | `x` | The only name of a value. Any other name is refused; names stay free for parameters, if conversions between quantities come one day (research T6, decision 1). |
| Numbers | `0.45359237`, `1609.344`, `1.4e3`, `22e-3` | Decimal point only, exponent with `e`; no thousands separator, no decimal comma (the file is JSON). |
| Constants | `pi`, `e` | Only these two. A constant of definition (g₀ = 9.80665, 0.45359237 for the pound) is written in figures. |
| Operators | `+` `-` `*` `/` `^`, and `-` before a value | `^` is the power. |
| Functions | `sqrt` `exp` `ln` `log10` `log2` `tan` `atan` | One argument each, in parentheses; angles in radians. |
| Parentheses | `( )` | Group as usual. Spaces are ignored. |

Nothing else: no sine or cosine, no absolute value, no rounding, no minimum or maximum, no condition, no comparison. No conversion read by research T6 needs them (3.6).

### The functions

| Function | Gives | Defined for | A conversion that needs it |
| --- | --- | --- | --- |
| `sqrt(a)` | the square root of `a` | `a ≥ 0` | square-root scaling |
| `exp(a)` | e to the power `a` | every `a` | back from the neper |
| `ln(a)` | the natural logarithm of `a` | `a > 0` | neper |
| `log10(a)` | the decimal logarithm of `a` | `a > 0` | bel, decibel, pH |
| `log2(a)` | the binary logarithm of `a` | `a > 0` | octave |
| `tan(a)` | the tangent of `a` | `a` not on π/2 + kπ | slope in percent |
| `atan(a)` | the arc tangent of `a`, between −π/2 and π/2 | every `a` | back from the slope |

`log` alone is refused: it means the natural logarithm in some tools and the decimal one in others (research T6, 3.9).

## Priority and reading order

The rows go from the weakest to the strongest: an operator lower in the table is computed first.

| Operators | Read | Example |
| --- | --- | --- |
| `+` `-` | from left to right | `x - 32 + 1` is `(x - 32) + 1` |
| `*` `/` | from left to right | `x * 5 / 9` is `(x * 5) / 9` |
| `-` before a value | — | `-x` |
| `^` | from right to left | `2^3^2` is `2^(3^2)`, 512 |
| a function, parentheses | first | `10^(x / 10)` |

## Refused forms

Each is refused with a message that says how to write it.

| Written | Why | Write instead |
| --- | --- | --- |
| `-x^2` | Read −(x²) by Python and −x squared by Excel's order: a minus sign directly before a power is ambiguous | `-(x^2)` or `(-x)^2` |
| `2x`, `2(x + 1)`, `2 pi` | No implied multiplication | `2 * x` |
| `x**2` | One power operator only | `x^2` |
| `log(x)` | Ambiguous | `ln(x)` or `log10(x)` |
| `Math.PI`, `y`, `t` | Unknown name | `pi`, `x` |
| `1,5` | Decimal comma | `1.5` |

A negative exponent stays allowed when nothing follows it: `10^-3`.

## Grammar

The grammar in EBNF; the rule against a minus sign before a power, above, is checked on top of it.

```mermaid
railroad-ebnf-beta
formula = sum ;
sum = product , { ( "+" | "-" ) , product } ;
product = unary , { ( "*" | "/" ) , unary } ;
unary = "-" , unary | power ;
power = primary , [ "^" , exponent ] ;
exponent = "-" , exponent | primary , [ "^" , exponent ] ;
primary = number | "x" | "pi" | "e" | function , "(" , sum , ")" | "(" , sum , ")" ;
function = "sqrt" | "exp" | "ln" | "log10" | "log2" | "tan" | "atan" ;
number = digits , [ "." , digits ] , [ "e" , [ "+" | "-" ] , digits ] ;
digits = digit , { digit } ;
digit = "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9" ;
```

- An `e` right after digits starts an exponent (`1.4e3`); an `e` alone is the constant.
- Names are in lower case.

## Numbers and precision

- Values are computed in double-precision floats, as JavaScript numbers; no exact fractions.
- An exact fraction is written as a division, `5 / 9`, never as a cut decimal: `0.5555555556 * 9` gives 5.0000000004 (research T6, 3.8).
- The order of the operations may change the last digit only (`x * 5 / 9` and `x * (5 / 9)` differ there); the display rounds it away.

## Computing a formula

- **No `eval` and no `new Function`**: a formula is read by a parser of its own into a tree, then the tree is computed. A quantity file may come from a third party (decisions 0069, 0071): a formula is never run as code.
- **Read once, computed often**: every formula is parsed when the catalogue is read, and the tree is kept for its unit. The POCs measure the cost of a conversion per shown value against the 8.3 ms of a frame (criterion C15).
- **A parser written for the project**, on the grammar above (research T6, decision 3, option D): no dependency, exactly the list of this file, and its own messages. Second option: jsep for the parsing, with an evaluator of the project and a white list of operators and functions. The two most complete libraries (math.js, expr-eval) had a code-execution flaw in 2025–2026.
- **A result that is not a number** (NaN, or ±Infinity, as `log10(0)` gives) is never shown as a number. What is shown instead is open (below).

## Checks of the catalogue

Run on every quantity file when it is read, and by the tests of the shipped catalogue.

1. Each formula follows the grammar and the refused forms; its only name is `x`.
2. **Round trip**: on a sample of values in the domain of the unit, `from_default(to_default(x))` gives `x` back within a relative tolerance of 1e-9 (the default of PEP 485; research T6, 3.11). °F → K → °F passes on 100,000 values from −459 to 911, with a largest relative error of 1.2 × 10⁻¹¹.
3. **Multiplies then shifts**, for a quantity with `offers_relative_quantity`: `to_default(x) − to_default(0)` equals `k · x`, with `k = to_default(1) − to_default(0)`, on the same sample (decision 0050).
4. The same tolerance compares two units of equal step when they are sorted ([Unit system](entities/13-unit-system.md)).

## Examples

| Unit (default unit) | `to_default` | `from_default` |
| --- | --- | --- |
| pound (kilogram) | `x * 0.45359237` | `x / 0.45359237` |
| mile (metre) | `x * 1609.344` | `x / 1609.344` |
| degree Fahrenheit (kelvin) | `(x + 459.67) * 5 / 9` | `x * 9 / 5 - 459.67` |
| decibel-milliwatt (milliwatt) | `10^(x / 10)` | `10 * log10(x)` |
| slope in percent (degree of angle) | `atan(x / 100) * 180 / pi` | `100 * tan(x * pi / 180)` |
| litre per 100 km (kilometre per litre) | `100 / x` | `100 / x` |

## Open questions

- What the synoptic shows, and what a typed value does, outside the domain of a formula (research T6, 3.10): a domain written in the catalogue for each conversion (D1), a check of the result only (D2), or the value brought back to a bound (D3).
- The absolute tolerance of the round trip near zero, where a relative tolerance alone fails (PEP 485).
- Scales defined by tables (hardness): out of these formulas; whether they enter the catalogue (research T6, open question 2).
