# =============  Makefile   =============  
Detail:  
https://makefiletutorial.com/

- Print in makefile
```make
TEST = Amtrak
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

- Conditional if/else
```make
foo = KO
ifeq ($(foo), KO)
    echo "foo equals KO"
else
    echo "NO"
endif
```
