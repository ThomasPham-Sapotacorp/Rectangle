    using Microsoft.VisualBasic.CompilerServices;
    using System;
    using System.Linq;
    using System.Collections;
    using System.Collections.Generic;
    namespace Rectangle
    {
        class Rectangle
        {
            public int X1;
            public int Y1;
            public int X2;
            public int Y2;
            public int Width;
            public int Height;

            public Rectangle(int X1, int Y1, int X2, int Y2)
            {
                this.X1 = X1;
                this.Y1 = Y1;
                this.X2 = X2;
                this.Y2 = Y2;
                Height = Math.Abs(Y2 - Y1);
                Width = Math.Abs(X2 - X1);
            }

            public static int Min(int A, int B)
            {
                if (A < B)
                {
                    return A;
                }
                else
                {
                    return B;
                }
            }

            public static int Max(int A, int B)
            {
                if (A > B)
                {
                    return A;
                }
                else
                {
                    return B;
                }
            }

            public static Rectangle operator +(Rectangle A, Rectangle B)
            {
                int left = Max(A.X1, B.X1);
                int right = Min(A.X1 + A.Width, B.X1 + B.Width);
                int top = Max(A.Y1, B.Y1);
                int bot = Min(A.Y1 + A.Height, B.Y1 + B.Height);
                int w = right - left;
                int h = bot - top;
                if (w <= 0 || h <= 0)
                    return new Rectangle(0, 0, 0, 0);
                return new Rectangle(left, top, w, h); 
            }

            public void Area()
            {
                Console.WriteLine("Area of rectangle: "+ Height * Width);
            }

        }

        class Program
        {


            static void Main(string[] args)
            {

                Rectangle Test1 = new Rectangle(0, 0, 4, 3);
                Rectangle Test2 = new Rectangle(-2, 2, 2, 6);
                Rectangle Ghepdoi = Test1 + Test2;
                Ghepdoi.Area();



            }
        }
    }
