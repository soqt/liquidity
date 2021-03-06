
Installation
============

Installation from Sources
-------------------------

To install Liquidity from sources, you will need a working
installation of OCaml with `OPAM
<http://opam.ocaml.org/doc/2.0/Install.html>`__ at least version 2.0.

As of Aug 15, 2018, the following process should work:

1. Create an OPAM switch called ``liquidity``, with version 4.06.1 of OCaml::
     
    opam switch create liquidity 4.06.1

  This command should take some time to compile the OCaml distribution.
  Everytime you want to use this switch in a terminal, you should use
  the following command::

    eval `opam env --switch liquidity`
    
2. Checkout the Github repository::
     
    git clone https://github.com/OCamlPro/liquidity
    cd liquidity
    
  This command should create a ``liquidity`` directory with the ``next`` branch.

3. Within the ``liquidity`` directory, the Tezos sources in branch
   ``betanet`` should be in a subdirectory ``tezos``. This can be
   achieved either with a symbolic link, or by checkouting the sources::

     make clone-tezos

4. Install Liquidity dependencies::

     opam install ocp-build
     opam install ocplib-endian zarith calendar digestif hex ocurl lwt \
       lwt_log uri sodium bigstring ezjsonm

5. Build and install::

     make
     make install

  The last command should install the command ``liquidity`` in the
  OPAM switch ``liquidity``.

6. Do a simple test::

     (cd tests && liquidity test0.liq)

7. Optionnally, you can build some local documentation with sphynx
   and the Read-The-Docs theme (``pip3 install sphinx-rtd-theme``)::

     cd docs/sphynx
     make pdf
     make epub
     make html

   The documentation should then be available in ``Liquidity.pdf``,
   ``Liquidity.epub`` and in the ``_site/`` sub-directory for HTML.
