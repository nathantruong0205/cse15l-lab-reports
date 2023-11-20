# `reversed(int[] arr)

the bug that I plan to be writing about and fixing is the bug with the `reversed` method within ArrayExamples.java from the lab3 repository of week 4.

The initial code looks something like this

public class ArrayExamples {
  // Returns a *new* array with all the elements of the input array in reversed
 // order
  static int[] reversed(int[] arr) {
   int[] newArray = new int[arr.length];
   for(int i = 0; i < arr.length; i += 1) {
     arr[i] = newArray[arr.length - i - 1];
   }
   return arr;
 }
}
