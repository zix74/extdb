COMPILER := g++
CFLAGS := -march=i686 -msse2 -msse3 -fPIC -m32 -O2 -pipe -std=c++0x
STATIC_LIBRARYS := -lPocoCrypto -lPocoUtil -lPocoDataMySQL -lPocoDataSQLite -lPocoData -lPocoNet -lPocoFoundation -lmysqlclient -lboost_filesystem -lboost_random -lboost_regex -lboost_system -lboost_thread -lz
DYNAMIC_LIBRARYS := -ldl -pthread -ltbbmalloc
FILES := src/memory_allocator.cpp src/uniqueid.cpp src/rcon.cpp src/sanitize.cpp src/ext.cpp src/protocols/*.cpp 

extdb-static:
	$(COMPILER) $(CFLAGS) -shared -static-libstdc++ -static-libgcc -o extDB2.so $(FILES) src/main.cpp -Wl,-Bstatic $(STATIC_LIBRARYS) -Wl,-Bdynamic $(DYNAMIC_LIBRARYS)

extdb-static-debug-logging:
	$(COMPILER) $(CFLAGS) -shared -static-libstdc++ -static-libgcc -o extDB2.so $(FILES) src/main.cpp -DDEBUG_LOGGING -Wl,-Bstatic $(STATIC_LIBRARYS) -Wl,-Bdynamic $(DYNAMIC_LIBRARYS)

test:
	$(COMPILER) $(CFLAGS) -g -static-libstdc++ -static-libgcc -o extDB2-test $(FILES) -DTEST_APP -DTESTING -DDEBUG_LOGGING -Wl,-Bstatic $(STATIC_LIBRARYS) -Wl,-Bdynamic $(DYNAMIC_LIBRARYS)
