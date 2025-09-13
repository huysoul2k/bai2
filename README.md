using System;
using System.Collections.Generic;
using System.Linq;

namespace QuanLyDSHocSinh_LinQ
{
    class Student
    {
        public int Id { get; set; }
        public string Name { get; set; }
        public int Age { get; set; }

        public override string ToString()
        {
            return $"Id: {Id}, Name: {Name}, Age: {Age}";
        }
    }

    class QuanLyDSHocSinh_LinQ
    {
        static void Main(string[] args)
        {
            List<Student> students = new List<Student>
            {
                new Student { Id = 1, Name = "Huy", Age = 16 },
                new Student { Id = 2, Name = "Viet", Age = 14 },
                new Student { Id = 3, Name = "Thang", Age = 18 },
                new Student { Id = 4, Name = "Minh", Age = 15 },
                new Student { Id = 5, Name = "Hieu", Age = 19 }
            };

            Console.WriteLine("a. Danh sach hoc sinh:");
            students.ForEach(s => Console.WriteLine(s));
            Console.WriteLine();    

            Console.WriteLine("b. Hoc sinh tuoi tu 15 den 18:");
            var tuoi1518 = students.Where(s => s.Age >= 15 && s.Age <= 18);
            tuoi1518.ToList().ForEach(s => Console.WriteLine(s));
            Console.WriteLine();

            Console.WriteLine("c. Hoc sinh co ten bat dau bang 'A':");
            var batDauA = students.Where(s => s.Name.StartsWith("A"));
            batDauA.ToList().ForEach(s => Console.WriteLine(s));
            Console.WriteLine();

            Console.WriteLine("d. Tong tuoi tat ca hoc sinh trong danh sach:");
            int tongTuoi = students.Sum(s => s.Age);
            Console.WriteLine($"Tong tuoi = {tongTuoi}");
            Console.WriteLine();

            Console.WriteLine("e. Hoc sinh co tuoi lon nhat:");
            int maxAge = students.Max(s => s.Age);
            var lonNhat = students.Where(s => s.Age == maxAge);
            lonNhat.ToList().ForEach(s => Console.WriteLine(s));
            Console.WriteLine();

            Console.WriteLine("f. Danh sach sap xep theo tuoi tang dan:");
            var sapXep = students.OrderBy(s => s.Age);
            sapXep.ToList().ForEach(s => Console.WriteLine(s));
        }
    }
}
