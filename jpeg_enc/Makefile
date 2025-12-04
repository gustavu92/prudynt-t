CC = $(CROSS_COMPILE)gcc
AR = $(CROSS_COMPILE)ar

CFLAGS = -std=c99 -fPIC -O2
LDFLAGS_SO = -shared -lm
CFILES = $(wildcard *.c)
OFILES = $(CFILES:.c=.o)

PREFIX ?= ./

all: libjpeg_enc.so libjpeg_enc.a

.c.o:
	$(CC) $(CFLAGS) -c $< -o $@

libjpeg_enc.so: $(OFILES)
	$(CC) $(LDFLAGS_SO) -o $@ $(OFILES)

libjpeg_enc.a: $(OFILES)
	$(AR) rcs $@ $(OFILES)

install:
	mkdir -p $(PREFIX)/lib
	mkdir -p $(PREFIX)/include
	cp libjpeg_enc.so $(PREFIX)/lib/
	cp libjpeg_enc.a $(PREFIX)/lib/
	cp *.h $(PREFIX)/include/

clean:
	rm -f $(OFILES) libjpeg_enc.so libjpeg_enc.a jpegEnc
