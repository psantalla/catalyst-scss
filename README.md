# Catalyst SCSS

A lightweight, extensible system for generating CSS variables and utility classes for typography, color, and spacing.

Catalyst SCSS gives you a small SCSS core that compiles into a clean, scalable style layer. You define tokens once and everything else is generated from there with consistent naming and predictable output. No framework lock-in, just structured CSS.

## What it covers

- Typography with a fluid `clamp()` scale
- Color tokens with automatic opacity variants
- Spacing scale with responsive overrides
- Utility classes mapped to real CSS properties
- Centralized breakpoints reused across systems

## Foundations

Catalyst SCSS is meant to keep design and implementation speaking the same language. The compiled CSS isn’t trying to be clever — it’s trying to be stable, readable, and easy to evolve.

You work from token maps. Change a value there, recompile, and the system updates everywhere those tokens are used. That keeps iteration cheap even when the project is already large.

## Quick setup

1. Drop the SCSS files into your project.
2. Adjust the token maps (colors, spacing, type scale, breakpoints).
3. Compile SCSS to CSS.
4. Start using the generated variables and utility classes in your markup.

## How it works

Everything starts from SCSS maps. Colors, spacing sizes, typography steps, and breakpoints are defined once. Loops generate CSS variables in `:root`, then utility classes that point to those variables.

Responsive behavior mostly overrides variables instead of duplicating whole rule sets. That keeps the CSS smaller and easier to reason about.

Typography sizes are calculated, not hardcoded, using ratios and viewport bounds.

## Variables and naming (quick orientation)

You don’t need to memorize everything — just the prefixes.

Examples you’ll see in the output:

- `--c-primary` → color token  
- `--sp-l` → spacing token  
- `--t-s-xl` → type size token  

Utilities follow the same idea:

- `.c-bg-primary` → background color
- `.sp-m-l` → margin
- `.t-s-xl` → font size step

> Use an IDE with autocomplete. Once you remember the prefixes (`c-`, `sp-`, `t-`), suggestions do the rest.

## Color system

Colors are defined once in a map. Opacity variants are generated automatically from those base values.

From that, Catalyst outputs CSS variables and small utility classes for text color, background color, and border color. You can also assign default colors to base elements through a selector map.

## Spacing system

Spacing comes from a size scale map. Those values become spacing variables and margin/padding/gap utilities.

Tablet and mobile breakpoint blocks override selected spacing tokens, so the same utility class adapts without redefining it everywhere.

There are also max-width helpers based on a site-width variable, useful for layout containers.

## Breakpoints

Breakpoints live in a single SCSS map and are reused across media queries. Change them once and every dependent rule follows. No scattered magic numbers.

## Typography system

Typography is built on a modular scale with fluid sizing. A function calculates each step using min/max sizes and viewport ranges, then outputs `clamp()` values.

Each step can be linked to HTML elements and bundled with style tokens like line-height, weight, and font family. You get both element defaults and utility classes for manual control.

Extra small helpers are included for text alignment, wrapping, and headline patterns.