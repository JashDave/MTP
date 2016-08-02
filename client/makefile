GCC = g++ -std=c++11
LIBS = -lboost_serialization
WARN = 0
SHOWWARN = -Wno-deprecated
OPLEVEL = 0
OPL =
TC = 50

ifeq ($(WARN),1)
SHOWWARN =
endif

ifneq ($(OPLEVEL),0)
OPL = -O$(OPLEVEL)
endif

all:	TestKVStore.o TestKVStorePerformance.o


TestKVStore.o: kvstore_client.cpp KVStoreImplLevelDB.cpp KVStoreHeader.h KVStore.h TestKVStore.cpp
	$(GCC) $(SHOWWARN) $(OPL) TestKVStore.cpp  -o TestKVStore.o $(LIBS)


TestKVStorePerformance.o: kvstore_client.cpp KVStoreImplLevelDB.cpp KVStoreHeader.h KVStore.h TestKVStorePerformance.cpp
	$(GCC) $(SHOWWARN) $(OPL) TestKVStorePerformance.cpp  -o TestKVStorePerformance.o $(LIBS) -Dthread_count=$(TC)

clean:
	rm -f *.o *~
