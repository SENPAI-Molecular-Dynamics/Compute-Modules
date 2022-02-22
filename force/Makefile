##
## Makefile
##
## Licensed under MIT license
##


CC ?= gcc

NAME := compute-force.so

WARNINGS := -Wall -Wextra -Wshadow -Wpointer-arith -Wcast-align -Wwrite-strings -Wmissing-prototypes -Wmissing-declarations -Wredundant-decls -Wnested-externs -Winline -Wno-long-long -Wuninitialized -Wstrict-prototypes
CFLAGS ?= -O2 -s -fpic -std=c99 -U__STRICT_ANSI__
CFLAGS := $(CFLAGS) -I./headers $(WARNINGS)
LDLIBS := -lm

DEPFILES := $(wildcard sources/*.d)
SRCS := $(wildcard sources/*.c)
OBJS := $(SRCS:.c=.o)

$(NAME): $(OBJS)
	$(CC) $(LDFLAGS) $^ $(LDLIBS) -shared -o $@

%.o: %.c
	$(CC) -MMD -MP -MF $*.d $(CFLAGS) $(CPPFLAGS) -c -o $@ $<

clean:
	$(RM) -rf $(DEPFILES) $(OBJS) $(NAME)

-include $(DEPFILES)

.PHONY: clean install
