# Java Code Style

This document lists Java coding recommendations common in the Java development community.

The recommendations are based on established standards collected from a number of sources.

## 1. Naming Conventions

* Names representing packages should be in all lower case, example :

	` com.onebank.orm`
	` com.ovo.orm`

* Names representing types must be nouns and written in mixed case starting with upper case, example :

	`User` `DatabaseConnection`

* Avoid too verbose name or Enterprisify for type name, example :

	`AbstractDataSourceBasedMultiTenantConnectionProviderImpl (Hibernate Framework)`
	`PreAuthenticatedGrantedAuthoritiesWebAuthenticationDetails (Spring Framework)`
`HasThisTypePatternTriedToSneakInSomeGenericOrParameterizedTypePatternMatchingStuffAnywhereVisitor (AspectJ)`

* Names representing methods must be verbs and written in mixed case starting with lower case.

	`compute()` `getTotalWidth()`

* Avoid too verbose method name, example :

	`stalkingToYourExWhileYouAreWorking()`

* Names representing constants (final variables) must be all uppercase using underscore to separate words, example :

	`MAX_ITERATIONS`

* Generic variables should have the same name as their type. example :

	`setTopic(Topic topic) not setTopic(Topic value)`

* The name of the object is implicit, and should be avoided in a method name.

	`line.getLength() NOT line.getLineLength()`

* The term compute can be used in methods where something is computed.

	`computeLength()`
	`computeWidth()`

* The term find can be used in methods where something is looked up.

	`User.findById()`

* The term initialize can be used where an object or a concept is established.

	`printer.initializeFont()`

* Variables should be initialized where they are declared and they should be declared in the smallest scope possible.

	`String name = "foo"`

## 2. Conditionals

Complex conditional expressions must be avoided. Introduce temporary boolean variables instead.


	bool isFinished = (elementNo < 0) || (elementNo > maxElement)
	bool isRepeatedEntry = elementNo == lastElement
	if (isFinished || isRepeatedEntry) {

	}

not

	if ((elementNo < 0) || (elementNo > maxElement)||
		 elementNo == lastElement) {
	}

Avoid nested if, make sure your method only have one if else condition so it can be tested easily.

	public void fight() {
		if(hasEnergy() || hasPower()) {
			shoot();
		}
		else {
			fallback();
		}
	}

not

	public void fight() {
		if(...) {
			if(..) {

			}
			else {

			}
		}
		else {
		}
	}

## 3. Exception Handling
A try-catch statement should have the following form:

	try {
		statements;
	}
	catch(Exception exception) {
		statements;
	}

or

	try {
		statements;
	}
	catch(Exception exception) {
		statements;
	}
	finally {
		statements;
	}
