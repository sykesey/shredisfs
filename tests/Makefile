
#
#  Flags and stuffs.
#
CFLAGS=-ggdb -Wall -Werror  -I.
LDFLAGS=


#
#  By default make our filesystem.
#
all: link tests


#
#  Clean.
#
clean:
	rm tests *.o || true
	rm -f pathutil.h || true
	rm -f pathutil.c || true

#
#  Symlink
#
link: 
	ln -sf ../src/pathutil.c .
	ln -sf ../src/pathutil.h .

#
#  Test code
#
tests: pathutil.o AllTests.o CuTest.o pathutil_test.o
	gcc -o tests pathutil.o AllTests.o CuTest.o  pathutil_test.o
