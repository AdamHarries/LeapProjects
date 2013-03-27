OS := $(shell uname)
ARCH := $(shell uname -m)

ifeq ($(OS), Linux)
  ifeq ($(ARCH), x86_64)
    LEAP_LIBRARY := ../../LeapSDK/lib/x64/libLeap.so
  else
    LEAP_LIBRARY := ../../LeapSDK/lib/x86/libLeap.so
  endif
else
  # OS X
  LEAP_LIBRARY := ../lib/libLeap.dylib
endif

GesturePrinter: GesturePrinter.cpp
	$(CXX) -Wall -g -I../../LeapSDK/include GesturePrinter.cpp -o GesturePrinter $(LEAP_LIBRARY)
ifeq ($(OS), Darwin)
	install_name_tool -change @loader_path/libLeap.dylib ../lib/libLeap.dylib GesturePrinter
endif

clean:
	rm -rf GesturePrinter GesturePrinter.dSYM
