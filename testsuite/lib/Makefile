#**************************************************************************
#*                                                                        *
#*                                 OCaml                                  *
#*                                                                        *
#*                 Xavier Clerc, SED, INRIA Rocquencourt                  *
#*                                                                        *
#*   Copyright 2010 Institut National de Recherche en Informatique et     *
#*     en Automatique.                                                    *
#*                                                                        *
#*   All rights reserved.  This file is distributed under the terms of    *
#*   the GNU Lesser General Public License version 2.1, with the          *
#*   special exception on linking described in the file LICENSE.          *
#*                                                                        *
#**************************************************************************

TOPDIR = ../..
COMPFLAGS ?=
RUNTIME_VARIANT ?=

include $(TOPDIR)/Makefile.tools

libraries := testing.cmi testing.cma lib.cmo

# If the native compiler is enabled, then also compile testing.cmxa
ifeq "$(NATIVE_COMPILER)" "true"
libraries += testing.cmxa
endif

all: $(libraries)

testing.cma: testing.cmo
	$(OCAMLC) -a -linkall -o $@ $<

testing.cmxa: testing.cmx
	$(OCAMLOPT) -a -linkall -o $@ $<

testing.cmo : testing.cmi

%.cmi: %.mli
	$(OCAMLC) -c $<

%.cmo: %.ml
	$(OCAMLC) -c $<

%.cmx: %.ml
	$(OCAMLOPT) -c $<

.PHONY: clean
clean:
	rm -f *.cm* *.$(O) *.$(A)
