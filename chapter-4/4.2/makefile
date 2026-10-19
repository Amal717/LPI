# -------------- PROJECT_NAME ---------------------
PROJECT_NAME = open_example

# -------------- Build variables ------------------
BUILD_DIR = build

# -------------- Toolchain ------------------------
CC = gcc

# -------------- CFLAGS ---------------------------
CFLAGS = -Wall

# -------------- Targets --------------------------
TARGET := $(BUILD_DIR)/$(PROJECT_NAME)

all: $(TARGET)

# -------------- sub makefiles --------------------
include ./Core/makefile
include ../lib/makefile

# -------------- Build the target ----------------
$(TARGET): $(OBJS) $(LIB)	| $(BUILD_DIR)
	$(CC) $^ -o $@

# -------------- Build object files ---------------
$(BUILD_DIR)/%.o: %.c | $(BUILD_DIR)
	$(CC) $(CFLAGS) $(INC) -c $< -o $@

$(BUILD_DIR):
	mkdir $@

clean:
	rm -rf $(TARGET)
	rm -rf $(OBJS)

.phony: clean libclean
