CC = gcc
CFLAGS = -Wall -g -Iinclude

SRC = $(wildcard src/*/*.c src/*/*/*.c)

TARGET = build/mini-x86-sim

all:
	mkdir -p build
	$(CC) $(CFLAGS) $(SRC) -o $(TARGET)

run: all
	./$(TARGET)

clean:
	rm -rf build