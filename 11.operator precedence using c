#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdbool.h>
#include <ctype.h>
bool isOperator(char ch) {
    return (ch == '+' || ch == '-' || ch == '*' || ch == '/');
}
int precedence(char op) {
    if (op == '+' || op == '-')
        return 1;
    if (op == '*' || op == '/')
        return 2;
    return 0;
}
int applyOp(int a, int b, char op) {
    switch (op) {
        case '+': return a + b;
        case '-': return a - b;
        case '*': return a * b;
        case '/': return a / b;
    }
    return 0;
}
int evaluateExpression(char *exp) {
    int i;
    int values[100];
    int topOfValues = -1;
    char operators[100];
    int topOfOperators = -1;

    for (i = 0; i < strlen(exp); i++) {
        if (exp[i] == ' ')
            continue;
        if (exp[i] == '(') {
            operators[++topOfOperators] = exp[i];
        }
        else if (isdigit(exp[i])) {
            int val = 0;
            while (i < strlen(exp) && isdigit(exp[i])) {
                val = (val * 10) + (exp[i] - '0');
                i++;
            }
            i--; 
            values[++topOfValues] = val;
        }
        else if (exp[i] == ')') {
            while (topOfOperators != -1 && operators[topOfOperators] != '(') {
                int b = values[topOfValues--];
                int a = values[topOfValues--];
                char op = operators[topOfOperators--];
                values[++topOfValues] = applyOp(a, b, op);
            }
            topOfOperators--;
        }
        else if (isOperator(exp[i])) {
            while (topOfOperators != -1 && precedence(operators[topOfOperators]) >= precedence(exp[i])) {
                int b = values[topOfValues--];
                int a = values[topOfValues--];
                char op = operators[topOfOperators--];
                values[++topOfValues] = applyOp(a, b, op);
            }
            operators[++topOfOperators] = exp[i];
        }
    }
    while (topOfOperators != -1) {
        int b = values[topOfValues--];
        int a = values[topOfValues--];
        char op = operators[topOfOperators--];
        values[++topOfValues] = applyOp(a, b, op);
    }
    return values[topOfValues];
}
int main() {
    char exp[100];
    printf("Enter expression: ");
    fgets(exp, sizeof(exp), stdin);
    if (exp[strlen(exp) - 1] == '\n')
        exp[strlen(exp) - 1] = '\0';
    int result = evaluateExpression(exp);
    printf("Result: %d\n", result);
    return 0;
}
