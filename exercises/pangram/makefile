### If you wish to use extra libraries,
### add their flags in the "LIBS" variable (like we do with "CFLAGS").

###
CFLAGS  = -std=c99
CFLAGS += -g
CFLAGS += -Wall
CFLAGS += -Wextra
CFLAGS += -pedantic
CFLAGS += -Werror

VFLAGS  = --quiet
VFLAGS += --tool=memcheck
VFLAGS += --leak-check=full
VFLAGS += --error-exitcode=1

test: tests.out
	@./tests.out

memcheck: tests.out
	@valgrind $(VFLAGS) ./tests.out
	@echo "Memory check passed"

clean:
	rm -rf *.o *.out *.out.dSYM

tests.out: test/test_pangram.c src/pangram.c src/pangram.h
	@echo Compiling $@
	@$(CC) $(CFLAGS) src/pangram.c test/vendor/unity.c test/test_pangram.c -o tests.out $(LIBS)
