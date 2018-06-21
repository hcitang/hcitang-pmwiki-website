title: ''
author: ''
appears: ''
updated: Invalid date

---

(:source lang=C# :) <pre class="escaped">

using System.Reflection;

...

        public override string ToString() {
            StringBuilder sb = new StringBuilder();

            sb.Append(this.GetType().ToString() + ": {");
            sb.Append("Foo: {");
            foreach (PropertyInfo p in this.GetType().GetProperties(BindingFlags.Public | BindingFlags.Instance)) {
                sb.Append(p.Name + ": " + p.GetValue(this, null) + "; ");
            }
            sb.Append("}");
            return sb.ToString();
        }

</pre>
