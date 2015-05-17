# Introduction #

This library simplifies the process of generation of different combinatorial objects such as:
  1. **Permutations without repetitions**
  1. **Permutations with repetitions**
  1. **Partitions**
  1. **Subsets**
  1. **Simple combinations**
  1. **Compositions**

CombinatoricsLib 0.2 allows generating vectors of any items. Type of the items should be specified as type parameter of generator and vector. There is a general pattern using the generator below
```
    // create combinatorics vector
    CombinatoricsVector<T> vector = new CombinatoricsVector<T>(array);

    // create a concrete generator
    Generator<T> generator = new <Concrete>Generator<T>(vector);
    
    // create iterator
    Iterator<CombinatoricsVector<T>> iterator = generator.createIterator();


    // go through the iterator
    while (iterator.hasNext()) {
      CombinatoricsVector<T> item = iterator.next();
      System.out.println(item);
    }
```


# 1. Permutations without repetitions #

A permutation is an ordering of a set in the context of all possible orderings. For example, the set containing the first three digits, 123, has six permutations: 123, 132, 213, 231, 312, and 321.

This is a example of permutation of 3 string items:
```
    // create array of initial items
    ArrayList<String> array = new ArrayList<String>();
    array.add("one");
    array.add("two");
    array.add("three");

    // create combinatorics vector
    CombinatoricsVector<String> corePermutation = new CombinatoricsVector<String>(array);
    
    // create permutation generator
    Generator<String> generator = new PermutationGenerator<String>(corePermutation);

    // print the number of generated permutations
    System.out.println("Number of permutations is: " + gnerator.getNumberOfGeneratedObjects());

    // create iterator
    Iterator<CombinatoricsVector<String>> iterator = generator.createIterator();

    // go through the iterator
    while (iterator.hasNext()) {
      CombinatoricsVector<String> permutation = iterator.next();
      System.out.println(permutation);
    }
```

Output result is
```
   Number of permutations is: 6
   CombinatoricsVector=[[one, two, three]], size=3]
   CombinatoricsVector=[[one, three, two]], size=3]
   CombinatoricsVector=[[three, one, two]], size=3]
   CombinatoricsVector=[[three, two, one]], size=3]
   CombinatoricsVector=[[two, three, one]], size=3]
   CombinatoricsVector=[[two, one, three]], size=3]
```


# 2. Permutations with repetitions #

The permutation may have more elements than slots.  For example, the three possible permutation of 12 in three slots are: 111, 211, 121, 221, 112, 212, 122, and 222.

This is a code:
```

    // create array of initial items
    ArrayList<String> array = new ArrayList<String>();
    array.add("one");
    array.add("two");

    // create combinatorics vector
    CombinatoricsVector<String> corePermutation = new CombinatoricsVector<String>(array);
    
    // create permutation with repetition generator, second parameter is a number of slots
    Generator<String> permutationWithRepetitionGenerator = new PermutationWithRepetitionGenerator<String>(corePermutation, 3);

    // create iterator
    Iterator<CombinatoricsVector<String>> permutationWithRepetitionIterator = permutationWithRepetitionGenerator.createIterator();

    // print the number of generated permutations
    System.out.println("Number of permutationWithRepetition is: " + permutationWithRepetitionGenerator.getNumberOfGeneratedObjects());

    // go through the iterator
    while (permutationWithRepetitionIterator.hasNext()) {
      CombinatoricsVector<String> permutationWithRepetition = permutationWithRepetitionIterator.next();
      System.out.println(permutationWithRepetitionIterator);
    }
```

And the result
```
   Number of permutationWithRepetition is: 8
   PermutationWithRepetitionIterator=[#1, CombinatoricsVector=[[one, one, one]], size=3]]
   PermutationWithRepetitionIterator=[#2, CombinatoricsVector=[[two, one, one]], size=3]]
   PermutationWithRepetitionIterator=[#3, CombinatoricsVector=[[one, two, one]], size=3]]
   PermutationWithRepetitionIterator=[#4, CombinatoricsVector=[[two, two, one]], size=3]]
   PermutationWithRepetitionIterator=[#5, CombinatoricsVector=[[one, one, two]], size=3]]
   PermutationWithRepetitionIterator=[#6, CombinatoricsVector=[[two, one, two]], size=3]]
   PermutationWithRepetitionIterator=[#7, CombinatoricsVector=[[one, two, two]], size=3]]
   PermutationWithRepetitionIterator=[#8, CombinatoricsVector=[[two, two, two]], size=3]]
```

# 3. Partitions #

In number theory, a partition of a positive integer n is a way of writing n as a sum of positive integers. Two sums that differ only in the order of their summands are considered to be the same partition; if order matters then the sum becomes a composition. A summand in a partition is also called a part.

The partitions of 5 are listed below:
  1. 1 + 1 + 1 + 1 + 1
  1. 2 + 1 + 1 + 1
  1. 2 + 2 + 1
  1. 3 + 1 + 1
  1. 3 + 2
  1. 4 + 1
  1. 5

The number of partitions of n is given by the partition function p(n). In number theory, the partition function p(n) represents the number of possible partitions of a natural number n, which is to say the number of distinct (and order independent) ways of representing n as a sum of natural numbers.

This is a code:
```
    // create partition generator of 5
    Generator<Integer> partitionGenerator = new PartitionGenerator(5);

    // create iterator
    Iterator<CombinatoricsVector<Integer>> partitionIterator = partitionGenerator.createIterator();
    
    // go through the iterator 
    while (partitionIterator.hasNext()) {
      CombinatoricsVector<Integer> partition = partitionIterator.next();
      System.out.println(partitionIterator);
    }
```

And the result
```
   PartitionIterator=[#1, CombinatoricsVector=[[1, 1, 1, 1, 1]], size=5]]
   PartitionIterator=[#2, CombinatoricsVector=[[2, 1, 1, 1]], size=4]]
   PartitionIterator=[#3, CombinatoricsVector=[[2, 2, 1]], size=3]]
   PartitionIterator=[#4, CombinatoricsVector=[[3, 1, 1]], size=3]]
   PartitionIterator=[#5, CombinatoricsVector=[[3, 2]], size=2]]
   PartitionIterator=[#6, CombinatoricsVector=[[4, 1]], size=2]]
   PartitionIterator=[#7, CombinatoricsVector=[[5]], size=1]]
```

# 4. Subsets #

A set A is a subset of a set B if A is "contained" inside B. A and B may coincide. The relationship of one set being a subset of another is called inclusion or sometimes containment.

Examples:
  * The set {1, 2} is a proper subset of {1, 2, 3}.
  * Any set is a subset of itself, but not a proper subset.
  * The empty set, denoted by ∅, is also a subset of any given set X.

All subsets of {1, 2, 3} are:
  1. {}
  1. {1}
  1. {2}
  1. {1, 2}
  1. {3}
  1. {1, 3}
  1. {2, 3}
  1. {1, 2, 3}

And code which generates all subsets of {one, two, three}
```
    // create array of initial items
    ArrayList<String> array = new ArrayList<String>();
    array.add("one");
    array.add("two");
    array.add("three");

    // create combinatorics vector
    CombinatoricsVector<String> corePermutation = new CombinatoricsVector<String>(array);
    
    // create subset generator
    Generator<String> subSetGenerator = new SubSetGenerator<String>(corePermutation);

    // create iterator
    Iterator<CombinatoricsVector<String>> subSetIterator = subSetGenerator.createIterator();
    // print the number of subsets
    System.out.println("Number of subsets is: " + subSetGenerator.getNumberOfGeneratedObjects());

    // go through the iterator 
    while (subSetIterator.hasNext()) {
      CombinatoricsVector<String> subSet = subSetIterator.next();
      System.out.println(subSetIterator);
    }    
```

And the result
```
   Number of subsets is: 8
   SubSetIterator=[#1, CombinatoricsVector=[[]], size=0]]
   SubSetIterator=[#2, CombinatoricsVector=[[one]], size=1]]
   SubSetIterator=[#3, CombinatoricsVector=[[two]], size=1]]
   SubSetIterator=[#4, CombinatoricsVector=[[one, two]], size=2]]
   SubSetIterator=[#5, CombinatoricsVector=[[three]], size=1]]
   SubSetIterator=[#6, CombinatoricsVector=[[one, three]], size=2]]
   SubSetIterator=[#7, CombinatoricsVector=[[two, three]], size=2]]
   SubSetIterator=[#8, CombinatoricsVector=[[one, two, three]], size=3]]
```

# 5. Simple combinations #

A simple k-combination of a finite set S is a subset of k distinct elements of S. Specifying a subset does not arrange them in a particular order. As an example, a poker hand can be described as a 5-combination of cards from a 52-card deck: the 5 cards of the hand are all distinct, and the order of the cards in the hand does not matter.

Example. Generate 3-combination of the set {red, black, white, green, blue}.
```
    // create array of initial items
    ArrayList<String> array = new ArrayList<String>();
    array.add("red");
    array.add("black");
    array.add("white");
    array.add("green");
    array.add("blue");

    // create combinatorics vector
    CombinatoricsVector<String> corePermutation = new CombinatoricsVector<String>(array);

    // create simple combination generator to generate 3-combination
    Generator<String> combinationGenerator = new SimpleCombinationGenerator<String>(corePermutation, 3);
    
    // create iterator
    Iterator<CombinatoricsVector<String>> combinationIterator = combinationGenerator.createIterator();
    
    // print the number of combinations
    System.out.println("Number of combinations is: " + combinationGenerator.getNumberOfGeneratedObjects());
    
    // go through the iterator
    while (!combinationIterator.isDone()) {
      CombinatoricsVector<String> combination = combinationIterator.next();
      System.out.println(combinationIterator);
    }
```

And the result
```
   Number of combinations is: 10
   SimpleCombinationIterator=[#1, CombinatoricsVector=[[red, black, white]], size=3]]
   SimpleCombinationIterator=[#2, CombinatoricsVector=[[red, black, green]], size=3]]
   SimpleCombinationIterator=[#3, CombinatoricsVector=[[red, black, blue]], size=3]]
   SimpleCombinationIterator=[#4, CombinatoricsVector=[[red, white, green]], size=3]]
   SimpleCombinationIterator=[#5, CombinatoricsVector=[[red, white, blue]], size=3]]
   SimpleCombinationIterator=[#6, CombinatoricsVector=[[red, green, blue]], size=3]]
   SimpleCombinationIterator=[#7, CombinatoricsVector=[[black, white, green]], size=3]]
   SimpleCombinationIterator=[#8, CombinatoricsVector=[[black, white, blue]], size=3]]
   SimpleCombinationIterator=[#9, CombinatoricsVector=[[black, green, blue]], size=3]]
   SimpleCombinationIterator=[#10, CombinatoricsVector=[[white, green, blue]], size=3]]
```

# 6. Compositions #

A composition of an integer n is a way of writing n as the sum of a sequence of (strictly) positive integers. Two sequences that differ in the order of their terms define different compositions of their sum, while they are considered to define the same partition of that number (see. p. 3 above).

The sixteen compositions of 5 are:
  1. 5
  1. 4+1
  1. 3+2
  1. 3+1+1
  1. 2+3
  1. 2+2+1
  1. 2+1+2
  1. 2+1+1+1
  1. 1+4
  1. 1+3+1
  1. 1+2+2
  1. 1+2+1+1
  1. 1+1+3
  1. 1+1+2+1
  1. 1+1+1+2
  1. 1+1+1+1+1.

Compare this with the seven partitions of 5 (see p. 3 above):
  1. 5
  1. 4+1
  1. 3+2
  1. 3+1+1
  1. 2+2+1
  1. 2+1+1+1
  1. 1+1+1+1+1.

Example. Generate compositions of 5.
```
    // create composition generator of 5
    Generator<Integer> compositionGenerator = new CompositionGenerator(5);

    // create iterator
    Iterator<CombinatoricsVector<Integer>> compositionIterator = compositionGenerator.createIterator();
    
    // go through the iterator 
    while (compositionIterator.hasNext()) {
      CombinatoricsVector<Integer> composition = compositionIterator.next();
      System.out.println(partitionIterator);
    }
```

And the result
```
   CompositionIterator=[#1, CombinatoricsVector=[[5]], size=1]]
   CompositionIterator=[#2, CombinatoricsVector=[[1, 4]], size=2]]
   CompositionIterator=[#3, CombinatoricsVector=[[2, 3]], size=2]]
   CompositionIterator=[#4, CombinatoricsVector=[[1, 1, 3]], size=3]]
   CompositionIterator=[#5, CombinatoricsVector=[[3, 2]], size=2]]
   CompositionIterator=[#6, CombinatoricsVector=[[1, 2, 2]], size=3]]
   CompositionIterator=[#7, CombinatoricsVector=[[2, 1, 2]], size=3]]
   CompositionIterator=[#8, CombinatoricsVector=[[1, 1, 1, 2]], size=4]]
   CompositionIterator=[#9, CombinatoricsVector=[[4, 1]], size=2]]
   CompositionIterator=[#10, CombinatoricsVector=[[1, 3, 1]], size=3]]
   CompositionIterator=[#11, CombinatoricsVector=[[2, 2, 1]], size=3]]
   CompositionIterator=[#12, CombinatoricsVector=[[1, 1, 2, 1]], size=4]]
   CompositionIterator=[#13, CombinatoricsVector=[[3, 1, 1]], size=3]]
   CompositionIterator=[#14, CombinatoricsVector=[[1, 2, 1, 1]], size=4]]
   CompositionIterator=[#15, CombinatoricsVector=[[2, 1, 1, 1]], size=4]]
   CompositionIterator=[#16, CombinatoricsVector=[[1, 1, 1, 1, 1]], size=5]]
```