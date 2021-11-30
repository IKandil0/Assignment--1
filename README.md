using System;
using System.Collections.Generic;

class Program
{
    static void Main(string[] args)
    {
        Random r = new Random();
        var array1 = new int[10];
        var array2 = new int[10];
        InitData(array1, array2, r);
        Console.WriteLine();
        InterSection(array1, array2);
        Console.WriteLine();
        Union(array1, array2);
        Console.WriteLine();
        Differance(array1, array2);
    }
    static void InitData(int[] array1, int[] array2, Random r)
    {
        for (int i = 0; i < array1.Length; i++)
        {
            if (i == 0)
                Console.Write("[");
            array1[i] = r.Next(1, 10);
            Console.Write(String.Concat(array1[i], i == array1.Length - 1 ? "]" : ","));
        }
        Console.WriteLine();
        for (int i = 0; i < array1.Length; i++)
        {
            if (i == 0)
                Console.Write("[");
            array2[i] = r.Next(1, 10);
            Console.Write(String.Concat(array2[i], i == array1.Length - 1 ? "]" : ","));
        }
    }
    static void InterSection(int[] array1, int[] array2)
    {
        List<int> intersection = new List<int>();
        List<int> alldata = new List<int>();
        foreach (var data in array1)
            alldata.Add(data);
        foreach (var data in array2)
        {
            if (alldata.Contains(data) && !intersection.Contains(data))
                intersection.Add(data);
        }
        Console.Write(String.Concat("Inersection", " => "));
        int i = 0;
        foreach (var data in intersection)
        {
            if (i == 0)
                Console.Write("[");
            i++;
            Console.Write(string.Concat(data, i == intersection.Count ? "]" : ","));

        }
    }
    static void Union(int[] arr1, int[] arr2)
    {

        List<int> alldata = new List<int>();
        for (int i = 0; i < arr1.Length; i++)
            alldata.Add(arr1[i]);

        for (int i = 0; i < arr2.Length; i++)
        {
            if (!alldata.Contains(arr2[i]))
                alldata.Add(arr1[i]);
        }
        int U = 0;
        Console.Write(String.Concat("union", " => "));
        foreach (var data in alldata)
        {
            if (U == 0)
                Console.Write("[");
            U++;
            Console.Write(string.Concat(data, U == alldata.Count ? "]" : ","));
        }
    }
    static void Differance(int[] array1, int[] array2)
    {

        List<int> diffenace = new List<int>();
        List<int> alldata = new List<int>();
        foreach (var data in array1)
            alldata.Add(data);
        foreach (var data in array2)
        {
            if (!alldata.Contains(data) && !diffenace.Contains(data))
                diffenace.Add(data);
        }
        alldata.Clear();
        foreach (var data in array2)
            alldata.Add(data);
        foreach (var data in array1)
        {
            if (!alldata.Contains(data) && !diffenace.Contains(data))
                diffenace.Add(data);
        }
        Console.Write(String.Concat("differance", " => "));
        int i = 0;
        foreach (var data in diffenace)
        {
            if (i == 0)
                Console.Write("[");
            i++;
            Console.Write(string.Concat(data, i == diffenace.Count ? "]" : ","));

        }
    }
}
 
