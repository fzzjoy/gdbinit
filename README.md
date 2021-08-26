 # STL GDB evaluators/views/utilities - 1.03

   The new GDB commands:                                                         
 	    are entirely non instrumental                                             
 	    do not depend on any "inline"(s) - e.g. size(), [], etc
       are extremely tolerant to debugger settings
                                                                                 
   This file should be "included" in .gdbinit as following:
   source stl-views.gdb or just paste it into your .gdbinit file

   The following STL containers are currently supported:

       std::vector<T> -- via pvector command
       std::list<T> -- via plist or plist_member command
       std::map<T,T> -- via pmap or pmap_member command
       std::multimap<T,T> -- via pmap or pmap_member command
       std::set<T> -- via pset command
       std::multiset<T> -- via pset command
       std::deque<T> -- via pdequeue command
       std::stack<T> -- via pstack command
       std::queue<T> -- via pqueue command
       std::priority_queue<T> -- via ppqueue command
       std::bitset<n> -- via pbitset command
       std::string -- via pstring command
       std::widestring -- via pwstring command

   The end of this file contains (optional) C++ beautifiers
   Make sure your debugger supports $argc

   Simple GDB Macros writen by Dan Marinescu (H-PhD) - License GPL
   Inspired by intial work of Tom Malnar, 
     Tony Novac (PhD) / Cornell / Stanford,
     Gilad Mishne (PhD) and Many Many Others.
   Contact: dan_c_marinescu@yahoo.com (Subject: STL)

   Modified to work with g++ 4.3 by Anders Elton
   Also added _member functions, that instead of printing the entire class in map, prints a member.

# How To
1. copy the file .gdbinit to user main dir: ~/
2. then use the above command in gdb, you can see the contents of the container.

        (gdb) pmap
        Prints std::map<TLeft and TRight> or std::multimap<TLeft and TRight> information. Works for std::multimap as well.
        Syntax: pmap <map> <TtypeLeft> <TypeRight> <valLeft> <valRight>: Prints map size, if T defined all elements or just element(s) with val(s)
        Examples:
        pmap m - prints map size and definition
        pmap m int int - prints all elements and map size
        pmap m int int 20 - prints the element(s) with left-value = 20 (if any) and map size
        pmap m int int 20 200 - prints the element(s) with left-value = 20 and right-value = 200 (if any) and map size
        (gdb) q


