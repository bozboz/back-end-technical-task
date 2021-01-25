<p align="center">
  <img src="https://avatars.githubusercontent.com/u/1674051?s=400&u=abac644db14427c9edf1f067c1ac2217bb60ddcb&v=4" alt="Logo" width="150" height="150" />
</p>
<h1 align="center">Backend Technical Task</h1>

1. What is the output of the following psudo code?

```
a = 0 
b = 1 
print a 
for n in range(1..10): 
  print b 
  c = a+b 
  a = b 
  b = c 
```

2. The following PHP functions are riddled with error, please fix them:

```
    /**
     * Add two numbers together and return the result
     * 
     * @param mixed $a
     - @param mixed $b
     * @return mixed
     */
    function sum(a, b)
    {
        return $a + $b;
    }
```

```
    /**
     * Subtract $b from $a and return the result
     * 
     * @praam mixed $a
     * @param mixed $b
     * @return mixed
     */
    fuuction subtract($a, &b)
    {
        return $b -- $a;
    }
```

```
    /**
     * Divide $a by $b and return the result
     *
     * @param mixed $a
     * @param mixed $b
     * @return mixed
     */
    public function divide($a, $b)
    (
        return $a % $d;
    }
```

```
    /**
     * Return $int cubed
     *
     * @param int $int
     * @return int
     */
    function cube(int $int) : int
    {
        retunr $a * 3
    }
```

4. Write a function that searches an array for the string 'Bozboz' and returns its location in the array. There can only be one 'Bozboz' so it should throw and exception if there is more than one. If 'Bozboz' is not found in the array it should return `-1`.

```
findBozboz(['Bozboz', 'Foo', 'Bar']);
// should return 0

findBozboz(['Foo', 'Bar', 'Baz']);
// Should return -1
```

5. Demonstrate how you would refactor* the following code. Include a brief list of the changes you made along with the improved code.

    _*Code refactoring is the process of restructuring existing computer code—changing the factoring—without changing its external behavior. Refactoring improves nonfunctional attributes of the software._

```php
<?php
class Film
{
    public function __construct($title, $priceCode)
    {
        $this->_title = $title;
        $this->_priceCode = $priceCode;
    }
    public function getPriceCode()
    {
        return $this->_priceCode;
    }
    public function setPriceCode($value)
    {
        $this->_priceCode = $value;
    }
    public function getTitle()
    {
        return $this->_title;
    }
    private $_title;
    private $_priceCode;
    const CHILDRENS = 2;
    const REGULAR = 0;
    const NEW_RELEASE = 1;
}
class Rental
{
    public function __construct($film, $daysRented)
    {
        $this->_film = $film;
        $this->_daysRented = $daysRented;
    }
    public function getDaysRented()
    {
        return $this->_daysRented;
    }
    /**
     * @return Film
     */
    public function getFilm()
    {
        return $this->_film;
    }
    private $_film;
    private $_daysRented;
}
class Customer
{
    public function __construct($name)
    {
        $this->_name = $name;
        $this->_rentals = array();
    }
    public function addRental($rental)
    {
        array_push($this->_rentals, $rental);
    }
    public function getName()
    {
        return $this->_name;
    }
    public function getStatement()
    {
        $totalAmount = 0;
        $frequentRenterPoints = 0;
        $result = "Rental Record for " . $this->getName() . "\n";
        foreach ($this->_rentals as $rental)
        {
            /* @var $rental Rental */
            $thisAmount = 0;
            //determine amounts for each line 
            switch ($rental->getFilm()->getPriceCode()) {
                case Film::REGULAR:
                    $thisAmount += 2;
                    if ($rental->getDaysRented() > 2) $thisAmount += ($rental->getDaysRented() - 2) * 1.5;
                    break;
                case Film::NEW_RELEASE:
                    $thisAmount += $rental->getDaysRented() * 3;
                    break;
                case Film::CHILDRENS:
                    $thisAmount += 1.5;
                    if ($rental->getDaysRented() > 3) $thisAmount += ($rental->getDaysRented() - 3) * 1.5;
                    break;
            }
            // add frequent renter points
            $frequentRenterPoints++;
            // add bonus for a two day new release rental 
            if ($rental->getFilm()->getPriceCode() == Film::NEW_RELEASE && $rental->getDaysRented() > 1) $frequentRenterPoints++;
            //show figures for this rental 
            $result .= "\t" . $rental->getFilm()->getTitle() . "\t" . $thisAmount . "\n";
            $totalAmount += $thisAmount;
        }
        return $result;
    }
    private $_name;
    private $_rentals;
}
```
