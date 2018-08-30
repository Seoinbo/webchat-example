# Version informations
VERSION := 0.1.0-devel
BUILD = `date +"%Y%m%d.%H%M%S"`
CXX := c++
CXXFLAGS := -std=c++1y -pedantic-errors -Wall -Wextra -Werror -lboost_system -pthread
LDFLAGS := -L/usr/lib
BUILD_DIR := ./build
OBJ_DIR := $(BUILD_DIR)/objects
BIN_DIR := $(BUILD_DIR)/bin
TARGET := chatserver
INCLUDE := -Iinclude/
SRC := \
	$(wildcard *.cpp) \

OBJECTS := $(SRC:%.cpp=$(OBJ_DIR)/%.o)

all: build $(BIN_DIR)/$(TARGET)

$(OBJ_DIR)/%.o: %.cpp
	@mkdir -p $(@D)
	$(CXX) $(CXXFLAGS) $(INCLUDE) -o $@ -c $<

$(BIN_DIR)/$(TARGET): $(OBJECTS)
	@mkdir -p $(@D)
	$(CXX) $(CXXFLAGS) $(INCLUDE) $(LDFLAGS) -o $(BIN_DIR)/$(TARGET) $(OBJECTS)

.PHONY: all build clean debug release

build:
	@mkdir -p $(BIN_DIR)
	@mkdir -p $(OBJ_DIR)

debug: CXXFLAGS += -DDEBUG -g
debug: all

release: CXXFLAGS += -O2
release: all

clean:
	-@rm -rvf $(OBJ_DIR)/*
	-@rm -rvf $(BIN_DIR)/*