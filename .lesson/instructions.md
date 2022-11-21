# Instructions  
### Description:
A Hashset is a commonly used implementation of the Set interface of the Collection API. Sets are data structures which do not contain duplicate values. Additionally, data within a HashSet is not guaranteed to be placed or retrieved in any particular order. Sets are commonly used as part of other systems, or when the idenfication of a unique value is important.

Common HashSet methods:
* **add** : Adds the specified element into the set, if it is not already present. Returns true if the elements is added. Returns false otherwise.
* **remove** : Removes the specified element from the set, if it is preset. Returns true if the element is removed. Returns false otherwise.
* **contains** : Returns true if the specified element exists within the collection.

At this point, you've had plenty of practice looking at basic interactions using different collections, so for this activity, we will provide some additional context for using Collections as part of other applications.
Please follow the steps below:

### Steps:
1. Modify your **Main** class to look like the following:
```Java
import java.util.HashSet;
import java.util.Scanner;

class Main {
  public static void main(String[] args) {
    HashSet<String> states = new HashSet<String>();
    HashSet<String> answers = new HashSet<String>();
    Scanner scan = new Scanner(System.in);
  }
}
```
Here, we are creating a new HashSet object and storing the reference in a variable called 'states'. Notice the import statement above the Main class declaration. Additionally, notice the angle brackets '<>' which contain the word 'String'. These are known as 'Generics'. Different classes, particularly those in the Collection API of Java, use 'Generics' to specify what Datatype can be used with an Object that has been created. In this case, we are specifying that our HashSet 'states' can only contain String objects. If we try to place other Objects within this HashSet, we would be met with a compilation error.

You may be wondering why we've created two HashSets...don't worry, we'll explain that shortly!

Finally, we can also see a return of the Scanner class. As a reminder, the Scanner class is used to take input from a user using the console. By calling various methods on our Scanner Object, we will be able to take input from the console and store those expression into variables.

2. Now add the following code to your `main()` method, underneath the created Scanner object:
```Java
states.add("alabama");
states.add("alaska");
states.add("arizona");
states.add("arkansas");
states.add("california");
states.add("colorado");
states.add("connecticut");
states.add("delaware");
states.add("florida");
states.add("georgia");
states.add("hawaii");
states.add("idaho");
states.add("illinois");
states.add("indiana");
states.add("iowa");
states.add("kansas");
states.add("kentucky");
states.add("louisiana");
states.add("maine");
states.add("maryland");
states.add("massachusetts");
states.add("michigan");
states.add("minnesota");
states.add("mississippi");
states.add("missouri");
states.add("montana");
states.add("nebraska");
states.add("nevada");
states.add("new hampshire");
states.add("new jersey");
states.add("new mexico");
states.add("new york");
states.add("north carolina");
states.add("north dakota");
states.add("ohio");
states.add("oklahoma");
states.add("oregon");
states.add("pennsylvania");
states.add("rhode island");
states.add("south carolina");
states.add("south dakota");
states.add("tennessee");
states.add("texas");
states.add("utah");
states.add("vermont");
states.add("virginia");
states.add("washington");
states.add("west virginia");
states.add("wisconsin");
states.add("wyoming");
```
Here, we are adding all 50 states to the 'states' HashSet. The `add()` method allows us to insert values into the collection. 

3. Now, add the following code to the `main()` method, underneath the previously added code:
```Java
// if 'answers' is smaller than 'states' we haven't guess all 50 states yet
while (answers.size() < states.size()) {
  // Ask the user to enter a state
  System.out.println("Enter a State:");

  // change input to make it case-insensitive
  String input = scan.nextLine().toLowerCase();

  // Check if the user input is an actual state
  if (states.contains(input)) {

    // if the input was correct, lets try to add it to our collection
    if (answers.add(input)) {
      // if the input was added to the collection, print this statement
      System.out.println("You've added: " + input + " to the collection!");  
    } else {
      // if the input was not added, it means they've already guess that state
      System.out.println("Sorry, you've already added: " + input + " previously!");
    }
  } else {
    System.out.println("Sorry: " + input + " is not a State! (double check your spelling)");
  }

  // This message tells the user how many more states to guess.
  System.out.println(states.size() - answers.size() + " more to go!");
}

scan.close();
```
You may already see where we are going with this example; but, we are creating a game in which a user can try to guess all 50 states! The code comments above detail some of the code, but let's walk through some of the lines in more detail:
* `while (answers.size() < states.size()) {` : The condition for our while loop is "as long as the 'answers' HashSet is smaller than the 'states' HashSet, continue to loop". Within the while loop, we check if the user's input matches one of the fifty (50) states in the 'states' HashSet. If the input matches, this means the user entered a valid state. This means the `size()` of 'answers' can only be, at most, the same size of 'states'.
* `String input = scan.nextLine().toLowerCase();` : The `toLowerCase()` method on Strings changes the letter casing to lower case. This makes input case-insensitive. Meaning that "UTAH" or "utah" are the same value. Since the 50 states were added with all lowercase letters, we match that casing when gathering user input.
* `if (states.contains(input)) {` : This if-statement condition checks to make sure the input given exists in the 'states' HashSet. This prevents users from entering random words.
* `if (answers.add(input)) {` : This if-statement checks if the input does not already exist in the collection 'answers'. Remember that the `add()` method will return `true` if data is added, and `false` if it is not. Since Sets do not contain duplicate values, this will return false if we enter the same state twice.

There are many improvements that could be made, and this code can definitely be expended upon, but hopefully this showcases how we can start to apply some of these concepts and combine all of the tools we've been working with in interesting ways!

### Test:
Use the test provided to verify your functionality.