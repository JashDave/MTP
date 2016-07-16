GCC = g++ -std=c++11
LIBS = -lboost_serialization
WARN = 0
SHOWWARN = -Wno-deprecated
OPLEVEL = 0
OPL =

ifeq ($(WARN),1)
SHOWWARN =
endif

ifneq ($(OPLEVEL),0)
OPL = -O$(OPLEVEL)
endif

TestKVStore.o: kvstore_client.cpp KVStoreImplLevelDB.cpp KVStoreHeader.h KVStore.h TestKVStore.cpp
	$(GCC) $(SHOWWARN) $(OPL) TestKVStore.cpp  -o TestKVStore.o $(LIBS)

clean:
	rm -f *.o *~
