<div align="center">

## Understanding Polymorphism


</div>

### Description

This tutorial is meant to cover the bare basics of polymorphism.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Karthik Veeramani](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/karthik-veeramani.md)
**Level**          |Beginner
**User Rating**    |4.9 (141 globes from 29 users)
**Compatibility**  |Java \(JDK 1\.1\), Java \(JDK 1\.2\), Java \(JDK 1\.3\), Java \(JDK 1\.4\), Java \(JDK 1\.5\)
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__2-57.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/karthik-veeramani-understanding-polymorphism__2-4811/archive/master.zip)





### Source Code

<p><p>This tutorial is meant to cover the bare basics of polymorphism. I assume you
 know a little about object oriented programming, and some basic Java syntax.</p>
<p>Here is what my Merriam-Webster dictionary says </p>
<p><font color="#0000FF">poly.mor.phism</font> : the quality or state of being
 able to assume different forms</p>
<p>This is what your school book on OOPS would've told you. This is the definition
 my teacher used to expect for questions on polymorphism. I used to blindly memorize
 this and vomit it on the exam paper. Now that I know a little more about it,
 let me try to save you from doing the same, if you are still in school.</p>
<p>Don't expect a definition of polymorphism from me, coz it'll be nothing more
 than what you saw just now. But once you finish reading the tutorial, come back,
 read the definition again, see if it makes sense.</p>
<p>Back in school, when we used to do C++, this question used to appear in every
 test - "What are the different types of polymorphism? Give examples".
 Some book I read described two types of polymorphism - <b>static</b> and <b>dynamic</b>.
 According to the book, a static polymorphism is like this - say you need to
 write a program that adds two <i>int </i>data types; and then you also need
 to add two <i>long </i>data types; and then you need to add two <i>float </i>data
 types. Your sense of logic will tell you that, if you name the 3 functions as
 add1(), add2() and add3(), the person using your function (perhaps you, after
 a month) will think you have the weirdest naming habits in the world of computer
 programmers. What can be done better? addInt(), addFloat(), addLong()? Not bad.
 Actually, with parameters, it'll look like this -<br>
 addInt(int a, int b), addFloat(float a, float b), addLong(long a, long b). This
 is fine, and its not too hard to remember. However, you don't want a software
 engineer to look at you like an insect. So, switch over to what a hard core
 techie would've done - </p>
<p>add(int a, int b)<br>
 add(float a, float b)<br>
 add(long a, long b)</p>
<p>That looks cool, doesn't it? Don't argue with me, just accept it. This is exactly
 what the book described as static polymorphism - the ability to overload a function's
 name with different sets of parameters, so that the same function name stands
 for everything. In other words, overloading a function to make it assume different
 forms! The second definition would've brought me closer to the geek world. Now,
 when you really call these functions, the compiler looks at what type you actually
 pass, and calls the correct version. If you try to confuse the compiler by passing
 ambiguous types, it'll either choose one using its sense of logic, or will throw
 an error. OK. That was just a warmup for you. Our concentration is going to
 be on the other type - dynamic polymorphism - so lets not bother about this.
</p>
<p>I hope you know what inheritance is, atleast a little. I have a class by name
 Human that looks like this -</p>
<pre>class Human {
 public String getGender() {return "Neutral";}
}
</pre>
There is nothing much to explain in that. The class Human, that represents a human,
has a single method, that returns the sex. I'm returning a "neutral"
for this. Now, here comes a Man who is a Human.<br>
<pre>class Man extends Human {
}
</pre>
And here is a Woman who is also a Human<br>
<pre>class Woman extends Human {
}
</pre>
No difficulties, right? A quick look at what has been done - we have a base class
called Human, that has a single method. Two classes Man and Woman inherit the
Human class. That means, both of them have the method getGender() - in other words,
once you create an object of <i>any</i> of these classes, you can invoke the getGender()
method. Example,
<pre>Human human = new Human();
System.out.println("Gender: " + human.getGender());
Man man = new Man();
System.out.println("Gender: " + man.getGender());
Woman woman = new Woman();
System.out.println("Gender: " + woman.getGender());
</pre>
What do you think the output will be? You'll see three "Neutral"s on
the screen. Is something going wrong? Ofcourse. You know what it means when you
say a man is neutral :) . Now to fix it... we could <i>override</i> the method
getGender() in the subclasses.<br>
<br>
<pre>class Man {
 public String getGender() {return "Man";}
}
</pre>
<pre>class Woman {
 public String getGender() {return "Woman";}
}
</pre>
Now run the code, you'll get Neutral, Man and Woman respectively from the 3 print
statements. Well if you think thats polymorphism, no. That was just overriding
a base class's method. Nothing more. Look at the following lines closely (same as
above).
<pre>Human human = new Human();
System.out.println("Gender: " + human.getGender());
Man man = new Man();
System.out.println("Gender: " + man.getGender());
</pre>
<p>I'm going to make a small change in the 3rd line. <br>
</p>
<pre>Human human = new Human();
System.out.println("Gender: " + human.getGender());
<b>Human man = new Man();</b>
System.out.println("Gender: " + man.getGender());
</pre>
<p>What did I change? The <i>reference type</i>. If you are not familiar with
 that term, get familiar now. In that line, "man" is a <i>reference</i>
 to an <i>object. </i>But normally, we mean the object when we speak about the
 reference. There is a difference between the lines</p>
<pre>Human man;
man = new Man();</pre>
<p>First line, you declared an <i>object reference</i>. The <i>reference type</i>
 of this <i>reference</i> is Human. Second line, you actually created the object.
 The object that has been created is of the type Man. That is, the <i>object
 type</i> is Man. Hope its clear.<br>
</p>
<p>Now coming back to where we stopped, the change in the above code is, the reference
 type. The reference type points to the base class, while the object points to
 the derived class. Before I go further, think about the output of the above
 code (the 4 line code block). The first println is as usual, it prints Neutral.
 The second? Prints Man! So what does that imply? The method that got invoked,
 is the version thats present in the <i>object type </i>and NOT the <i>reference
 type. </i>Repeat the previous line 5 times, scribble it on the wall, open notepad
 and type it a few times. This is where polymorphism begins to show its color.
 What exactly is the use of this? Consider the code below:</p>
<pre>public void printTheRightGender(char g) {<br> <br> <b>Human human;</b> // Pay attention - my reference type is human.
<br> if(g == 'H') {<br> human = new Human();<br> System.out.println(human.getGender());<br> }
 else if(g == 'M') {
 <b>human = new Man();</b> // See how the object type changes, though reference type remains the same.
 System.out.println(human.getGender());
 }
 else if(g == 'F') {
 <b>human = new Woman();</b> // See how the object type changes, though reference type remains the same.
 System.out.println(human.getGender());
 }
 else {
 System.out.println("No such species");
 }
}
</pre>
<p>Voila! All I did was have a single reference type, and churn out different
 objects depending on my input! I know that wasn't the most useful piece of code
 you'd've seen, but thats enough to put you on the first gear. This is essentially
 <i>dynamic polymorphism</i>. The same object reference (that is, an object reference
 of the same reference type) is capable of behaving differently at runtime, depending
 on the object that it points to.</p>
<p>Now, a small question. Is this possible -</p>
<pre>Man man = new Human();
</pre>
<p>Nope. A man is a human, but not every human is a man. And Java compiler knows
 this. It won't let you compile the program. An object reference can only point
 to its own type, or to its derived classes's objects. What you are doing is
 the other way round - a <i>downcast</i> (and how many geek terms did we learn
 till now?).<br>
 <br>
 Now lets digest polymorphism with a more complex, more practical example. Quickly
 whip up a file by name BikeShop.java and dump whatever I'm going to give below
 in it. Or you can have separate files for each class. Your choice.</p>
<pre>class Bike {</pre>
<pre> public String getModel() {
 return "Not Applicable";
 }
 public String getManufacturer() {
 return "Not Applicable";
 }</pre>
<pre> public double getCost() {
 return 0.0; // Cheap, huh?
 }
}</pre>
<pre>class Splendor extends Bike {
 public String getModel() {
 return "Splendor";
 }
 public String getManufacturer() {
 return "Hero Honda";
 }</pre>
<pre> public double getCost() {
 return 45000.00;
 }
}</pre>
<pre>class Pulsar extends Bike {
 public String getModel() {
 return "Pulsar";
 }
 public String getManufacturer() {
 return "Bajaj";
 }</pre>
<pre> public double getCost() {
 return 55000.00;
 }
}</pre>
<pre>class Fiero extends Bike {
 public String getModel() {
 return "Fiero";
 }</pre>
<pre> public String getManufacturer() {
 return "Suzuki";
 }
 public double getCost() {
 return 52000.00;
 }
}</pre>
<p>There is no confusion I believe. The base class Bike retuns junk when you call
 its methods. However, the derived classes Splendor, Pulsar and Fiero return
 the details specific to them. Now for the coup de grace - watch how my last
 nail seals the coffin... Introducing, the BikeShop class!</p>
<pre>public class BikeShop {</pre>
<pre> public static void main(String[] ar) {
 System.out.println("Welcome to The Bike Shop");
 System.out.println("------------------------");
 System.out.println("Models available:");
 System.out.println("Splendor ...... S");
 System.out.println("Pulsar ...... P");
 System.out.println("Fiero ...... F");
 System.out.print("To get details about a model, enter the code: ");</pre>
<pre> BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
 String choice = null;
 try {
 choice = reader.readLine();
 } catch(Exception x) {}</pre>
<pre> Bike bike = getTheRightBike(choice); // this line assigns the correct object to this reference.
 if(bike == null) {
 System.out.println("Invalid code.");
 System.exit(1);
 }
 System.out.println("Model : " + bike.getModel());
 System.out.println("Maunfacturer : " + bike.getManufacturer());
 System.out.println("Cost : " + bike.getCost());
 }</pre>
<pre> public static Bike getTheRightBike(String bikeCode) {
 if(bikeCode == null) return null;
 if(bikeCode.equals("S")) {
 return new Splendor();
 // The above line returns an object of derived class.
 // Note that the return type of this method is base class type.
 // Doing this is allowed because... thats polymorphism!
 }
 else if(bikeCode.equals("P")) {
 return new Pulsar();
 }
 else if(bikeCode.equals("F")) {
 return new Fiero();
 }
 else return null;
 }
}</pre>
<p>And we are done. The getTheRightBike() method has its return type as Bike,
 the base class. However, depending on the parameter passed, it decides which
 class to instantiate, and returns the instance. Note that, it is allowed to
 return an instance of the Bike class, or instances of any of its derived classes.
 And similarly, the main method assigns the returned object to a reference of
 type Bike. This code doesn't have the usual ingredients like Exception etc.,
 because I decided to keep it as simple as possible. I have done very minimal
 error checking, by making the getTheRightBike() method return null if a wrong
 parameter is passed. </p>
<p>Actually, if you happen to look at more sophisticated tutorials or books, you
 are likely to see the name BikeFactory instead of BikeShop. 'Factory' is the
 fancy term used to denote a class that produces objects of different types depending
 on the inputs. So don't be emotionally upset when you see someone use the term
 the next time.</p>
<p>Another small thing to remember. You must have noticed that I kept returning
 junk values for the base class methods, if its not applicable. The better way
 to do it is, mark the method "abstract" (use the Java keyword abstract
 in the method declaration). If you make one or more methods abstract, you need
 to mark the whole class as abstract. By making a method abstract, you mean that,
 any class that derives from this class, SHOULD give a proper implementation
 to that method (proper doesn't mean it should make sense logically; you can
 even have a blank implementation). See this -</p>
<pre>public abstract class Human {
 public abstract void getGender(); // No implementation at all!
}
public class Man extends Human {
 public void getGender() { ... } // If you don't do this, you'll get a compile time error.
}
</pre>
So as I said, if you don't implement the getGender() method, you have two options
- one is, make the Man class also abstract, other is, close your Java editor and
sleep. And what if ALL your methods are going to be abstract? Yes, its fine. But
you may also want to have an "interface" instead of a "class".
That is, by using the <i>interface</i> keyword instead of <i>class</i> keyword,
you mean that, all the methods contained withing are <i>implicitly abstract. </i>That
is, you don't even need to add that abstract keyword in front of your methods,
its understood.
<pre>public interface Human {
 public void getGender(); // Now, did I say something about abstract? No. Its understood.<br>}</pre>
<p></p>
<p>The tutorial is supposed to end here. But before I finish, I thought I'll show
 you a few gotchas that I learnt while preparing for the Sun certification exam.
 So here we go. We have been dealing with methods, methods and just methods in
 this tutorial. How about attributes (or member variables, as C++ programmers
 say)? Take a look -</p>
<pre>class BaseClass {
 public String name = "BaseClass";
 public void print() {
 System.out.println("I am the base class");
 }
}</pre>
<pre>class DerivedClass extends BaseClass {
 public String name = "DerivedClass";
 public void print() {
 System.out.println("I am the derived class");
 }
}</pre>
<pre>public class Tester {
 public static void main(String[] ar) {
 BaseClass base = new BaseClass();
 BaseClass derived = new DerivedClass();
 base.print();
 derived.print();
 System.out.println("From base class object : " + base.name);
 System.out.println("From derived class object : " + derived.name);
 }
}
 </pre>
<p>I know you would've sensed something fishy, coz I woudn't have bothered telling
 you this. Now, lets rip it down. The first two lines in the main method of Tester
 class should be clear, we've been doing it all along. Both references have their
 reference type as BaseClass, but they point to different objects. The third
 and fourth line should also be clear, because I've explained it so patiently
 in this tutorial already. You must expect the third line to print "I am
 a base class" and the next line to print "I am a derived class".
 If that surprised you... well, forget it. </p>
<p>The fifth line. What do you expect? I expect "BaseClass", because
 its pretty normal. Because, the object and the object reference are of the type
 BaseClass, so there is no surprise in that. The sixth line.... prints "BaseClass"
 !! Surprised? Thats is how it works. What happens can be explained like this
 -</p>
<p>When the object reference is of base class type,<br>
 And when the object is of derived class type,<br>
 When you invoke a method, the derived class version is called.<br>
 BUT, when you invoke an attribute, the base class version is called!</p>
<p>Remember that. You may not come across this normally, but be prepared if you
 are taking a Java exam, or you want to flaunt your Java knowledge.</p>
<p>And... that... was... polymorphism... for you. Cast a vote if you liked it.</p>
<p> </p>

