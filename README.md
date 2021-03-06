## Dynamic Enforcement of Knowledge-based Security Policies using Probabilistic Abstract Interpretation [pdf](http://www.cs.umd.edu/~mwh/papers/beliefpol-extended.pdf)

Piotr Mardziel, Stephen Magill, Michael Hicks, Mudhakar Srivatsa

**CSF 2011, JCS 2013 Implementation and experiments**

## Knowledge-Oriented Secure Multiparty Computation [pdf](http://www.cs.umd.edu/~mwh/papers/belief-smc.pdf)

Piotr Mardziel, Michael Hicks, Jonathan Katz, Mudhakar Srivatsa

**PLAS 2012 Implementation and experiments**

### Requirements
  * opam      (available with homebrew)

  * ocaml >= 3.12 (available with opam)
  * ocamlfind (available with opam)
  * camlp5 (available with opam)

  * ppl [http://bugseng.com/products/ppl/download]
    - gmp   (available with homebrew)
    - mpfr  (available with homebrew)
    - mlgmp (available with opam)

  * latte [https://www.math.ucdavis.edu/~latte/software.php]

### Installation

Given instructions are for OSX using homebrew but should be adaptable
to other package managers or source installations.

1. Install homebrew

2. Install opam

   ```bash
   brew install opam
   ```

3. Install ocaml, ocamlfind, camlp5:

   ```bash
   opam switch 4.02.0
   opam install ocamlfind
   opam install camlp5
   ```

   The `4.02.0` above is the ocaml version to install. Just go with the latest available.

4. Install gmp, mpfr, and mlgmp:

   ```bash
   brew install gmp
   brew install mpfr
   opam install mlgmp
   ```

5. Install ppl with ocaml interface enabled [1.1 tarball](http://bugseng.com/products/ppl/download/ftp/releases/1.1/ppl-1.1.tar.gz):

    ```bash
    ./configure --enable-interfaces=ocaml --with-mlgmp=~/.opam/4.02/lib/gmp
    make
    sudo make install
    ```

    ** Warning: ppl's configuration may silently fail when it cannot find
       something it needs (like mlgmp). In those cases it might install
       the main library and even the ocaml interface documentation without
       actually installing the interface itself.**

6. Install latte [1.7.2 tarball](https://www.math.ucdavis.edu/~latte/software/packages/latte_current/latte-integrale-1.7.2.tar.gz):

   ```bash
   ./configure
   make
   ```

   Make latte's `count` and `latte-maximize` available on your path. You
   can do this by making links to `dest/bin/count` and `dest/bin/latte-maximize` like so:

   ```bash
   ln -s /Users/piotrm/Downloads/install/latte-integrale-1.7.2/dest/bin/count /usr/local/bin/count
   ln -s /Users/piotrm/Downloads/install/latte-integrale-1.7.2/dest/bin/latte-maximize /usr/local/bin/latte-maximize
   ```

7. Make prob:

   ```bash
   make prob
   ```

### Running
There are a bunch of examples in `examples/bench` . Some of the
stuff in `examples` proper might be outdated but `bench` should have
mostly working examples. To run you can start with:

  ```bash
  ./prob examples/bench/bday.pol
  ```

Run `./prob --help` to see options.

### Contact
Piotr Mardziel: [piotrm@gmail.com](mailto:piotrm@gmail.com),
[http://www.cs.umd.edu/~piotrm](http://www.cs.umd.edu/~piotrm)
