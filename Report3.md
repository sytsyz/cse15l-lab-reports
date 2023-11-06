## Part 1 Bugs
Chosen bug: ReversedInPlace
1. A failure-inducing input 
```
@Test 
	public void testReverseInPlace2()
  {
    int[] input1 = { 1,2,7 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 7,2,1 }, input1);
	}
```
2. An input that doesn’t induce a failure
```
@Test 
	public void testReverseInPlace3()
  {
    int[] input1 = { };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ }, input1);
	}
```
3. Symptoms
   - failure input
     <img width="993" alt="image" src="https://github.com/sytsyz/cse15l-lab-reports/assets/146896888/39fc2b73-b6f2-4644-85cd-37316b4a2f7a">
   - no failure input
     <img width="943" alt="image" src="https://github.com/sytsyz/cse15l-lab-reports/assets/146896888/06bf5d96-8ab3-4373-a191-acf9eb15ada7">
4. The Bug
   - Before
   ```
   // Changes the input array to be in reversed order
    static void reverseInPlace(int[] arr) 
    {
      for(int i = 0; i < arr.length; i += 1) 
      {
        arr[i] = arr[arr.length - i - 1];
      }
    }
   ```
   - After
   ```
   // Changes the input array to be in reversed order
   static void reverseInPlace(int[] arr) 
    {
      for(int i = 0; i < arr.length/2; i += 1) 
      {
        int temp = arr[i];
        arr[i] = arr[arr.length - i - 1];
        arr[arr.length-i-1] = temp;
      }
    }
   ```
  - Explanation
    The original code did not fulfill the fuction of reserve the input, it simply rewrite the array in the beginning by the number at the end of the array.
    As a result, the original code will have an output which an array that contains only the last number in the array. The fix address this issue. By adding a temperory
    number holder "temp", the code is now able to store the original number before it get rewrite by the last number of the array, then able to put this temp number towards
    the last places of the array. 
     


