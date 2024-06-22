#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_SYMBOLS 100

typedef struct {
    char name[20];
    int value;
} Symbol;

Symbol symbolTable[MAX_SYMBOLS];
int symbolCount = 0;

void insertSymbol(char *name, int value) {
    if (symbolCount < MAX_SYMBOLS) {
        strcpy(symbolTable[symbolCount].name, name);
        symbolTable[symbolCount].value = value;
        symbolCount++;
        printf("Inserted symbol: %s\n", name);
    } else {
        printf("Symbol table full\n");
    }
}

int findSymbol(char *name) {
    for (int i = 0; i < symbolCount; i++) {
        if (strcmp(symbolTable[i].name, name) == 0) {
            return symbolTable[i].value;
        }
    }
    return -1; // Symbol not found
}

int main() {
    insertSymbol("x", 10);
    insertSymbol("y", 20);

    printf("Value of x: %d\n", findSymbol("x"));
    printf("Value of y: %d\n", findSymbol("y"));
    printf("Value of z: %d\n", findSymbol("z")); // Not found

    return 0;
}
