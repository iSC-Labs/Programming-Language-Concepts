CABAL ?= cabal
GHC ?= ghc

.PHONY : all
all : cabal.sandbox.config
	$(CABAL) install --disable-documentation
	cp .cabal-sandbox/bin/while* .
	cp .cabal-sandbox/bin/test* .

~/.cabal/config :
	$(CABAL) update

cabal.sandbox.config : ~/.cabal/config
	$(CABAL) update
	$(CABAL) sandbox init
	$(CABAL) install --dependencies-only

.PHONY : clean
clean :
	$(CABAL) clean
	rm -f while test

.PHONY : distclean
distclean : clean
	rm -rf cabal.sandbox.config .cabal-sandbox

.PHONY : run-tests
run-tests : all
	./test
