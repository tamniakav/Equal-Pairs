using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Equal_Pairs
{
    class Program
    {
        static void Main(string[] args)
        {
            int n = int.Parse(Console.ReadLine());

            double sum1 = 0;
            double sum2 = 0;
            double sum4 = 0;

            double maxV = double.MinValue;
            double minV = double.MaxValue;


            if (n == 1)
            {
                double num1 = double.Parse(Console.ReadLine());
                double num2 = double.Parse(Console.ReadLine());
                sum1 = num1 + num2;
                Console.WriteLine($"Yes, value = {sum1}");
            }
            else if (n != 1)
            {

                for (int i = 0; i < n; i++)
                {
                    double num1 = double.Parse(Console.ReadLine());
                    double num2 = double.Parse(Console.ReadLine());

                    if (i == 0)
                    {
                        sum1 = num2 + num1;
                        sum2 = num1 + num2;
                    }
                    else if (i == 1)
                    {
                        sum2 = sum1;
                        sum4 = num1 + num2;

                        if (sum4 > sum2)
                        {
                            if (minV > sum2)
                            {
                                minV = sum2;
                            }
                            if (maxV < sum4)
                            {
                                maxV = sum4;
                            }
                        }
                        else
                        {
                            if (minV > sum4)
                            {
                                minV = sum4;
                            }
                            if (maxV < sum2)
                            {
                                maxV = sum2;
                            }
                        }
                    }
                    else
                    {
                        sum2 = sum4;
                        sum4 = num1 + num2;

                        if (sum4 > sum2)
                        {
                            maxV = sum4;
                            minV = sum2;
                        }
                        else
                        {

                            minV = sum4;

                            maxV = sum2;

                        }
                    }
                }
                double sum3 = maxV - minV;

                if (sum3 == 0)
                {
                    Console.WriteLine($"Yes, value = {sum2}");
                }
                else
                {
                    Console.WriteLine($"No, maxdiff = {sum3}");
                }
            }

        }
    }
}
