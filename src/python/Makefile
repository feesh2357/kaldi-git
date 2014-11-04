
all:
EXTRA_CXXFLAGS = -Wno-sign-compare
include ../kaldi.mk

BINFILES = 


OBJFILES = 


ADDLIBS = ../lm/kaldi-lm.a ../decoder/kaldi-decoder.a ../lat/kaldi-lat.a \
          ../hmm/kaldi-hmm.a ../transform/kaldi-transform.a ../gmm/kaldi-gmm.a \
	      ../tree/kaldi-tree.a ../matrix/kaldi-matrix.a  ../util/kaldi-util.a \
          ../base/kaldi-base.a  ../thread/kaldi-thread.a

TESTFILES =

PYLIB = $(shell python-config --libs)
PYINC = $(shell python-config --includes)
NPINC = -I$(shell python -c 'import numpy; print numpy.get_include()')

PYLIBS = kaldi_io_internal.so

#include ../makefiles/default_rules.mk

%.so: %.cpp
		g++ -shared -o $@ -Wall -fPIC $(PYINC) $(NPINC) $(CXXFLAGS) $< $(ADDLIBS) $(LDFLAGS) -L$(PYLIB) $(LOADLIBES) $(LDLIBS) -lpython2.7 -lboost_python -lboost_system 

clean:
	-rm -f *.o *.a *.so $(TESTFILES) $(BINFILES) $(TESTOUTPUTS) tmp* *.tmp

depend:
	-$(CXX) $(PYINC) $(NPINC) -M $(CXXFLAGS) *.cpp > .depend.mk  

test:

all: $(PYLIBS)
