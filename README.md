# Plagarism-Detector
**Process:**
Taking 2 files, removing repeated words/ duplicates from each files using bloom filter, use robin carp to compare the probability of plagiarism then use Aho corasick for confirmation.

**Execution Steps:**
Taking 2 files as input. One source and one input file.
Convert all words from files into all CAPITALS.
Generate a bloom filter from source filter, and  input filters. 
(3 words at a time like sliding window)
Using 3 words as one pattern. (3 provided best results we can use 4/2 too.)
Remove all uncommon/duplicates from files using bloom filters.
(saving possible common words from files, for reducing file size)
Above step removes our file size by more than 50-60% on average so we don’t have to compute that much and time complexity gets reduced.
Then we check for plagiarism using robin carp
Then we check for exact plagiarism confirmation for output from robin carp using Aho-corasick algorithm for pattern searching.
We are checking for exact plagiarism for remaining patterns from bloom filters line by line using aho corasick for pattern searching.
Aho corasick will give exact common words.
Then we generate plagiarism percentages by using formulas (length of common words / length of input).
We also had the plagiarism indexes for highlighting the plagiarisms.


Bloom Filter: A Bloom filter is a space-efficient probabilistic data structure that is used to test whether an element is a member of a set. For example, checking availability of username is set membership problem, where the set is the list of all registered usernames. The price we pay for efficiency is that it is probabilistic in nature that means, there might be some False Positive results. False positive means, it might tell that given username is already taken but actually it’s not.
A Bloom filter is a data structure designed to tell you, rapidly and memory-efficiently, whether an element is present in a set. The price paid for this efficiency is that a Bloom filter is a probabilistic data structure: it tells us that the element either definitely is not in the set or may be in the set.The base data structure of a Bloom filter is a Bit Vector.

Robin Karp:  This algorithm slides the pattern one by one. After each slide, it one by one checks characters at the current shift and if all characters match then prints. It matches the hash value of the pattern with the hash value of the current substring of text, and if the hash values match then only it starts matching individual characters. So the Rabin Karp algorithm needs to calculate hash values for following strings.
1) Pattern itself. 
2) All the substrings of the text of length m. 
Since we need to efficiently calculate hash values for all the substrings of size m of text, we must have a hash function which has the following property.

Aho Corasick Algorithm:  The complexity of the Aho-Corasick algorithm is O(N + L + Z),input text length N, l is length  where Z is duplicated.
We create multiway tries. time complexity of creating and searching in tries O(w*n) : w= word count, n=average word length







