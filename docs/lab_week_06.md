Lab 6: Maps!
===================================

Step 0, the BST
---

If you have not already completed your BST assignment, complete it! You're already late! 

Everything in this lab will be built off of your assignment code, so if you don't feel comfortable with your tree class, feel free to call me over to help you iron out the issues.

Step 1, Templatize!
---
Templatize your BST Assignment code! Feel free to copy the whole assignment to another folder if you wish to preserve the original (just in case something's messed up and Miller needs you to resubmit).

Don't forget to also templatize the `Node` struct/class. Be sure to compile everything and test with your original test harness to make sure things are still working as they should be!

In addition to templatizing your code, you should also adjust your recursive insert helper function and your recursive search/find function to return `Node *` instead of `void` or `bool` respectively. It'll make things easier in a few steps.

Furthermore, it'll make things easier if you change all of your private fields to protected.

Step 2, Map time!
---

No, not Nap Time, ***Map* Time**! It's even better!!

###Quick Map Description

Maps are, in my opinion, the coolest and most fun to use datatypes of everything you'll learn this quarter. And the best part is they're easy to implement!

Of course the STL (Standard Template Library) already has a map, so before we start with ours, comment out everything in your main and mess around with theirs to figure out how yours will be working (docs on STL map can be found [here](http://www.cplusplus.com/reference/map/map/)).

A Map is a datastructure that Maps a key to a value. You can think of a vector of strings as a map that will map an integer key (the index) to a string value. But maps can map any type of value to any other type!

For example, we could go the other way and map strings to integers (using the STL map as an example):

	map<string, int> m;
	m["hey!"] = 69; //Creates a pair {"hey!", 69} since one doesn't exits
	m["Hello?"] = 420;
	m["hey!"] += 2; //Modifies the existing pair
	cout << m["hey!"] << ' ' << m["Hello?"] << endl;
	
See it in action [here](http://ideone.com/5cVgUV)!

Maps are useful everywhere. Remember the stack exercise with all of the different bracket types you had to compare? You probably ended up using a switch-case or a bunch of if's. But what if you had a map? You could have mapped the open bracket type to the close bracket type to check, saving you up to 15 lines of code and simplifying everything!

###How We'll Do It

Each item in a map is actually the conjunction of two items, possibly of different types! You can think of a map item as a Key/Value pair, where we access the value by querying with the key.

I gave you a bit of a kickstart by already giving you a Pair struct. You'll notice that we have **two** template types, that's because, like in the example above, the key and value are allowed to be of different types.

While we could make our map a vector or list of these pairs, the only way to access in a map is by lookups of keys, and who wants to use a datastructure that takes `O(n)` time for it's most common operation? So instead, let's use your BST!

The tree we'll use for our map should be of type `Pair<K, V>`, so the Tree declaration would look like `Tree<Pair<K, V>>`. How ugly is that? Welcome to the real world of template programming.

Since a map here is technically just a tree with some special operations built on top, we can make our map inherit from our tree! I've given you this code too.


##How To Get The Code

[Visit](https://raw.githubusercontent.com/scohe001/Map/master/map.h/) to view the Map.h
    
###Your Job

All that's left for you is 

* [`[]` subscript operator](http://www.cplusplus.com/reference/map/map/operator[]/)
* [erase](http://www.cplusplus.com/reference/map/map/erase/)
* [size](http://www.cplusplus.com/reference/map/map/size/) (you may want to add a member variable for this one)
* [empty](http://www.cplusplus.com/reference/map/map/empty/)
* [count](http://www.cplusplus.com/reference/map/map/count/) (your count should either return 1 or 0 if we have or don't have a pair with the key)
* keys (should return a sorted vector of all keys in the map)

*Reminder:* You should have made all of your private Tree functions protected, so you'll have access to them in the Map member functions you're writing!

**IMPORTANT:** Don't forget to be testing your functions as you make them! If you don't start with the subscript operator, it'll be pretty hard to test things as you'll have no way of populating the map.
