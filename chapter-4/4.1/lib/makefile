C_DIR = $(dir $(lastword $(MAKEFILE_LIST)))
LIB_NAME = HELPER

BUILD_DIR ?= $(C_DIR)/build
LIB_DIR = $(BUILD_DIR)/$(LIB_NAME)
LIB = $(LIB_DIR)/lib$(LIB_NAME).a

# source files for the library
LIB_SRC = $(notdir $(wildcard $(C_DIR)/src/*.c))

# source files location
VPATH += $(C_DIR)/src

# add library include files
LIB_INC += $(C_DIR)/inc

# add library include dir to compiler flags
CFLAGS += $(addprefix -I,$(LIB_INC))

LIB_OBJS = $(patsubst %.c,$(LIB_DIR)/%.o,$(LIB_SRC))

$(LIB): $(LIB_OBJS)
	mkdir -p $(LIB_DIR)
	ar -r $@ $^

$(LIB_DIR)/%.o:%.c 		| $(LIB_DIR)
	$(CC) $(CFLAGS) -c $< -o $@

$(LIB_DIR):
	mkdir -p $(LIB_DIR)

libclean:
	rm -rf $(LIB_DIR)

.phony: libclean
