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

lib:	kvstore_client.cpp KVStoreImplLevelDB.cpp KVStoreNonTemplateImplLevelDB.cpp KVStoreHeader.h KVStore.h TestKVStore.cpp
	$(GCC) $(SHOWWARN) $(OPL) -c KVStoreNonTemplateImplLevelDB.cpp -o KVStoreNonTemplateImplLevelDB.o $(LIBS)

install:	KVStoreNonTemplateImplLevelDB.o
	ar -cq libkvstore.a KVStoreNonTemplateImplLevelDB.o
	cp -p libkvstore.a /usr/lib


test:	TestKVStore.o TestKVStorePerformance.o TestKVStoreNoReqPerSec.o


TestKVStore.o: kvstore_client.cpp KVStoreImplLevelDB.cpp KVStoreHeader.h KVStore.h TestKVStore.cpp
	$(GCC) $(SHOWWARN) $(OPL) TestKVStore.cpp  -o TestKVStore.o $(LIBS)


TestKVStorePerformance.o: kvstore_client.cpp KVStoreImplLevelDB.cpp KVStoreHeader.h KVStore.h TestKVStorePerformance.cpp
	$(GCC) $(SHOWWARN) $(OPL) TestKVStorePerformance.cpp  -o TestKVStorePerformance.o $(LIBS) -Dthread_count=$(TC)


TestKVStoreNoReqPerSec.o: kvstore_client.cpp KVStoreImplLevelDB.cpp KVStoreHeader.h KVStore.h TestKVStoreNoReqPerSec.cpp
	$(GCC) $(SHOWWARN) $(OPL) TestKVStoreNoReqPerSec.cpp  -o TestKVStoreNoReqPerSec.o $(LIBS) -Dthread_count=$(TC)

clean:
	rm -f *.o *~
