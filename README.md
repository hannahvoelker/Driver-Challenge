# Driver-Challenge
Coding Challenge for Summer 2017 Internship Opportunity

## The Problem:
The input to the problem is at most 50 DNA sequences (i.e, the character set is limited to T/C/G/A) whose length does not exceed 1000 characters. The sequences are given in FASTA format [https://en.wikipedia.org/wiki/FASTA_format]. These sequences are all different fragments of one chromosome.

The specific set of sequences you will get satisfy a very unique property:  there exists a unique way to reconstruct the entire chromosome from these reads by gluing together pairs of reads that overlap by more than half their length. An example set of input strings is attached.

The output of your program should be this unique sequence that contains each of the given input strings as a substring.

## My approach: 
We need to find the overlaps in these reads and join based on these overlaps. 
This means:
  0. Proper parsing of the input file
  1. Cleaning up the data (e.g, getting rid of read names and newline characters)
  2. Utilizing an algorithim that allows us to join reads that overlap by more than half of their length

For this, I utilized the 'greedy algorithim' that continuously finds the shortest substring between two elements in an array and merges them until there is only one element left in the array-- our desired result. Oftentimes, this algorithim does not properly produce the shortest substring, but for this problem, we have the invariant that each read that we merge into the substring must overlap by more than half of its length, thus making this algorithim much more likely to produce the desired output. 

#### Some other notes about this project:
My first attempt for this problem involved building two tries (prefix trees): one for the first half of each word, another for the second half of each word. Both tries had the index in the array the prefix/suffix could be found in as a sentienel, making for easy lookup. I had worked on this approach because I knew it would be optimal time- O(nk), where n is the number of reads, and k is the maximum length of a read. Unfortunately, I hit a roadblock- specifically, the tries couldn't be utilized properly since not every read is the same length, and thus were not being filled properly. Back to square one, and thus the idea for using the greedy algorithim was born. At least I learned how to implement a trie in Python. :)
