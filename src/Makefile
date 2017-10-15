INCLUDES := 
LIBRARIES := 
LIBS := 
CXXFLAGS := -O3 -fPIC -g -Wall -Werror $(INCLUDES) $(LIBRARIES) $(LIBS)
CXX := g++
#CXX := arm-unknown-linux-gnueabi-g++
MAJOR := 0
MINOR := 1
NAME := DS18B20
VERSION := $(MAJOR).$(MINOR)
RM := rm -rf

LDLIBS = -L./ -lDS18B20

SOURCE = DS18B20Test.cpp DS18B20.h
MYPROGRAM = dstest
MYINCLUDES = ./

MYLIBRARIES = DS18B20

LD_LIBRARY_PATH=./:$LD_LIBRARY_PATH

all: lib copy
lib: lib$(NAME).so.$(VERSION) lib$(NAME).so

lib$(NAME).so: lib$(NAME).so.$(VERSION)
	ldconfig -v -n .
	ln -s lib$(NAME).so.$(MAJOR) lib$(NAME).so

lib$(NAME).so.$(VERSION): $(NAME).o
	$(CXX) -pg -shared -Wl,-soname,lib$(NAME).so.$(MAJOR) $^ -o $@
test:
#	g++ $(LDFLAGS) -o tool tool.o support.o $(LDLIBS)
	@echo test
	@echo $(LD_LIBRARY_PATH)
	$(CXX) -I$(MYINCLUDES) $(SOURCE) -o$(MYPROGRAM) $(LDLIBS) -Wl,-rpath=/home/erick/temperature_sensor_ds18b20/cplusplus_lib/DS18B20/src
clean:
	$(RM) *.o *.so* 

copy:
ifdef DISTPATH
	cp lib$(NAME)* $(DISTPATH)
endif
