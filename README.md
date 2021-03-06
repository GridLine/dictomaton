# dictomaton

## Introduction

This Java library implements dictionaries that are stored in finite state
automata. *Dictomaton* has the following features:

 * Finite state dictionaries that implement the Java Set<String> interface.
 * Perfect hash dictionaries, that provide a unique hash for each character
   sequence that is in the dictionary. Perfect hash dictionaries can be used
   in two directions: (1) obtaining the hash code for a character sequence
   and (2) obtaining the character sequence for a hash code.
 * Levenshtein automata, that allow you to efficiently find all the sequences
   in the dictionary that are within the given edit distance of a sequence.
 * String to primitive type mappings, where the keys are stored in a perfect
   hashing automaton and the values in an (unboxed) array.

## Comparisons

The following table compares the sizes of the object graphs of the
<tt>Dictionary</tt> type of this library to that of <tt>TreeSet</tt> and
<tt>HashSet</tt>. The comparisons were obtained by storing all the words
in the *web2* and *web2a* dictionaries and were measured using
[memory-measurer](https://code.google.com/p/memory-measurer/)

<table>
   <tr><th>Data type</th><th>Objects</th><th>References</th><th>char</th><th>int</th><th>boolean</th><th>float</th></tr>
   <tr><td>TreeSet<String></td><td align="right">936277</td><td align="right">1872555</td><td align="right">3193749</td><td align="right">624184</td><td align="right">312091</td><td>0</td></tr>
   <tr><td>HashSet<String></td><td align="right">936277</td><td align="right">1772657</td><td align="right">3193749</td><td align="right">936277</td><td align="right">1</td><td>1</td></tr>
   <tr><td>Dictionary<String></td><td align="right">41188</td><td align="right">94546</td><td align="right">424169</td><td align="right">397033</td><td align="right">1</td><td>1</td></tr>
</table>

## Benchmarks

Benchmarks are in a different test group than normal unit tests. You can run
benchmarks via Maven, adding the Benchmarks group:

    mvn test -Djunit.groups=eu.danieldk.dictomaton.categories.Benchmarks

## Changelog

### 0.0.4

* Added Levenshtein automata for looking up sequences in a <tt>Dictionary</tt> that
  are within a certain edit distance of a sequence.

### 0.0.3

* Fix an off-by-one error in integer width of the state table.

### 0.0.2

* Rename the project from *fsadict-java* to *dictomaton*.
* Store the state and transition tables as packed int arrays, resulting in drastically smaller automata.


## Release plan


 * **0.0.5**: add ImmutableStringStringMap, wherein values are also stored
   in an automaton.
 * **0.0.6**: generic object values.
 * **1.0.0**: first stable release.

Plans for 1.2.0: Perhaps an explicit, fast, and compact data storage format
as an alternative to Java serialization. C or C++ version.
