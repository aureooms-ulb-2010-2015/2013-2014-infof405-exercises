
FLAGS = -Wall -W

ifeq ($(O),1)
	FLAGS += -O1
endif
ifeq ($(O),2)
	FLAGS += -O2
endif
ifeq ($(O),3)
	FLAGS += -O3
endif


CXX = g++ -std=c++11 $(FLAGS)
LINK = $(CXX) -o

OUTPUT_NAMES = $(patsubst $(SRC)/%.cpp,run/%,$(shell find $(SRC) | grep \\.cpp$$))
SRC = src
OUTPUTDIR = o
OBJFILES = $(patsubst $(SRC)/%,$(OUTPUTDIR)/%,$(patsubst %.cpp,%.o,$(shell find $(SRC) | grep \\.cpp$$)))

REQUIRED_DIRS = $(OUTPUTDIR) run
_MKDIRS := $(shell for d in $(REQUIRED_DIRS); \
             do                               \
               [ -d $$d ] || mkdir -p $$d;  \
             done)

default: all

all: $(OUTPUT_NAMES)

run/%: $(OUTPUTDIR)/%.o
	$(LINK) $@ $^

$(OUTPUTDIR)/%.o: $(SRC)/%.cpp
	$(CXX) -c $^ -o $@

clean:
	$(RM) -r $(REQUIRED_DIRS)
