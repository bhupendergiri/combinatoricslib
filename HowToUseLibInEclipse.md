# How to use combinatoricslib in Eclipse Projects #

  * Create a new java project called “MyExample” via the menu **File->New->Java Project**
> ![http://combinatoricslib.googlecode.com/svn/trunk/img/eclipse1.png](http://combinatoricslib.googlecode.com/svn/trunk/img/eclipse1.png)

  * Press the button "Finish"
  * Create a new folder “lib” in the project root folder
> ![http://combinatoricslib.googlecode.com/svn/trunk/img/eclipse2.png](http://combinatoricslib.googlecode.com/svn/trunk/img/eclipse2.png)

  * Download the latest version of the combinatoricslib [here](https://googledrive.com/host/0BxImlmdcF-rYYkZjY1hMTWR0Ujg). Put the downloaded jar-file into the created folder "lib" and refresh the project by pressing the key **F5**
> ![http://combinatoricslib.googlecode.com/svn/trunk/img/eclipse3.png](http://combinatoricslib.googlecode.com/svn/trunk/img/eclipse3.png)

  * Open the properties of the project and select the tab “Libraries”. Click the button “Add JARs…” and select the file **combinatoricslib-2.1.jar** to be added to the build path.
> ![http://combinatoricslib.googlecode.com/svn/trunk/img/eclipse4.png](http://combinatoricslib.googlecode.com/svn/trunk/img/eclipse4.png)

  * Press the button **OK** and refresh the project
> ![http://combinatoricslib.googlecode.com/svn/trunk/img/eclipse5.png](http://combinatoricslib.googlecode.com/svn/trunk/img/eclipse5.png)

  * Create a new java class called “MyExample”
> ![http://combinatoricslib.googlecode.com/svn/trunk/img/eclipse6.png](http://combinatoricslib.googlecode.com/svn/trunk/img/eclipse6.png)

  * Insert the following code into the class
```
import org.paukov.combinatorics.Factory;
import org.paukov.combinatorics.Generator;
import org.paukov.combinatorics.ICombinatoricsVector;

public class MyExample {

   public static void main(String[] args) {

      // create combinatorics vector
      ICombinatoricsVector<String> initialVector = Factory.createVector(new String[] { "apple", "orange " });
   
      // create multi-combination generator to generate 3-combination
      Generator<String> gen = Factory.createMultiCombinationGenerator(initialVector, 3);

      // print the number of combinations
      System.out.println("Number of combinations is: " + gen.getNumberOfGeneratedObjects());

      // go through the iterator
      for (ICombinatoricsVector<String> combination : gen) {
         System.out.println(combination);
      }
   }
}
```

  * Save the class and run the code. You will see the next result

```
Number of combinations is: 4
CombinatoricsVector=([apple, apple, apple], size=3)
CombinatoricsVector=([apple, apple, orange ], size=3)
CombinatoricsVector=([apple, orange , orange ], size=3)
CombinatoricsVector=([orange , orange , orange ], size=3)
```