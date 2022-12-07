# Helpdesk

Compiling the project on Apple M1 MacBook is giving me trouble.

## Clone from Github


    1003> git clone ssh://git@github.com:443/phm-esl/Ash-Framework-Demo.git from-github
    Cloning into 'from-github'...
    remote: Enumerating objects: 25, done.
    remote: Counting objects: 100% (25/25), done.
    remote: Compressing objects: 100% (19/19), done.
    remote: Total 25 (delta 3), reused 25 (delta 3), pack-reused 0
    Receiving objects: 100% (25/25), 5.42 KiB | 5.42 MiB/s, done.
    Resolving deltas: 100% (3/3), done.

    1004> cd from-github/

    1005> ls
    README.md  lib  mix.exs  mix.lock  test

## Resolve dependencies

    1006> mix deps.get
    * Getting elixir_sense (https://github.com/elixir-lsp/elixir_sense.git)
    remote: Enumerating objects: 8938, done.        
    remote: Counting objects: 100% (2034/2034), done.        
    remote: Compressing objects: 100% (853/853), done.        
    remote: Total 8938 (delta 1210), reused 1809 (delta 1105), pack-reused 6904        
    Resolving Hex dependencies...
    Resolution completed in 0.064s
    Unchanged:
      ash 2.4.12
      comparable 1.0.0
      decimal 2.0.0
      docsh 0.7.2
      ecto 3.9.2
      elixir_make 0.6.3
      ets 0.8.1
      getopt 1.0.1
      jason 1.4.0
      nimble_options 0.4.0
      picosat_elixir 0.2.2
      providers 1.8.1
      sourceror 0.11.2
      spark 0.2.12
      stream_data 0.5.0
      telemetry 1.1.0
      typable 0.3.0
    * Getting ash (Hex package)
    * Getting docsh (Hex package)
    * Getting providers (Hex package)
    * Getting getopt (Hex package)
    * Getting comparable (Hex package)
    * Getting decimal (Hex package)
    * Getting ecto (Hex package)
    * Getting ets (Hex package)
    * Getting jason (Hex package)
    * Getting nimble_options (Hex package)
    * Getting picosat_elixir (Hex package)
    * Getting spark (Hex package)
    * Getting stream_data (Hex package)
    * Getting telemetry (Hex package)
    * Getting sourceror (Hex package)
    * Getting elixir_make (Hex package)
    * Getting typable (Hex package)

## Compile the source

Note that there is an error in `./deps/picosat_elixir/Makefile` that will
require `unset CFLAGS LDFLAGS` in order to work-around.

The reason is that the Makefile will set appropriate linker options *only* if
these variables **do not have existing values**.

The result if `$LDFLAGS` has an assigned value:

    cc -L/some/library/paths/in/$LDFLAGS \
    -shared \
    $PWD/deps/picosat_elixir/priv/picosat_nif.o \
    $PWD/deps/picosat_elixir/priv/picosat.o \
    -o $PWD/_build/dev/lib/picosat_elixir/priv/picosat_nif.so
    Undefined symbols for architecture arm64:
      "_enif_get_int", referenced from:
          _solve_nif in picosat_nif.o
      "_enif_get_list_cell", referenced from:
          _solve_nif in picosat_nif.o
      "_enif_get_list_length", referenced from:
          _solve_nif in picosat_nif.o
      "_enif_make_atom", referenced from:
          _solve_nif in picosat_nif.o
      "_enif_make_badarg", referenced from:
          _solve_nif in picosat_nif.o
      "_enif_make_int", referenced from:
          _solve_nif in picosat_nif.o
      "_enif_make_list_from_array", referenced from:
          _solve_nif in picosat_nif.o
    ld: symbol(s) not found for architecture arm64
    clang: error: linker command failed with exit code 1 (use -v to see invocation)
    make: *** [Makefile:46: $PWD/_build/dev/lib/picosat_elixir/priv/picosat_nif.so] Error 1
    could not compile dependency :picosat_elixir, "mix compile" failed. 
    Errors may have been logged above.  You can recompile this dependency
    with "mix deps.compile picosat_elixir", update it with "mix deps.update
    picosat_elixir" or clean it with "mix deps.clean picosat_elixir"
    ==> helpdesk
    ** (Mix) Could not compile with "make" (exit status: 2).
    You need to have gcc and make installed. Try running the
    commands "gcc --version" and / or "make --version". If these programs
    are not installed, you will be prompted to install them.

Apply the work-around, and try again:

    $> unset LDFLAGS CFLAGS
    $> mix compile
    ==> picosat_elixir
    cc -flat_namespace \
       -undefined suppress \
       -shared \
       $PWD/deps/picosat_elixir/priv/picosat_nif.o \
       $PWD/deps/picosat_elixir/priv/picosat.o \
       -o $PWD/_build/dev/lib/picosat_elixir/priv/picosat_nif.so
