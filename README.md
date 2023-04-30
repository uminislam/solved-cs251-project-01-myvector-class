Download Link: https://assignmentchef.com/product/solved-cs251-project-01-myvector-class
<br>
In class we have been discussing the implementation of the built-in C++ <strong>std::vector</strong> class, which is based on a dynamically-allocated array.  In this project you’re going to re-implement vector as your own <strong>myvector</strong> class, using an implementation of your own design.

The assignment consists of 4 parts, which walks you through the process of starting with a simple myvector of integers, and ending with a templated-version of myvector based on your own implementation.  Approach the assignment part by part.

<strong><u>Part 01:</u></strong><strong>   </strong>

See zybooks section 1.9.  Complete exercise.

<strong><u>Part 02:</u></strong><strong>   </strong>

See zybooks section 1.10.  Complete exercise.

<strong><u>Part 03:</u></strong><strong>   </strong>

See zybooks section 1.11.  Complete exercise.

<strong><u>Part 04:</u></strong>

At this point, you should have a working <strong>myvector&lt;T&gt;</strong> class that is (a) templated, and (b) implemented in some approach other than the dynamically-allocated array we have discussed in class.  Make sure you have 3 constructors:  default, copy constructor, and one that takes an initial_size.  As discussed in part 03, the goal is for you to develop an approach that improves upon the array-based implementation in some way.  For example, perhaps you want to take an approach that avoids the cost of re-allocating the array when it’s full, e.g. using a linked-list.  Of course, with a linked-list the cost of accessing an element will jump from O(1) to O(N), so that’s a costly trade-off.  Perhaps you can think of a better approach that avoids the cost of reallocating the array, while retaining O(1) access to any element <em>in most cases</em>?  Take some time to think about your implementation (and the trade-offs), draw some diagrams, and then implement.




Here in part #04, the expectation is that you’ll work outside of zybooks so that you can do more extensive testing, since the “Movie Reviews” program is not an extensive test of myvector&lt;T&gt; functionality.  How you do this testing we’re going to leave to you, but testing is a skill that takes practice to develop.  In short, think of ways to break your myvector&lt;T&gt; class, and write code to make sure your vector&lt;T&gt; class works as required.  Can you insert thousands




Here in part #04 you are also required to add three additional functions to your myvector&lt;T&gt; class, as defined below:




//

// <strong>erase</strong>

//

// erase the element at position i from the vector by overwriting it and  // reducing the size (# of elements); the ith element is returned //

// Assume: 0 &lt;= i &lt; Size

//

<strong>T erase(int i); </strong>




//

// <strong>[]</strong> //

// returns a reference to the element at position i so the element can // be read or written

//

// Assume: 0 &lt;= i &lt; Size

//

<strong>T&amp; operator[](int i); </strong>

<strong> </strong>

//

// <strong>rangeof</strong>

//

// Returns the elements in the range of positions i..j, inclusive.

// The elements are returned in a dynamically-allocated C-style array.

//

// Example: if i is 2 and j is 4, then an array containing 3

// elements is returned:  element position 2, element position 3, and // element position 4.

//

// Assume: 0 &lt;= i &lt;= j &lt; Size

//

<strong>T* rangeof(int i, int j) </strong>




In general, assume all parameters to the myvector&lt;T&gt; class are valid — we’ll worry about proper error checking later.  Do not add a destructor, we’ll discuss destructors and proper memory deallocation in future projects.  However, you should free memory within your other functions, e.g. in class we discussed the freeing of the old array in push_back.

<h1>Requirements</h1>

Your approach needs to use pointers in some way, above and beyond a single pointer to a dynamicallyallocated array.  A simple one or two-way linked-list is a valid approach, but will not receive full credit — you can do better than that.  Do not use any of the built-in containers of C++ (e.g. do not use std::vector to implement myvector).  We aren’t looking for the best possible data structure, those are coming later.  Just something better than a linked-list, if posible.




You will be expected to update the comments in “myvector.h”, including the header comment to explain your implementation approach.  Ultimately we will be grading both the correctness and the quality of your implementation in “myvector.h”.  Be sure the header comment includes your name, and motivates your approach — what trade-offs are you making in comparison to the dynamic, array-based approach?




Keep all implementation details private.  You’ll probably need to define a private struct or class, e.g. to define a **NODE** in a linked-list.  The proper way to do this is within the *private* section of your **myvector** class, like this:




<strong>template&lt;typename T&gt; class myvector </strong>

{ private:

<strong>struct NODE </strong>

<strong>  { </strong>

<strong>    … </strong>

<strong>  }; </strong>




// rest of myvector class, which can now use struct NODE };




<h1>Programming Environment</h1>

You are welcome to program on whatever platform you want, using whatever compiler / programming environment you want.  If you not sure what to use, or have no environment available, use Codio; see Appendix at end of this document for getting started with Codio.




<h1>Have a question?  Use Piazza, not email</h1>

As discussed in the syllabus, questions must be posted to our course Piazza site — questions via email will be ignored.  Remember the guidelines for using Piazza:




<ol>

 <li><em><u>Look before you post</u></em> — the main advantage of Piazza is that common questions are already answered, so search for an existing answer before you post a question. Posts are categorized to help you search, e.g. “HW”.</li>

 <li><u>Post publicly</u> — only post privately when asked by the staff, or when it’s absolutely necessary (e.g. the question is of a personal nature). Private posts defeat the purpose of piazza, which is answering questions to the benefit of everyone.</li>

 <li><u>Ask pointed questions</u> — do not post a big chunk of code and then ask “help, please fix this”. Staff and other students are willing to help, but we aren’t going to type in that chunk of code to find the error.  You need to narrow down the problem, and ask a pointed question, e.g. “on the 3<sup>rd</sup> line I get this error, I don’t understand what that means…”.</li>

 <li><u>Post a screenshot</u> — sometimes a picture captures the essence of your question better than text. Piazza allows the posting of images, so don’t hesitate to take a screenshot and post; see <a href="http://www.take-a-screenshot.org/">http://www.take</a><a href="http://www.take-a-screenshot.org/">–</a><a href="http://www.take-a-screenshot.org/">a</a><a href="http://www.take-a-screenshot.org/">–</a><a href="http://www.take-a-screenshot.org/">org/</a> .</li>

 <li><u>Don’t post your entire answer / code</u> — if you do, you just gave away the answer to the ENTIRE CLASS. Sometimes you will need to post code when asking a question — in that case post only the fragment that denotes your question, and omit whatever details you can.  If you must post the entire code, then do so privately — there’s an option to create a private post (“visible to staff only”).</li>

</ol>

<h1>Appendix:  Codio Programming Environment</h1>

Here’s a quick summary of how to get started with Codio.  Codio is cloud-based, and accessible via a web browser.  It’s platform-neutral and works from any platform, but you must be online to use it.  The first step is to create a Codio account and join the class (“CS 251 Fall 2019”):




<a href="https://codio.com/p/join-class?token=brigade-america">https://codio.com/p/join</a><a href="https://codio.com/p/join-class?token=brigade-america">–</a><a href="https://codio.com/p/join-class?token=brigade-america">class?token=brigade</a><a href="https://codio.com/p/join-class?token=brigade-america">–</a><a href="https://codio.com/p/join-class?token=brigade-america">america</a>




Be sure to register using your UIC email address, especially since you may be using this account in future CS classes.  The above link will provide access to Codio, and the resources associated with CS 251.




Once you successfully login to Codio, you’ll see the project “<strong>cs251-project01-myvector</strong>” pinned to the top of your dashboard.  This represents a container-based C++ programming environment — think light-weight virtual machine (VM).  When you are ready to start programming, click “Ready to go” and Codio will startup the VM and within a few seconds you’ll have a complete Ubuntu environment at your disposal.  In particular, you’ll have access to C++ via the GNU g++ compiler.  You also have super-user (root) access, so you can install additional software if you want (“sudo aptget install XYZ”).




Once I login, I normally split the right-side into 2 windows: the top as my editor pane, and the bottom as my terminal window.  This can be done via the View menu, Panels, Split Horizontal.  Then click on the bottom window, drop the Tools menu, and select Terminal.  Here’s a snapshot showing “student.cpp” (from lab 01) open in the editor, and the terminal window open below it:




For the purposes of project #01, nothing is provided other than a makefile — use the File “Upload…” to upload your “myvector.h” code from zybooks, along with other files you might need.  At the very least you’ll want to create a new “main.cpp” file for testing purposes, and #include “myvector.h”.  You can use the provided makefile to compile and run:

type “make build” to compile, and “make run” to execute.


