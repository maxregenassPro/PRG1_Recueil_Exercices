# Surcharge des opérateurs
Soit MonEntier une classe encapsulant un entier (de type int).
Compléter la partie notée < à compléter > dans le code ci-après de telle sorte que, à l'exécution, celui-ci produise le résultat suivant :


~~~text
n = 0
n = 1
false
true
n = 1
n = 2
n = 3
n = 8
n = 8
n = 12
~~~

~~~cpp
< à compléter >

int main() {
   MonEntier m0, m1(1), m2 = 5;
   const MonEntier m3{7};

   cout << m0 << endl
        << m1 << endl;
   
   cout << boolalpha;
   cout << (m0 == m1) << endl;
   cout << (m0 != m1) << endl;   
   cout << noboolalpha;
   
   cout << m1++ << endl;
   cout << m1 << endl;
   cout << ++m1 << endl;
   
   cout << m1 + m2 << endl;
   m1 += m2;
   cout << m1 << endl;
   cout << m3 + m2 << endl;
   
   return EXIT_SUCCESS;
}
~~~



<details>
<summary>Solution</summary>

~~~cpp
#include <iostream>
#include <cstdlib>
using namespace std;

class MonEntier {
   int x;
public:
    MonEntier(int x = 0) : x(x) {}
    MonEntier& operator+=(const MonEntier& rhs) {
        x += rhs.x;
        return *this;
    }
    MonEntier operator+(const MonEntier& rhs) const {
        MonEntier temp(*this);
        temp += rhs;
        return temp;
    }
    MonEntier& operator++() {
        ++x;
        return *this;
    }
    MonEntier operator++(int) {
        MonEntier temp(*this);
        ++x;
        return temp;
    }
    bool operator==(const MonEntier& rhs) const {
        return x == rhs.x;
    }
    bool operator!=(const MonEntier& rhs) const {
        return !(*this == rhs);
    }
    friend ostream& operator<<(ostream& os, const MonEntier& rhs) {
        return os << "n = " << rhs.x;
    }
};



int main() {
   MonEntier m0, m1(1), m2 = 5;
   const MonEntier m3{7};

   cout << m0 << endl
        << m1 << endl;
   
   cout << boolalpha;
   cout << (m0 == m1) << endl;
   cout << (m0 != m1) << endl;   
   cout << noboolalpha;
   
   cout << m1++ << endl;
   cout << m1 << endl;
   cout << ++m1 << endl;
   
   cout << m1 + m2 << endl;
   m1 += m2;
   cout << m1 << endl;
   cout << m3 + m2 << endl;
   
   return EXIT_SUCCESS;
}
~~~

</details>