GADGET PUZZLE

A firm wants to determine the highest floor of its n-story headquarters from which a gadget can fall without breaking. The firm has two identical gadgets to experiment with. 
If one of them gets broken, it cannot be repaired, and the experiment will have to be completed with the remaining gadget. Design an algorithm in the best efficiency class you can 
to solve this problem.

1. Binary Search + Linear Search (O(n) TC):
          If n is the number of floors, check if the first gadget breaks at n/2 position. There are two cases here -
             * If it breaks at n/2th floor, search sequentially from first floor and see at which floor the second gadget breaks.
             * If it doesn't break, the the mid point of range (n/2+1, n) and repeat the process.
   In the worst case scenario, if first breaks at n/2th and second also breaks at n/2th, then time complexity will be O(logn + n/2) = O(n/2)

2. Sqrt Decomposition (O(n ^ 1/2) TC):
         Divide the floors into segments whose size is calculated by taking the floor of sqrt(n). Check if first gadget breaks in the upper bound of each segment. Again there are
   two cases -
          * If it breaks, then we check if second gadget breaks in this segment only.
          * If it doesn't, it means the highest floor the gadgets don't break is nth floor. Return n.
//Code
#include<stdio.h>
#include<math.h>

int main()
{
    int n, breakPoint, i, segment, j;
    scanf("%d %d", &n, &breakPoint);

    segment = ceil(sqrt(n));

    for(i = 1; i < n; i++){
        if(i * segment >= breakPoint){
            break;
        }
    }

    if(i * segment == breakPoint){
        printf("%d", (i*segment));
        return 0;
    }

    j = (i-1) * segment;

    while(j < (i * segment)){
        if(j == breakPoint){
            break;
        }
    }

    printf("%d", j - 1);

    return 0;
}
