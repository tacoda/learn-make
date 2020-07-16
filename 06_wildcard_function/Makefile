wrong = *.o # Wrong
objects := $(wildcard *.c) # Right
some_binary: 
	touch f1.c
	touch f2.c
	echo $(wrong)
	echo $(objects)

clean:
	rm -f *.c