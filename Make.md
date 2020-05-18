# =============  Makefile   =============  
Detail:  
https://makefiletutorial.com/

- Print in makefile
```make
TEST = test
target:
    echo "This line will always print"
    echo Print out test: $(TEST)
```

- Run makefile in silence mode that **@** before each line ```make -s```
```make
all:
    @echo "This make line will not be printed"
```

- Run **shell** command
```make
all:
    cd ..
    # The cd above does not affect this line, because each command is effectively run in a new shell
    echo `pwd`

    # This cd command affects the next because they are on the same line
    cd ..;echo `pwd`

    # Same as above
    cd ..; \
    echo `pwd`
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
