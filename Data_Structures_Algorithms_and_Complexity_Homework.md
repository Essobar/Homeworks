1. What is the expected running time of the following C# code?
  * Explain why using Markdown.
  * Assume the array's size is n.
  ```
  long Compute(int[] arr)
  {
    long count = 0;
    for (int i=0; i<arr.Length; i++)
    {
        int start = 0, end = arr.Length-1;
        while (start < end)
            if (arr[start] < arr[end])
                { start++; count++; }
            else 
                end--;
    }
    return count;
  }
  ```
The expected running time is O(n^2) as the while -cycle has the same length n as the for -cycle. So the first cycle is iterated
n times and the nested second cycle also n times.

2. What is the expected running time of the following C# code?
  * Explain why using Markdown.
  * Assume the input matrix has size of n * m.
  ```
  long CalcCount(int[,] matrix)
  {
    long count = 0;
    for (int row=0; row<matrix.GetLength(0); row++)
        if (matrix[row, 0] % 2 == 0)
            for (int col=0; col<matrix.GetLength(1); col++)
                if (matrix[row,col] > 0)
                    count++;
    return count;
  }
  ```
  It can be only O(n) if every row starts with an odd number. Then it iterates only the outer loop n times. But the worst case
  scenario is that every row starts with an even number, then the expected running time is O(n*m).
  
3. (*) What is the expected running time of the following C# code?
  * Explain why using Markdown.
  * Assume the input matrix has size of n * m.
  ```
  long CalcSum(int[,] matrix, int row)
  {
    long sum = 0;
    for (int col = 0; col < matrix.GetLength(0); col++) 
        sum += matrix[row, col];
    if (row + 1 < matrix.GetLength(1)) 
        sum += CalcSum(matrix, row + 1);
    return sum;
  }

  Console.WriteLine(CalcSum(matrix, 0));
  ```
  Here the expected running time is O(n^m) as the for loop is iterated n times and the loop is recursively called m times.
