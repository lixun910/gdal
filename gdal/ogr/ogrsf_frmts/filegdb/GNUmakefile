

include ../../../GDALmake.opt
LNK_FLAGS += -arch x86_64
FGDB_INC = -I$(FGDB_HOME)/include
EXTRA_LIBS += -L$(FGDB_HOME)/lib -lfgdbunixrtl -lFileGDBAPI

OBJ	=	FGdbDatasource.o FGdbDriver.o FGdbLayer.o FGdbUtils.o FGdbResultLayer.o 

PLUGIN_SO	= ogr_FileGDB.$(SO_EXT)

CPPFLAGS	:=	-I../generic  $(GDAL_INCLUDE) $(FGDB_INC) $(CPPFLAGS)

default:	$(O_OBJ:.o=.$(OBJ_EXT))

plugin:		$(PLUGIN_SO)

clean:
	rm -f *.o $(O_OBJ)

$(O_OBJ):	ogr_fgdb.h

$(PLUGIN_SO):	$(OBJ)
		$(LD_SHARED) $(LNK_FLAGS) $(OBJ) $(CONFIG_LIBS_INS) $(EXTRA_LIBS) $(LIBS) \
		-o $(PLUGIN_SO)
