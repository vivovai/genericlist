# genericlist
using System;
using System.Collections;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace GenericList
{
    class MyList<T> : IEnumerable<T>
    {
        private T[] items;

        public MyList()
        {
            this.items = new T[16];
            this.Count = 0;
        }

        public void Add(T element)
        {
            this.items[this.Count] = element;
            this.Count++;

        }

        public int Count { get; private set; }

        public IEnumerator<T> GetEnumerator()
        {
            for (int index = 0; index < this.Count; index++)
            {
                yield return this.items[index];
            }
        }

        IEnumerator IEnumerable.GetEnumerator()
        {
            return this.GetEnumerator();
        }
    }
}
######################################################################################

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace GenericList
{
    class Program
    {
        static void Main(string[] args)
        {
            MyList<int> test = new MyList<int>();

            test.Add(5);
            test.Add(6);
            test.Add(2);
            test.Add(3);
            test.Add(25);
            test.Add(53);

            foreach (var item in test)
            {
                Console.WriteLine(item);
            }

        }
    }
}
