LIBNAME=lfs
OUTDIR=target

#############################################################

CC= gcc

INCS = -I/usr/local/openresty/luajit/include/luajit-2.1

# Compilation directives
CFLAGS= -c -O2 -Wall -fPIC -W -Waggregate-return -Wcast-align -Wmissing-prototypes -Wnested-externs -Wshadow -Wwrite-strings -pedantic

LFLAGS=-L/usr/local/openresty/luajit/lib -lluajit-5.1

SOURCES = lfs.c
OBJS=$(SOURCES:%.c=${OUTDIR}/%.o)

all: ${LIBNAME}


${LIBNAME}: ${OBJS}
	@ echo "[AR] $@"
	@ ar crs ${OUTDIR}/lib${LIBNAME}.a $^
	@ ls -lh ${OUTDIR}/${LIBNAME}.a
	@ echo "[SO] $@"
	@ ${CC} -shared -o ${OUTDIR}/${LIBNAME}.so $^
	@ ls -lh ${OUTDIR}/${LIBNAME}.so

install:
	cp ${OUTDIR}/${LIBNAME}.so ../../

clean:
	rm -rf ${OUTDIR}

#############################################################
${OUTDIR}/%.o:%.c
	@ mkdir -p $(@D)
	@ echo "[CC] $^"
	@ ${CC} ${CFLAGS} ${INCS} $< -o $@ ${LFLAGS}