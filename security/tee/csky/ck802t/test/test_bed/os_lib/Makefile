#
# Copyright (C) 2015 The YunOS Project. All rights reserved.
#
TOP  := ../../../src/tw/
CURRENT_BUILD := NTW
include $(TOP)/tee.cfg
include $(TOP)/Make.rules
DIRS := $(ARCH)

CFLAGS  += -I../inc
ASFLAGS += -I../inc

SRCS := $(wildcard $(addsuffix /*.c, $(DIRS)))
OBJS := $(addsuffix /built-in.o, $(DIRS))
LIBS := os_lib.o

all: $(OBJS) $(LIBS)

$(LIBS): $(OBJS)
	$(LD) -r -o $(LIBS) $(OBJS)
	@echo "Finish building $@..."

$(OBJS): $(SRCS)
	@for dir in $(DIRS); do $(MAKE) -C $$dir; done

clean:
	@ echo "Cleaning $(LIBS)..."
	@ for dir in $(DIRS); do $(MAKE) -C $$dir clean; done
	@-rm -f $(LIBS)

