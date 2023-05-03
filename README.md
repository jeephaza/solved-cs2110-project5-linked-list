Download Link: https://assignmentchef.com/product/solved-cs2110-project5-linked-list
<br>
In this assignment, you will be implementing a list data structure whose underlying implementation is a doubly-linked list. If you have taken CS 1331/32 (don’t worry if you haven’t taken 32), then you should be familiar with this data structure.

<h1><a name="_Toc7065"></a>2           Linked List Implementation</h1>

We are implementing a doubly-linked list. You are given a list which has a head pointer pointing to the first node in the list. Each node contains a next pointer to the next node in the list, a prev pointer to the previous node in the list and a data pointer to a Process. Refer to the following diagram for a visual representation to help you out when implementing your linked list!

<h1><a name="_Toc7066"></a>3           Instructions</h1>

You have been given one C file – list.c in which to implement the data structure. Implement all functions in this file. Each function has a block comment that describes exactly what it should do and there is a synopsis included below.

<ul>

 <li>Process *create_Process(char *, int): Takes in a string and an int. Create a new process with name equal to the passed in string, and priority equal to the passed in int. Assign a new PID one higher than the previous PID, with the first one being 0.</li>

 <li>ListNode *create_node(Process *): Takes in a Process, creates a ListNode containing that Process as its data, and returns the ListNode.</li>

 <li>List *create_list(): creates an empty list and returns it</li>

 <li>void push_front(List *, ListNode *): adds a ListNode to the front of the List ( the beginning of the list, so that this node becomes the new head of the list ).</li>

 <li>void push_back(List *, ListNode *): adds a ListNode to the back of the List ( the end of the list, so that this node becomes the last node in the list )</li>

 <li>int remove(List *, Process **, int): finds and removes the Process whose PID is equal to the third input. The Process data will be returned via the Process** parameter and the ListNode containing the Process will be removed completely.</li>

 <li>void destroy_Process(Process *): completely destroys all data in the Process and the Process itself.</li>

 <li>void destroy(List *): destroys the list itself. This will destroy the list, all nodes within the list, and the Processes within the nodes.</li>

 <li>int copy_Process(Process *, Process **): creates a deep copy of a Process and returns the deep copy through the Process ** parameter.</li>

 <li>List *copy_list(List *): creates a deep copy of the list. This includes creating a new list, new nodes, and new Processes in the nodes.</li>

 <li>int compare_PID(Process *, Process *): Compares the two Processes based off of PID.</li>

 <li>int compare_name(Process *, Process *): Compares two Processes based on their name</li>

 <li>int swap_nodes(ListNode *, ListNode *, List *): Swaps the two nodes in the list in place.</li>

 <li>int sort(List *, int (*compare_func)(Process *, Process *b)): Utilizes the compare function pointer to sort the list (in place) in ascending order.</li>

 <li>int make_idle(Process *): Append ” (idle)” to the end of the name of the passed in process. You must use realloc and any functions you may need from string.h.</li>

 <li>int make_active(Process *): See if the process name ends with ” (idle)” If it does, remove it. You must use realloc and any functions you may need from string.h.</li>

 <li>int map_inplace(List *, int (*map_func)(Process *)): Calls the map function pointer on each Process in the list.</li>

 <li>Process **list_to_array(List *, int): Converts the linked list data structure to an array of pointers to Processes while removing the linked list structure itself so that only the process pointers remain.</li>

</ul>

You should not be leaking memory in any of the functions. For any functions utilizing malloc, if malloc returns null, return either 0 or null (based on the function header) and ensure that no memory is leaked.

Be sure not to modify any other files. Doing so may result in point deductions that the tester will not reflect.

<h1><a name="_Toc7067"></a>4           Checker/Makefile Usage</h1>

<h2><a name="_Toc7068"></a>4.1           Testing &amp; Debugging</h2>

We have provided you with a test suite to check your linked list that you can run locally on your very own personal computer. You can run these using the Makefile.

Note: There is a file called test_utils.o that contains some functions that the test suite needs. We are not providing you the source code for this, so make sure not to accidentally delete this file as you will need to redownload the assignment. Also keep in mind that this file does not have debugging symbols so you will not be able to step into it with gdb (which will be discussed shortly).

Your process for doing this homework should be to write one function at a time and make sure all of the tests pass for that function. Then, you can make sure that you do not have any memory leaks using valgrind. It doesn’t pay to run valgrind on tests that you haven’t passed yet. Further down, there are instructions for running valgrind on an individual test under the Makefile section, as well as how to run it on all of your tests.

The given test cases are the same as the ones on Gradescope. Note that you will pass some of these tests by default. Your grade on Gradescope may not necessarily be your final grade as we reserve the right to adjust the weighting. However, if you pass all the tests and have no memory leaks according to valgrind, you can rest assured that you will get 100 as long as you did not cheat or hard code in values.

You will not receive credit for any tests you pass where valgrind detects memory leaks or memory errors. Gradescope will run valgrind on your submission, but you may also run the tester locally with valgrind for ease of use.

Printing out the contents of your structures can’t catch all logical and memory errors, which is why we also require you run your code through valgrind.

We certainly will be checking for memory leaks by using valgrind, so if you learn how to use it, you’ll catch any memory errors before we do.

Here are tutorials on valgrind:

<ul>

 <li><a href="http://cs.ecs.baylor.edu/~donahoo/tools/valgrind/">http://cs.ecs.baylor.edu/~donahoo/tools/valgrind/</a></li>

 <li><a href="http://valgrind.org/docs/manual/quick-start.html">http://valgrind.org/docs/manual/quick-start.html</a></li>

</ul>

Your code must not crash, run infinitely, nor generate memory leaks/errors. Any test we run for which valgrind reports a memory leak or memory error will receive no credit.

If you need help with debugging, there is a C debugger called gdb that will help point out problems. See instructions in the Makefile section for running an individual test with gdb.

If your code generates a segmentation fault then you should first run gdb before asking questions. We will not look at your code to find your segmentation fault. This is why gdb was written to help you find your segmentation fault yourself.

Here are some tutorials on gdb:

<ul>

 <li><a href="https://www.cs.cmu.edu/~gilpin/tutorial/">https://www.cs.cmu.edu/~gilpin/tutorial/</a></li>

 <li><a href="http://www.cs.yale.edu/homes/aspnes/pinewiki/C%282f%29Debugging.html">http://www.cs.yale.edu/homes/aspnes/pinewiki/C%282f%29Debugging.html</a></li>

 <li><a href="http://heather.cs.ucdavis.edu/~matloff/UnixAndC/CLanguage/Debug.html">http://heather.cs.ucdavis.edu/~matloff/UnixAndC/CLanguage/Debug.html</a></li>

 <li><a href="http://heather.cs.ucdavis.edu/~matloff/debug.html">http://heather.cs.ucdavis.edu/~matloff/debug.html</a></li>

 <li><a href="http://www.delorie.com/gnu/docs/gdb/gdb_toc.html">http://www.delorie.com/gnu/docs/gdb/gdb_toc.html</a></li>

</ul>

Getting good at debugging will make your life with C that much easier.

<h2><a name="_Toc7069"></a>4.2           Makefile</h2>

We have provided a Makefile for this assignment that will build your project. Here are the commands you should be using with this Makefile:

<ol>

 <li>To clean your working directory (use this command instead of manually deleting the .o files): make clean</li>

 <li>To run the tests without valgrind or gdb: make run-tests</li>

 <li>To run your tests with valgrind: make run-valgrind</li>

 <li>To debug a specific test with valgrind: make TEST=test_name run-valgrind</li>

 <li>To debug a specific test using gdb: make TEST=test_name run-gdb Then, at the (gdb) prompt:

  <ul>

   <li>Set some breakpoints (if you need to — for stepping through your code you would, but you wouldn’t if you just want to see where your code is segfaulting) with b suites/list_suite.c:420, or b list.c:69, or wherever you want to set a breakpoint</li>

   <li>Run the test with run</li>

   <li>If you set breakpoints: you can step line-by-line (including into function calls) with s or step over function calls with n</li>

   <li>If your code segfaults, you can run bt to see a stack trace</li>

  </ul></li>

</ol>

For more information on gdb, please see one of the many tutorials linked above.

To get an individual test name, you can look at the output produced by the tester. For example, the following failed test is test_list_size_empty:

suites/list_suite.c:906:F:test_list_size_empty:test_list_size_empty:0: Assertion failed… ^^^^^^^^^^^^^^^^^^^^

Beware that segfaulting tests will show the line number of the last test assertion made before the segfault, not the segfaulting line number itself. This is a limitation of the testing library we use. To see what line in your code (or in the tests) is segfaulting, follow the “To debug a specific test using gdb” instructions above.

Note: The checker may not reflect your actual grade on this assignment. We reserve the right to update the checker as we see fit when grading.

<h1><a name="_Toc7070"></a>5           Deliverables</h1>

Submit ONLY list.c.

Your files must compile with our Makefile, which means it must compile with the following gcc flags:

-std=c99 -pedantic -Wall -Werror -Wextra -Wstrict-prototypes -Wold-style-definition

All non-compiling homeworks will receive a zero. If you want to avoid this, do not run gcc manually; use the Makefile as described below.

Please check your submission after you have uploaded it to Gradescope to ensure you have submitted the correct file.