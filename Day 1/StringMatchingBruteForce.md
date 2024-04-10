#### How many comparisons (both successful and unsuccessful) will be made by the brute-force algorithm in searching for each of the following patterns in the binary text of one thousand zeros? Explain along answer

a. 00001
b. 10000
c. 01010

Text = 000000000.......
a. Pattern = 00001
   For every index i from 0 to (n - m), first 4 zeroes match but the last 1 doesn't match. So 5 comparitions will be made at each index.
   n - m = (1000 - 5) = 995 indexes
   Because it is 0-indexed, 995+1 = 996 indexes
   The total number of comparisions is 996*5 = 4980
b. Pattern = 10000
   For every index i from 0 to (n - m), the first character 1 itself doesn't match. So 1 comparision is made at each index.
   (n - m) = (1000 - 5) = 995 indexes
   0-indexed, so 996 indexes.
   The total number of comparisions is 996*1 = 996
c. Pattern = 01010
   For every index i from 0 to (n - m), the first character matches, second character 1 doesn't match. So 2 comparisions is made at each index.
   (n - m) = (1000 - 5) = 995 indexes
   0-indexed, so 996 indexes.
   The total number of comparisions is 996*2 = 1992
