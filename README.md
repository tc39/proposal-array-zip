# proposal-array-zip

A TC39 proposal to synchronize the iteration of multiple arrays.

This proposal is based entirely on https://github.com/tc39/proposal-joint-iteration - in other words, this proposal is `Iterator.zip` and `Iterator.zipKeyed` for arrays.

**Stage**: 1

**Specification**: https://ljharb.github.io/proposal-array-zip/

## Motivation / Problem

Despite iterators existing for over a decade, it is still exceedingly common to use - and prefer - arrays over iterators, especially for small finite lists. They're simpler to work with, often more performant, and more broadly compatible with ecosystem libraries.

One can now always turn any iterator into an array with `.toArray()` - which is useful, but not ergnomic, especially when combined with the need to wrap the value in `Iterator.from()` before accessing iterator helpers.

## Solution

Add `Array.zip` and `Array.zipKeyed` static methods to the `Array` constructor.

### Rationales

 - the method names, APIs, and semantics must match https://github.com/tc39/proposal-joint-iteration, to avoid confusion
  - this includes accepting iterables, like `Array.from` and `Array.fromAsync`
 - Adding Array.prototype methods is the most frequent cause of web compatibility issues, and browsers have expressed an unwillingness to even attempt adding more in the future - thus, they must be static
