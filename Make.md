# =============  Makefile   =============  
Detail:  
https://makefiletutorial.com/

- Run the makefile.  
A simple ```make``` will build the **first target** in the list.  
```make all``` will build the target **all**. If you want **all** to be the default, then move it to the **top of the list**.  

- Reset the file and cache.
```make
make clean
```

- Print the variable in makefile
```make
TEST = test_123
target:
    echo Print out test: $(TEST)
```

- Run makefile in silence mode that **@** before each line. Use ```make -s``` to disable showing all the commands. 
```make
all:
    @echo "Disable showing the command"
    # "Disable showing the command"

    echo "The Command will printed"
    # echo "The Command will printed"
    # "The Command will printed"
```

- Run **shell** command special rule.
```make
all:
    # No Work! The cd above does not affect this line, because each command is effectively run in a new shell
    cd ..
    pwd

    # This cd command affects the next because they are on the same line
    cd ..; pwd

    # Same as above
    cd ..; \
    pwd
```

- Regular expressions syntax.
```make
# Get all files in current path and test/ path.
src = $(wildcard *.c) $(wildcard test/*.c)
```

- Modify the file attribute.
```make
# Change *.c to *.o in this path.
$(patsubst %.c, %.o, $(dir) )
```

- Declare variable
```make
# Normal declaring
V = $(VERSION)

# "Override Directive" to append more text
variable := value

# No input will "Empty" default
Name ?= %{nil}

# "pattern-specific" will assign `CFLAGS` the value of `-O' for all targets matching the pattern `%.o`.
%.o : CFLAGS = -O
```

- Passing variable from shell command **make foo=test all**
```make
# make foo=test all
foo ?= TEST

all:
    echo 'BUILD_NUMBER= $(foo)'
```

- Passing user defined parameters in rpmbuild to fill variables
```make
# And refer it within the spec as %{_foobar} , the _ is a convention, not a must
rpmbuild -bb --define '_foobar Foo' somespecfile.spec
```

- Conditional if/else
```make
foo = KO
ifeq ($(foo), KO)
    echo "foo equals KO"
else
    echo "NO"
endif
```

- Conditional ifdef/else (ifdef negative ifndef)
```make
ifdef foo
    frobozz = yes
else
    frobozz = no
endif
```
