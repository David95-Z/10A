#include <stdio.h>
#include <stdlib.h>

// Function to calculate (a^b) % mod using efficient exponentiation
long long int power(int a, int b, int mod) {
    long long int result = 1;
    while (b > 0) {
        if (b % 2 == 1) {
            result = (result * a) % mod;
        }
        a = (a * a) % mod;
        b = b / 2;
    }
    return result;
}

int main() {


    int n, g, x, a, y, b;

    // Input values for n and g (modulus and base)
    printf("Enter the value of n and g: ");
    scanf("%d %d", &n, &g);

    // Input private key for the first person (x)
    printf("Enter the value of x for the first person: ");
    scanf("%d", &x);

    // Calculate public key for the first person (a = g^x mod n)
    a = power(g, x, n);

    // Input private key for the second person (y)
    printf("Enter the value of y for the second person: ");
    scanf("%d", &y);

    // Calculate public key for the second person (b = g^y mod n)
    b = power(g, y, n);

    // Calculate shared secret key for the first person (b^x mod n)
    printf("Key for the first person is: %lld\n", power(b, x, n));

    // Calculate shared secret key for the second person (a^y mod n)
    printf("Key for the second person is: %lld\n", power(a, y, n));

    return 0;
}
