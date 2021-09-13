CC := g++
SOURCE_FILES := $(wildcard *.cpp)
OBJ_FILES := $(patsubst %.cpp, %.o, $(SOURCE_FILES))
DEPENDENCIES := $(patsubst %.cpp, %.dep, $(SOURCE_FILES))
EXE := main

all: $(EXE)

.PHONY: debug
debug: OPTIONS := -g
#debug: OBJ_FILES := $(patsubst %.cpp, %.o.d, $(SOURCE_FILES))
debug: clean $(EXE)

$(EXE): $(OBJ_FILES)
	$(CC) $^ -o $@

%.dep: %.cpp
	$(CC) -M $^ -o $@
	
%.o: %.cpp
	$(CC) $(OPTIONS) -c $< -o $@

-include $(DEPENDENCIES)

.PHONY: remake
remake: clean all

.PHONY: clean
clean:
	@rm -f $(OBJ_FILES) $(DEPENDENCIES) $(EXE) 

