
Lab 5: Binary Tree Applications
===================================

To do this excercise, first type into your terminal the following command:
`git clone https://github.com/Andre-Castro/cs14`. You should now see a folder with multiple .h,
.o and one main.cpp file.

Exercise 1 - Arithmetic Expression Trees
----------
Using the files provided for you from the git clone, we will be working with an arithmetic expression tree
(If you have had lab for this week, yes it is the same arithemetic expression trees you will be using in lab!).

Create a function `evaluate()` that takes the expression and evaluates the result.
For example, given the expression: `"1+5/2*4+3-1"`, the evaluation shold return 10 (using integer division).

Huffman Trees
-------------

####Introduction####
**Huffman coding** is a lossless data compression algorithm. The idea is to assign variable-length 
codes to input characters, lengths of the assigned codes are based on the frequencies of 
corresponding characters. The most frequent character gets the smallest code and the least frequent 
character gets the largest code. -Wikipedia
<br> Basically, let's say you have a message "M". By using Huffman coding, you can determine a coding
scheme for each letter in message "M". 
<br> For example, 
the letter "A" will be "10",<br>
the letter "B" will be "11", and <br>
the letter "C" will be "0".<br>
So, you can **encode** the message "ABC" as "10110".<br>
See?<br>
Well, anyway the point of Huffman coding is so that when you convert your message of characters
into a long list of zeros and ones, it will be **as short as possible**, otherwise known as 
**optimal**. The coding scheme is different for every message. There are usually more than one
way to make the Huffman tree. Here is how the tree looks like for our example:
![alt text](https://www.nayuki.io/res/reference-huffman-coding/code-tree-model.png)

The whole point of the tree is so that we can traverse it like a BST! To decode the message,
Make a for loop that iterates through the string "10110". You start at the root, 
then **go left if you see a '0' or go right if you see a '1'**. Try it by tracing through the tree!
The first character in "10110" is a '1' so let's start at the root and then go RIGHT.
Ok. Now the next character is a '0' so let's go LEFT. KAPOOYAH! Now we know the first
letter is 'A'. Cool, huh?

Exercise 2
----------
Ok, you don't have to worry about the Huffman encoding (you'll learn that in CS141). So we'll
use an online tool.
1. Make a secret message for the person next to you! Please try to keep it short 
       (like 1-3 short words). and try not to use too many different letters otherwise it 
       will be crazy for your partner!

2. Go to http://huffman.ooz.ie/

3. Type in your message and then click "generate a tree" at the top. 

4. Now encode your messsage by looking at the codes at each leaf of your tree. Send the picture
       of your tree and your secret message of zeros and ones to your partner!

5. Now you should have someone else's tree and secret message. Make the tree in C++! internal 
       nodes do not need any value just the leaves which should have the letter as a string.

6. Lastly, make a function called Decode() that takes in a string of zeros and ones and prints
       the decoded message! Read the "introduction" section above to see how the tree is used to decode
    (Go left if you see a zero and go right if you see a one).
