

(:source lang=C# :) <pre class="escaped">
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using System.Runtime.Serialization;
using System.Runtime.Serialization.Formatters.Binary;

namespace ConsoleApplication1 {
    class Program {
        static void Main(string[] args) {
            Foo f = new Foo() { Foobar = 3, Baz = 4 };
            Console.WriteLine("F: " + f);

            string file = Path.GetTempFileName();
            Stream s = File.Open(file, FileMode.Create);
            BinaryFormatter bf = new BinaryFormatter();
            bf.Serialize(s, f);
            s.Close();

            f = null;

            s = File.Open(file, FileMode.Open);
            bf = new BinaryFormatter();
            f = (Foo)bf.Deserialize(s);
            s.Close();

            Console.WriteLine("F: " + f);
         }

    }

    [Serializable]
    class Foo : ISerializable {
        public int Foobar { get; set; }
        public int Baz { get; set; }

        public Foo() {
        }

        public Foo(SerializationInfo info, StreamingContext ctxt) {
            this.Foobar = (int)info.GetValue("Foobar", typeof(int));
            this.Baz = (int)info.GetValue("Baz", typeof(int));
        }

        public void GetObjectData(SerializationInfo info, StreamingContext ctxt) {
            info.AddValue("Foobar", this.Foobar);
            info.AddValue("Baz", this.Baz);
        }

        public override string ToString() {
            return "Foobar: " + this.Foobar + "; Baz: " + this.Baz;
        }
    }
}

</pre>
