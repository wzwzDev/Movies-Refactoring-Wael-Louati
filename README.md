# Movies

## Refactoring: Movies

## <em>**Version 1.**</em> "Customer" Class - "statement()" Method

### <em>**Smell code**</em>:
####  Long Method => more than 15 lines
- Poor distribution of responsibilities => Lack of Cohesion
- Impossible to reuse for another format (HTML) => Immobile
  * copy+paste => DRY
- Change in cost and points policy => 
  * Viscous
- copy+paste => multiplies and complicates maintenance

### <em>**Refactoring**</em>: 

Extract Method => switch and dependent code in "amountFor" method of Customer class

![claseCustomer](/out/docs/diagrams/src/movies/movies.svg) 

## <em>**Version 2.**</em> "Customer" Class - "amountFor()" Method

### <em>**Smell code:**</em>

- Bad names => "each" and "thisAmount"

### <em>**Refactoring:**</em>

- Rename variable => "rental" and "result"

![claseCustomer](/out/docs/diagrams/src/movies2/movies.svg)

## <em>**Version 3.**</em> "Customer" Class - "amountFor()" Method

### <em>**Smell Code:**</em>

- Feature Envy => get(), get(), … from the server

- Data Class => get(), get(), … in the client
Information Expert => the responsible class is the one that has the information

### <em>**Refactoring**</em>

- Move method => "getCharge" method to "Rental" class

## <em>**Version 4.**</em> "Customer" Class – "amountFor()" Method

### <em>**Smell Code:**</em>

- "Unnecessary decomposition": private method without justification

### <em>**Refactoring**</em>

- Inline Method => remove "amountFor"

![claseCustomer](/out/docs/diagrams/src/movies4/movies.svg)


## <em>**Version 5.**</em> "Customer" Class – "statement()" Method

### <em>**Smell Code:**</em>

- Unnecessary temporary variable => "thisAmount"

### <em>**Refactoring**</em>

- Replace Temp with Query => "each.getCharge()"

![claseCustomer](/out/docs/diagrams/src/movies5/movies.svg)

## <em>**Version 6.**</em> "Customer" Class – "statement()" Method

### <em>**Smell Code:**</em>

- Long Method => more than 15 lines

### <em>**Refactoring**</em>

- Extract method => "getFrequentRenterPoints()" method to "Rental" class

## <em>**Version 7.**</em> "Customer" Class – "statement()" Method

### <em>**Smell Code:**</em>

- Unnecessary temporary variable => "totalAmount"

### <em>**Refactoring**</em>

- Replace Temp with Query => "this.getTotalCharge()"

![claseCustomer](/out/docs/diagrams/src/movies7/movies.svg)


## <em>**Version 8.**</em> "Customer" Class – "statement()" Method

### <em>**Smell Code:**</em>

- Unnecessary temporary variable => "frequentRenterPoints"

### <em>**Refactoring**</em>

- Replace Temp with Query =>  "this.getTotalFrequentRenterPoints()"

![claseCustomer](/out/docs/diagrams/src/movies8/movies.svg)


## <em>**Version 9.**</em> "Rental" Class – "getCharge()" Method

### <em>**Smell Code:**</em>

- Information Expert => most of the information is from Movie

### <em>**Refactoring**</em>

- Move Method => "getCharge()" method to "Movie" class

![claseCustomer](/out/docs/diagrams/src/movies9/movies.svg)

## <em>**Version 10.**</em> "Rental" Class – "getFrequentRenterPoints()" Method

### <em>**Smell Code:*</em>

- Information Expert => most of the information is from Movie

### <em>**Refactoring**</em>

- Move Method => "getFrequentRenterPoints()" method to "Movie" class

![claseCustomer](/out/docs/diagrams/src/movies10/movies.svg)


## <em>**Version 11.**</em> "Movie" Class – "getCharge()" Method

### <em>**Smell Code:**</em>

- Multiple Alternative Statement => behavior depends on a type/code/...

### <em>**Refactoring**</em>

- Replace Type Code with Strategy/State (dependency injection) => Self Encapsulate Field => "priceCode"

![claseCustomer](/out/docs/diagrams/src/movies11/movies.svg)


## <em>**Version 12.**</em> "Movie" Class – "getCharge()" Method

### <em>**Smell Code:**</em>

- Multiple Alternative Statement => behavior depends on a type/code/...

### <em>**Refactoring**</em>

- Replace Type Code with Strategy/State (dependency injection) => Add new classes => "Price", "ChildrenPrice", ...

## <em>**Version 13.**</em> "Movie" Class - "priceCode" Attribute

### <em>**Smell Code:**</em>

- Multiple Alternative Statement => behavior depends on a type/code/...

### <em>**Refactoring**</em>

- Replace Type Code with Strategy/State (dependency injection) => Replace attribute: "int priceCode" with "Price price"


![claseCustomer](/out/docs/diagrams/src/movies13/movies.svg)

## <em>**Version 14.**</em> "Movie" Class - "getCharge()" method

### <em>**Smell Code:**</em>

- Multiple Alternative Statement => behavior depends on a type/code/...

### <em>**Refactoring**</em>

- Replace Type Code with Strategy/State (dependency injection) => Move method: "getCharge()" method to "Price" class

![claseCustomer](/out/docs/diagrams/src/movies14/movies.svg)


## <em>**Version 15.**</em> "Price" Class - "getCharge()" method

### <em>**Smell Code:**</em>

- Multiple Alternative Statement => behavior depends on a type/code/...

### <em>**Refactoring**</em>

- Replace Conditional with Polymorphism => Override "getCharge()" method in derived classes

![claseCustomer](/out/docs/diagrams/src/movies15/movies.svg)


## <em>**Version 16.**</em> "Price" Class - "getFrequentRenterPoints()" method

### <em>**Smell Code:**</em>

- Multiple Alternative Statement => behavior depends on a type/code/...

### <em>**Refactoring**</em>

- Replace Conditional with Polymorphism => Override "getFrequentRenterPoints()" method in derived classes

![claseCustomer](/out/docs/diagrams/src/movies16/movies.svg)

## <em>**Version 17.**</em> "CustomerTest" Class - test methods with Type/Code

### <em>**Smell Code:**</em>

- Multiple Alternative Statement => behavior depends on a type/code/...

### <em>**Refactoring**</em>

- Hide field: add "childrens()", "regular()" and "newRelease()" methods in "MovieBuilder" class

![claseCustomer](/out/docs/diagrams/src/movies17/movies.svg)

## <em>**Version 18.**</em> "CustomerTest" Class - test methods with Type/Code

### <em>**Smell Code:**</em>

- Multiple Alternative Statement => behavior depends on a type/code/...

### <em>**Refactoring**</em>

-Hide field: from "CustomerTest" call "childrens()", "regular()" and "newRelease()" methods of "MovieBuilder" class
-Replace field: "priceCode" attribute with "Price" in "MovieBuilder" class
-Replace field: "priceCode" attribute with "Price" in "Movie" class

## <em>**Version 19.**</em> "Price" Class - "getPriceCode()" method

### <em>**Smell Code:**</em>

- Multiple Alternative Statement => behavior depends on a type/code/...

### <em>**Refactoring**</em>

- Remove method: "getPriceCode()" from "Price" and "Movie" classes

## <em>**Version 20.**</em> "Price" Hierarchy

### <em>**Smell Code:**</em>

- Magic numbers => 2, 1.5, ...

### <em>**Refactoring**</em>

- Add attribute: "CHARGE", "DAYS_RENTER_THRESHOLD", ... in "Price" hierarchy

![claseCustomer](/out/docs/diagrams/src/movies20/movies.svg)

## <em>**Version 21**</em>


![claseCustomer](/out/docs/diagrams/src/movies21/movies.svg)

