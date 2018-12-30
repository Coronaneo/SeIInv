include ../Makefile.in

SUPLDLT = ../LIB/libsupldlt.a 

LIBS = $(METIS) $(SUPLDLT) $(LAPACK) $(BLAS) -lm 

OBJS = C2Finterface.o 

all: lap2d5pt.x selinv.x

.c.o:
	$(CC) $(CFLAGS)  -c $<

.f.o:
	${FC} ${FFLAGS} -c $<

lap2d5pt.x: lap2d5pt.o $(OBJS) $(SUPLDLT) $(METIS)
	$(LD) $(LDFLAGS) lap2d5pt.o $(OBJS) $(LIBS) -o $@

selinv.x: selinv.o $(OBJS) $(SUPLDLT) $(METIS) 
	$(LD) $(LDFLAGS) selinv.o $(OBJS) $(LIBS) -o $@


$(SUPLDLT):
	(cd ../LIB; make lib)

clean:
	rm -f *.o selinv.x lap2d5pt.x
