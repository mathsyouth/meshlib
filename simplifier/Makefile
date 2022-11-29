
#// =============================================================== 
#// Makefile for ASST1 (OpenGL)
#// =============================================================== 

#// ===============================
#// A few generic defines


#// ===============================
#// Compiler to use : if you want to use the DEC native "cc"
#// compiler, some of the flags below may not work

CC        = CC

#// ===============================
#// Compile flags flags : 
#//	-g = include debug info
#//	-pg = include profile info
#//	-Wall = enable all warnings
#//	-O6 = highest optimization

#CFLAGS     = -g -Wall
#CFLAGS     = -g -pg -Wall
CFLAGS     =  -g
#CFLAGS     = -O6

#// ===============================
#// Linking flags :

#OFLAGS    = -pg
OFLAGS    =

#// ===============================
#// Paths :

#INCPATH   = -I/tmp_mnt/home/sjg/include
LIBPATH   =  -L../lib

LIB       = -lglut -lGLU -lGL -lX11 -lXmu -lm -lmesh

#// ===============================
#// Files :

INCLUDES = draw.h inverse.h draw.h coords3.h matrix4.h catmull-rom.h geom.h ../lib/mesh.h ../lib/funcs.h

SOURCES  = viewer.c matrix4.c coords3.c draw.c coords3.c quat.c arcball.c

OBJECTS  = viewer.o matrix4.o coords3.o draw.o quat.o arcball.o

TARGET   = viewer

# Target --------------------------

$(TARGET):	$(OBJECTS)
	$(CC) $(OFLAGS) -o $(TARGET) $(OBJECTS) $(LIBPATH) $(LIB)
	chmod a+rx $(TARGET) *.o

# Utilities ------------------------

# Print up the entire source tree
#
print:
	enscript -2rG -pprint.ps $(SOURCES) $(INCLUDES) Makefile

# Create code dependencies 
#
depend: $(SOURCES) $(INCLUDES)
	$(CC) $(CPPFLAGS) -M $(SOURCES) > makedep
	echo '/^# DO NOT DELETE THIS LINE/+2,$$d' >eddep
	echo '$$r makedep' >>eddep
	echo 'w' >>eddep
	ed - Makefile < eddep
	rm eddep makedep
	echo '# DEPENDENCIES MUST END AT END OF FILE' >> Makefile
	echo '# IF YOU PUT STUFF HERE IT WILL GO AWAY' >> Makefile
	echo '# see make depend above' >> Makefile

# Cleanup
#
clean:
	rm -rf core *~ *.o $(TARGET)

# Code checkin
#
ci:
	ci -l $(SOURCES) $(INCLUDES) Makefile

#-----------------------------------------------------------------
# DO NOT DELETE THIS LINE -- make depend uses it
# DEPENDENCIES MUST END AT END OF FILE

