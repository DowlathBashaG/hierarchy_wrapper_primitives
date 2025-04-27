# hierarchy_wrapper_primitives

what is the precedence order hierarchy for wrapper classes and object for Object,String,Integer,Number,Long and Double and Primitive datatype int,short,byte,char,long for these function overroadling and overriding.? Give the examples and answers.


"What is the precedence order (hierarchy) for wrapper classes, primitives, Object, String, Integer, Number, Long, Double in method overloading and overriding?"

Let’s break it down very simply but deeply 🔥.

📚 First, Basic Rules

			In Java Method Overloading, compiler decides which method to call at compile time (based on argument type).

Precedence for Choosing a Method in Overloading:


			Priority	Rule
			1️⃣	Exact primitive match (e.g., int matches int)
			2️⃣	Widening primitive (e.g., byte → short, int, long, float, double)
			3️⃣	Boxing (primitive → Wrapper class) (e.g., int → Integer)
			4️⃣	Widening after Boxing (e.g., Integer → Number → Object)
			5️⃣	Varargs (least priority)
			✅ Method Overriding is only for Runtime polymorphism — works only with inheritance classes.

🧠 Now, Understand the Type Hierarchy

			Object (topmost class)

			String (child of Object)

			Number (child of Object)

			Integer (child of Number)

			Long (child of Number)

			Double (child of Number)


			Class	Parent

			Object	-
			Number	Object
			Integer	Number
			Long	Number
			Double	Number
			String	Object (direct)
		
Primitive Types Widening:

			byte → short → int → long → float → double

			char → int → long → float → double

			📊 Precedence Order (in case of overloaded methods)
			For overloading resolution:

✅ Priority Order:

			Exact primitive > Widening primitive > Boxing > Widening after boxing > Object > Varargs
		
		
⚡ Examples
Let's create several overloaded methods:


			public class OverloadingPrecedence {

				void show(int i) {
					System.out.println("Primitive int");
				}

				void show(long l) {
					System.out.println("Primitive long");
				}

				void show(Integer i) {
					System.out.println("Wrapper Integer");
				}

				void show(Number n) {
					System.out.println("Number");
				}

				void show(Object o) {
					System.out.println("Object");
				}

				void show(String s) {
					System.out.println("String");
				}

				void show(Double d) {
					System.out.println("Double");
				}

				void show(int... i) {
					System.out.println("Varargs int...");
				}

				public static void main(String[] args) {
					OverloadingPrecedence obj = new OverloadingPrecedence();
					
					int a = 10;
					obj.show(a); // Primitive int → Exact match
					
					byte b = 10;
					obj.show(b); // byte widens to int → Primitive int

					short s = 10;
					obj.show(s); // short widens to int → Primitive int

					long l = 10L;
					obj.show(l); // Primitive long → Exact match

					char c = 'A';
					obj.show(c); // char widens to int → Primitive int

					Integer intObj = 10;
					obj.show(intObj); // Wrapper Integer → Exact match

					Double d = 10.5;
					obj.show(d); // Wrapper Double → Exact match
					
					Number n = 10;
					obj.show(n); // Number → Exact match
					
					Object o = new Object();
					obj.show(o); // Object → Exact match
					
					String str = "Hello";
					obj.show(str); // String → Exact match
				}
			}
			
🧩 Output:

			Primitive int
			Primitive int
			Primitive int
			Primitive long
			Primitive int
			Wrapper Integer
			Double
			Number
			Object
			String
			
🧠 Key Insights from the Above Example:

			Scenario	Which method?	Why?

			int	show(int)	Exact primitive match
			byte/short/char	show(int)	Widening to int
			long	show(long)	Exact primitive match
			Integer	show(Integer)	Exact wrapper match
			Double	show(Double)	Exact wrapper match
			Number	show(Number)	Exact match
			Object	show(Object)	Exact match
			String	show(String)	Exact match
			
⚠️ Important:

			Widening is preferred over boxing.

			Boxing is preferred over widening after boxing.

			Varargs (int...) is the least preferred — used only if nothing else matches.

🧠 Extra Advanced Tip for Interview:

			byte b = 10;
			obj.show(b); 

			It first tries widening to int.

			It won't box byte to Byte, because widening is preferred over boxing!

Similarly:

			Integer intObj = 10;
			obj.show(intObj);
			
			It matches exactly with show(Integer).

			If not available, it would go to Number, then Object.

🎯 Final Shortcut to Remember:

			Primitive first (widening if needed), Boxing second, Object third, Varargs last.

🚀 Conclusion

			Priority	Precedence
			1️⃣	Exact Primitive Match
			2️⃣	Widening Primitive
			3️⃣	Boxing
			4️⃣	Widening after Boxing (Wrapper → Parent Class like Number/Object)
			5️⃣	Object (topmost)
			6️⃣	Varargs
			📦 Bonus: Overriding vs Overloading
			Overriding depends only on runtime object type.

			Overloading depends on compile-time declared type.

