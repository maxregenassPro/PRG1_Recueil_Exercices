# Permutation circulaire droite de 3 valeurs

Reprendre l'exercice [02b-02 - permutation](../04%20-%20Fonctions/02b-02%20-%20permutation.md) en rendant tout le code complètement générique.

<details>
<summary>Solution</summary>

~~~cpp
#include <cstdlib>
#include <iostream>

using namespace std;

template<typename T>
void permutationCirculaireDroite(T& x,
                                 T& y,
                                 T& z);

// note : const T& car on ne sait pas à l'avance le type à traiter
template<typename T>
void afficher(const T& x,
              const T& y,
              const T& z);

//------------------------------------------------------------
// rien ne change ici
int main() {
   double x = 1, y = 2, z = 3;
   for (int i = 1; i <= 3; ++i) {
      permutationCirculaireDroite(x, y, z);
      afficher(x, y, z);
   }
   return EXIT_SUCCESS;
}

//------------------------------------------------------------
template<typename T>
void permutationCirculaireDroite(T& x,
                                 T& y,
                                 T& z) {
   double tmp = z;
   z = y;
   y = x;
   x = tmp;
}

//------------------------------------------------------------
template<typename T>
void afficher(const T& x,
              const T& y,
              const T& z) {
   cout << "x = " << x << ", "
        << "y = " << y << ", "
        << "z = " << z << endl;
}
~~~

</details>