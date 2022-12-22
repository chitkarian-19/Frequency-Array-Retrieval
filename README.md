# Frequency-Array-Retrieval
Frequency Array Retrieval

Problem Link: https://www.codechef.com/problems/FREQARRRET
Solution Link: 

Solution description
```cpp
This question is providing the frequency array and we have to make the lexicograpically smallest array, for that we have to ensure that the first element of the output array becomes 1. We can't sort the array for sure, because the relative positioning will be hampered. So 1 will be having the frequency which is equal to the first value of the frequncy array.

To create the output array , we will use hashmap to store the the count and value assigned to that frequency item. We will be using one cntr value to generate new numbers , it will be assigned to 1 initially. We will loop inside the frequecny array, if the frequency item is present in the map then we will check what is the count value assigned to it, if it is less than the frequency item the count will be updated to count+1, otherwise the "value" associated to will be setteed to the cntr and the count willl be setted as 1, for that the frequency item. cntr will also be incremented by 1. If the frequency item is not present in the hashmap, then update cntr to cntr+1 and add the entry of the frequency item into the hashamp with the "value" equal to cntr and count equal to 1. After this data setting get the final "value" of freqeuncy item from the map and append into the output array. Here with "value", i mean with value associated with that key.

For final checking that it was possible or not, traverse into hashmap and check the count value associated to frequency item is equal to frequency item or not. If not then print -1, if yes for all the times then print the output array
```

Solution code:
```cpp
/* package codechef; // don't place package name! */

import java.util.*;
import java.lang.*;
import java.io.*;

/* Name of the class has to be "Main" only if the class is public. */
class Item{
    int value;
    int count;
    
    Item(int value,int count){
        this.count=count;
        this.value = value;
    }
}
class Codechef
{
	public static void main (String[] args) throws java.lang.Exception
	{
		// your code goes here
		Scanner sc = new Scanner(System.in);
		int t=sc.nextInt();
		StringBuilder op=new StringBuilder("");
		
		while(t-->0){
		      int n = sc.nextInt();
		      int[] arr = new int[n];
		      
		      for(int i=0;i<n;i++){
		          arr[i]=sc.nextInt();
		      }
		      
		      HashMap<Integer,Item> hmp = new HashMap<Integer,Item>();
		      
		      int cntr = 1;
		      StringBuilder res = new StringBuilder("");
		      for(int i=0;i<n;i++){
		          if(hmp.containsKey(arr[i])){
		              Item val = hmp.get(arr[i]);
		              
		              if(arr[i] == val.count){
		                  hmp.put(arr[i],new Item(cntr,1));
		                  cntr++;
		              }
		              else{
		                  hmp.put(arr[i],new Item(val.value,val.count+1));
		              }
		              res.append(hmp.get(arr[i]).value+" ");
		          }
		          else{
		              hmp.put(arr[i],new Item(cntr,1));
		              res.append(hmp.get(arr[i]).value+" ");
		              cntr++;
		          }
		      }
		      
		      for(Map.Entry<Integer,Item> item:hmp.entrySet()){
		          if(item.getKey()!=item.getValue().count){
		              res=new StringBuilder("-1");
		          }
		      }
		      
		      res.append("\n");
		      op.append(res);
		    
		}
		
		System.out.print(op.toString());
		
	}
}

```

Time COmplexity : O(N)
Space Complexity :O(N)
