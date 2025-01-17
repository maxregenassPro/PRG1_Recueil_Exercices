# Point avec opérateurs
Reprenez la classe Point de l'exercice 01-01 et faites les modifications / ajouts nécessaires afin que le code ci-dessous s'exécute correctement et affiche le résultat ci-après.

~~~cpp
#include <iostream>
#include <cstdlib>
#include <utility>
#include <iomanip>

using namespace std;

int main() {

    Point p1(1.2, 2.4);
    Point p2(3., 4.2);

    cout << "p1" << p1 << ", p2" << p2 << endl;
    
    cout << "p1 + p2 = " << p1 + p2 << endl;
    cout << "p2 + p1 = " << p2 + p1 << endl;

    cout << "p1 + 2. = " << p1 + 2. << endl;
    cout << "2. + p1 = " << 2. + p1 << endl;

    
    cout << (p1 == p2 ? "p1 == p2" : "p1 != p2") << endl;
    Point p3(p1);
    cout << (p1 == p3 ? "p1 == p3" : "p1 != p3") << endl;

    return EXIT_SUCCESS;
}
~~~

~~~text
p1(1.2,2.4), p2(3.0,4.2)
p1 + p2 = (4.2,6.6)
p2 + p1 = (4.2,6.6)
p1 + 2. = (3.2,4.4)
2. + p1 = (3.2,4.4)
p1 != p2
p1 == p3
~~~


<details>
<summary>Solution</summary>

~~~cpp
#include <iostream>
#include <cstdlib>
#include <utility>
#include <iomanip>

using namespace std;

class Point {
public:
    Point();
    Point(double x, double y);
    Point(const Point& p);
    void setX(double x);
    void setY(double y);
    double getX() const;
    double getY() const;
    void deplacer(double dx, double dy);
    void afficher() const;
    Point operator+(const Point& rhs) const;
    Point operator+(double rhs) const;
    bool operator== (const Point & rhs) const;
private:
    double x, y;
};

// -----------------------------------------------------------------
pair<double, double> analyserPoint(const Point& p);
ostream& operator<<(ostream& cout, const Point& p);
Point operator+(double rhs, const Point& lhs);

// -----------------------------------------------------------------


int main() {

    Point p1(1.2, 2.4);
    Point p2(3., 4.2);

    cout << "p1" << p1 << ", p2" << p2 << endl;
    
    cout << "p1 + p2 = " << p1 + p2 << endl;
    cout << "p2 + p1 = " << p2 + p1 << endl;

    cout << "p1 + 2. = " << p1 + 2. << endl;
    cout << "2. + p1 = " << 2. + p1 << endl;

    
    cout << (p1 == p2 ? "p1 == p2" : "p1 != p2") << endl;
    Point p3(p1);
    cout << (p1 == p3 ? "p1 == p3" : "p1 != p3") << endl;

    return EXIT_SUCCESS;
}

// -----------------------------------------------------------------
Point::Point() : Point(0., 0.) {}

Point::Point(double x, double y) : x(x), y(y) {}

Point::Point(const Point& p) : Point(p.x, p.y) {}

void Point::setX(double x){
    this->x = x;
}

void Point::setY(double y){
    this->y = y;
}

double Point::getX() const {
    return this->x;
}

double Point::getY() const {
    return this->y;
}

void Point::deplacer(double dx, double dy) {
    x += dx;
    y += dy;
}

void Point::afficher() const {
    cout << "(" << x << "," << y << ")" << endl;
}

Point Point::operator+(const Point& rhs) const {
    return Point(this->x + rhs.x, this->y + rhs.y);
}

Point Point::operator+(double rhs) const {
    return Point(this->x + rhs, this->y + rhs);
}

bool Point::operator== (const Point & rhs) const {
    return this->x == rhs.x && this->y == rhs.y;
}

// -----------------------------------------------------------------
pair<double, double> analyserPoint(const Point& p){
    return {p.getX(), p.getY()};
}

ostream& operator<<(ostream& cout, const Point& p){
    return cout << fixed << setprecision(1) 
            << "(" << p.getX() << "," 
            << p.getY() << ")"; 
}

Point operator+(double rhs, const Point& lhs){
    return lhs + rhs;
}


// -----------------------------------------------------------------
~~~



</details>