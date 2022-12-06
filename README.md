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

    1007> mix compile
    ==> sourceror
    Compiling 1 file (.yrl)
    Compiling 5 files (.erl)
    Compiling 12 files (.ex)
    Generated sourceror app
    ==> stream_data
    Compiling 3 files (.ex)
    Generated stream_data app
    ==> decimal
    Compiling 4 files (.ex)
    Generated decimal app
    ==> nimble_options
    Compiling 3 files (.ex)
    Generated nimble_options app
    ==> typable
    Compiling 1 file (.ex)
    Generated typable app
    ===> Analyzing applications...
    ===> Compiling telemetry
    ==> jason
    Compiling 10 files (.ex)
    Generated jason app
    ==> comparable
    Compiling 10 files (.ex)
    warning: atom ::: must be written between quotes, as in :"::", to avoid ambiguity
      lib/comp.ex:90:15

    warning: atom ::: must be written between quotes, as in :"::", to avoid ambiguity
      lib/comp.ex:91:15

    warning: <|> is deprecated. Use another pipe-like operator
      lib/comp.ex:149:18

    warning: <|> is deprecated. Use another pipe-like operator
      lib/comp.ex:158:18

    warning: <|> is deprecated. Use another pipe-like operator
      lib/comp.ex:176:18

    warning: <|> is deprecated. Use another pipe-like operator
      lib/comp.ex:185:18

    warning: <|> is deprecated. Use another pipe-like operator
      lib/comp.ex:231:17

    Generated comparable app
    ===> Analyzing applications...
    ===> Compiling getopt
    ===> Analyzing applications...
    ===> Compiling providers
    ==> spark
    Compiling 16 files (.ex)
    Generated spark app
    ===> Analyzing applications...
    ===> Compiling docsh
    src/docsh_tracer.erl:37:1: Warning: missing specification for function tracer_monitor/1
    src/docsh_tracer.erl:45:1: Warning: missing specification for function handler/2
    src/docsh_tracer.erl:63:1: Warning: missing specification for function strip_ts/1
    src/docsh_tracer.erl:66:1: Warning: missing specification for function format_call/1
    src/docsh_tracer.erl:70:1: Warning: missing specification for function format_return_from/1
    src/docsh_tracer.erl:74:1: Warning: missing specification for function translate_args/1
    src/docsh_tracer.erl:78:1: Warning: missing specification for function translate_ret/1
    src/docsh_tracer.erl:81:1: Warning: missing specification for function translate_one/1
    src/docsh_tracer.erl:84:1: Warning: missing specification for function translations/0
    src/docsh_tracer.erl:87:1: Warning: missing specification for function flatten_if_state/1
    src/docsh_tracer.erl:90:1: Warning: missing specification for function pass_to_dbg/2
    src/docsh_tracer.erl:97:1: Warning: missing specification for function ffunc/1
    src/docsh_tracer.erl:105:1: Warning: missing specification for function fargs/1
    src/docsh_tracer.erl:111:1: Warning: missing specification for function print/3
    src/docsh_tracer.erl:114:1: Warning: missing specification for function enum/1
    src/docsh_tracer.erl:117:1: Warning: missing specification for function format_timestamp/1
    src/docsh_tracer.erl:119:1: Warning: missing specification for function format_timestamp/2
    src/docsh_tracer.erl:132:1: Warning: missing specification for function format_element/0
    src/docsh_tracer.erl:137:1: Warning: missing specification for function format_content/0
    src/docsh_tracer.erl:153:1: Warning: missing specification for function element/1
    src/docsh_tracer.erl:162:1: Warning: missing specification for function cleanup_text/0

    ==> elixir_sense
    Compiling 55 files (.ex)
    Generated elixir_sense app
    ==> ecto
    Compiling 56 files (.ex)
    Generated ecto app
    ==> ets
    Compiling 7 files (.ex)
    Generated ets app
    ==> elixir_make
    Compiling 1 file (.ex)
    Generated elixir_make app
    ==> picosat_elixir
    cc -std=c99 -finline-functions -Wall -O3 -DNDEBUG -fPIC -I /Users/phm/Software/erlang-25.0.2/lib/erlang/erts-13.0.2/include -o /Users/phm/Repos/Workshop/Ash-Framework-Demo/from-github/deps/picosat_elixir/priv/picosat.o -c /Users/phm/Repos/Workshop/Ash-Framework-Demo/from-github/deps/picosat_elixir/c_src/picosat.c
    cc -std=c99 -finline-functions -Wall -O3 -DNDEBUG -fPIC -I /Users/phm/Software/erlang-25.0.2/lib/erlang/erts-13.0.2/include -o /Users/phm/Repos/Workshop/Ash-Framework-Demo/from-github/deps/picosat_elixir/priv/picosat_nif.o -c /Users/phm/Repos/Workshop/Ash-Framework-Demo/from-github/deps/picosat_elixir/c_src/picosat_nif.c
    cc -L/Users/phm/Software/Python-3.10.5/lib \
       -L/Users/phm/Software/bash-5.1.16/lib \
       -L/Users/phm/Software/erlang-25.0.2/lib \
       -L/Users/phm/Software/gdal-3.4.3/lib \
       -L/Users/phm/Software/geos-3.10.3/lib \
       -L/Users/phm/Software/gettext-0.21/lib \
       -L/Users/phm/Software/jdk-18.0.1.1/lib \
       -L/Users/phm/Software/libtool-2.4.6/lib \
       -L/Users/phm/Software/libxml2-2.9.10/lib \
       -L/Users/phm/Software/ncurses-6.3/lib \
       -L/Users/phm/Software/node-16.15.1/lib \
       -L/Users/phm/Software/openssl-1.1.1o/lib \
       -L/Users/phm/Software/postgresql-14.3/lib \
       -L/Users/phm/Software/proj-8.2.1/lib \
       -L/Users/phm/Software/sqlite-3.39.0/lib \
       -L/Users/phm/Software/tiff-4.4.0/lib \
       -L/Users/phm/Software/wxWidgets-3.1.6/lib \
       -L/Users/phm/Software/xz-5.2.5/lib \
       -shared \
       /Users/phm/Repos/Workshop/Ash-Framework-Demo/from-github/deps/picosat_elixir/priv/picosat_nif.o \
       /Users/phm/Repos/Workshop/Ash-Framework-Demo/from-github/deps/picosat_elixir/priv/picosat.o \
       -o /Users/phm/Repos/Workshop/Ash-Framework-Demo/from-github/_build/dev/lib/picosat_elixir/priv/picosat_nif.so
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
    make: *** [Makefile:46: /Users/phm/Repos/Workshop/Ash-Framework-Demo/from-github/_build/dev/lib/picosat_elixir/priv/picosat_nif.so] Error 1
    could not compile dependency :picosat_elixir, "mix compile" failed. Errors may have been logged above. You can recompile this dependency with "mix deps.compile picosat_elixir", update it with "mix deps.update picosat_elixir" or clean it with "mix deps.clean picosat_elixir"
    ==> helpdesk
    ** (Mix) Could not compile with "make" (exit status: 2).
    You need to have gcc and make installed. Try running the
    commands "gcc --version" and / or "make --version". If these programs
    are not installed, you will be prompted to install them.

    error = 1 

## Example of compilation that succeeds

This example was discovered quite by accident.

    cc -flat_namespace \
       -undefined suppress \
       -shared \
       /Users/phm/Repos/Workshop/Ash-Framework-Demo/helpdesk-again/deps/picosat_elixir/priv/picosat_nif.o \
       /Users/phm/Repos/Workshop/Ash-Framework-Demo/helpdesk-again/deps/picosat_elixir/priv/picosat.o \
       -o /Users/phm/Repos/Workshop/Ash-Framework-Demo/helpdesk-again/_build/dev/lib/picosat_elixir/priv/picosat_nif.so

