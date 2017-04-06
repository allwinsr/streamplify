[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://github.com/beryx/streamplify/blob/master/LICENSE)
[![Build Status](https://img.shields.io/travis/beryx/handlebars-java-helpers/master.svg?label=Build)](https://travis-ci.org/beryx/streamplify)
## Streamplify ##


The goal of this library is to provide useful Java 8 streams and to assist you in building new streams that allow efficient parallel processing.

The utilities offered by Streamplify include:

- combinatorics streams: permutations, combinations, Cartesian products, power sets, derangements, partial permutations.
- classes that help you implement your own efficient parallel streams.

**Example**

The following code snippet uses a parallel permutation stream to find all solutions of the [N-Queens problem](https://en.wikipedia.org/wiki/Eight_queens_puzzle) for n = 10.
```
System.out.println(new Permutations(10)
        .parallelStream()
        .filter(perm -> {
            for(int i = 0; i < perm.length - 1; i++) {
                for(int j = i + 1; j < perm.length; j++) {
                    if(Math.abs(perm[j] - perm[i]) == j - i) return false;
                }
            }
            return true;
        })
        .map(perm -> IntStream.range(0, perm.length)
                .mapToObj(i -> "(" + (i + 1) + "," + (perm[i] + 1) + ")")
                .collect(Collectors.joining(", ")))
        .collect(Collectors.joining("\n")));
```


Before starting to use the library, take a look at the **[examples](streamplify-examples/src/main/java/org/beryx/streamplify/example)**, read the **[documentation](http://streamplify.beryx.org)** and consult the **[javadoc](http://streamplify.beryx.org/releases/latest/javadoc)**.

Streamplify is available in [Maven Central](http://search.maven.org/#search%7Cga%7C1%7Cg%3A%22org.beryx%22%20AND%20a%3A%22streamplify%22) and [JCenter](https://bintray.com/beryx/maven/streamplify).

**Contribute to this project!**

We accept all types of contributions and we are very welcoming to first time contributors.

Read **[how to contribute](CONTRIBUTING.md)** and jump in!
