LIBS=-lpcap 
ifacelookup: ifacelookup.o
    $(CC) opensniff.o -o ifacelookup $(LDFLAGS) $(LIBS)
ifacelookupf.o: ifacelookup.c
    $(CC) $(CFLAGS) -c ifacelookup.c
clean:
    rm *.o ifacelookup