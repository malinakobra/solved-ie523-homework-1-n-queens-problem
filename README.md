Download Link: https://assignmentchef.com/product/solved-ie523-homework-1-n-queens-problem
<br>
The original version of this problem goes like this – You have a 8 × 8 chessboard, and you have to place 8 queens on this chessboard such that no two of them threaten each other. Since a queen can attack any piece that shares a row, column, or diagonal, with it, we are essentially looking to place 8 elements in a 8 × 8 grid such that no two of them share a common row, column, or diagonal. You can read more about this problem at <a href="https://en.wikipedia.org/wiki/Eight_queens_puzzle">this link</a><a href="https://en.wikipedia.org/wiki/Eight_queens_puzzle">.</a>

The <em>n </em>× <em>n </em>version of this problem asks you to place <em>n </em>queens on a <em>n </em>× <em>n </em>chessboard. For the first part of this assignment we are seeking just one solution (among a set of many possible solutions) to this problem. You have to solve this by a recursive implementation of the <em>backtracking </em>search/algorithm, and it must be done in an “object-oriented” manner. For the second part, we seek all possible solutions to the problem, by modifying the code for the first part.

Assume you have gone through the necessary steps to define a <em>n </em>× <em>n </em>chessboard. You must do the following:

<ol>

 <li>Write a function is this position safe(<em>i,j</em>), which returns “true” (resp. “false”) if placing a queen in the (<em>i,j</em>)-th position in the <em>n </em>× <em>n </em>chessboard is safe (resp. unsafe).</li>

 <li>Implement a recursive back-tracking search procedure solve(<em>i</em>), as shown in figure 2, which returns “true” if there is a way to place a queen at the <em>i</em>-th column of the <em>n </em>× <em>n </em>chessboard, where 0 ≤ <em>i </em>≤ <em>n </em>− 1 (notice: the indexing starts from 0 and ends with <em>n</em>−1). You call solve(0) to solve the puzzle.</li>

</ol>

<h1>Finding one solution to the <em>N</em>-Queens Problem</h1>

Just to get us thinking in object-oriented terms, I want you to do the following:

<ol>

 <li>Define a class called Board, it should have a private data member called size (which is <em>n </em>in the <em>n</em>×<em>n </em>chessboard), and a integer-valued chessboard. If there is a queen at the (<em>i,j</em>)-th position of the <em>n </em>× <em>n </em>chessboard, then chessboard[<em>i</em>][<em>j</em>] = 1, otherwise, chessboard[<em>i</em>][<em>j</em>] = 0.</li>

 <li>Keep in mind, the value of <em>n</em>(= size) is not known a priori – <strong>it will be known at runtime when the user inputs it via the commandline </strong>(you should pay attention to this when I go over it in class). One way is to accomplish this is to have a private data member declared as int **chessboard, and once the size of the chessboard is known, you can declare an array using a <em>pointer-to-pointers </em> If you need help with this</li>

</ol>

<em>Boolean </em><strong>Solve</strong>(column)

1: <strong>if </strong>column ≥ <em>n </em><strong>then</strong>

2:                You have solved the puzzle.

3: <strong>else</strong>

4:                  <strong>for </strong>0 ≤ row ≤ <em>n </em>− 1 <strong>do</strong>

5:                          <strong>if </strong>is this position safe(row, column) <strong>then</strong>

6:                                Place queen at (row<em>,</em>column)-position in the <em>n </em>× <em>n </em>chessboard.

7:               <strong>if </strong>Solve(column+1) <strong>then </strong>8:                      Return <em>true</em>.

9:                            <strong>else</strong>

10:                                     Remove queen at (row<em>,</em>column)-position in the <em>n </em>× <em>n </em>chessboard.

Placing it here was a bad idea.

11:                          <strong>end if</strong>

12:                   <strong>end if</strong>

13:             <strong>end for</strong>

14: <strong>end if</strong>

{ /* If we got here then all assignments of the queen in (column-th column are invalid. So, we return <em>false</em>*/}. 15: Return <em>false</em>.

Figure 1: Pseudo-code for the recursive implementation of the exhaustivesearch algorithm for the (<em>n</em>×<em>n</em>) Queens-puzzle. You solve the puzzle by calling <strong>Solve</strong>(0), assuming the indices are in the range {0<em>,</em>1<em>,…,n </em>− 1}.

<em>// N Queens Problem                via       ( Backtracking ,        which     is       implemented      by )      Recursion</em>

<em>// Written           by     Prof .       Sreenivas       for      IE523 :       Financial       Computing</em>

<strong>#include </strong><em>&lt;</em>iostream<em>&gt;</em>

<strong>#include </strong>”N queens .h”

<strong>int </strong>main ( <strong>int </strong>argc , <strong>char </strong>∗ <strong>const </strong>argv [ ] )

{ Board x ;

<strong>int </strong>board size ; sscanf ( argv [1] , ”%d” , &amp;board size );

x . nQueens( board size );

<strong>return </strong>0;

}

Figure 2: f16 prog1 hint.cpp: C++ code to help you with Programming Assign-

part, you might want to see the handout “Programming Assignment 5: Dynamic Arrays in C++” in the Bootcamp folder on Compass.

<ol start="3">

 <li>I also want you to write a member function that prints the (solved) chessboard. Although I do not want you to mimic my output exactly, something similar will be sufficient.</li>

 <li>I have provided partial code samples for the *.cpp file in figure 2, and the *.h file in figure 3. Two sample outputs are shown in figure 4.</li>

</ol>

Here is what I want from you for the first part of the assignment

<ol>

 <li>A well-commented C++ code that produces output that is similar to what is shown in figure 4.</li>

</ol>

You will submit this electronically to the TA before the due date.

<h1>Finding all solutions to the <em>N</em>-Queens Problem</h1>

.

For this part of the assignment I want you to extend/modify the code for the previous part of the assignment, where you found a single solution to the <em>N</em>-Queens Problem, to find <u>all </u>solutions to the <em>N</em>-Queens problem.

Keep in mind that the number of solutions can grow to be very large very quickly. Table 1 shows the number of solutions for different values of <em>N</em>. I am looking for outputs along the lines of what is shown in figures 5, 6 and 7.

<strong>#ifndef </strong>N queens

<strong>#define </strong>N queens <strong>using namespace </strong>std ;

<strong>class </strong>Board

{

<em>//                      p r i v a t e        data                 member :          s i z e                o f                    t h e                  board </em><strong>int </strong>size ;

<em>// p o i n t e r </em>−<em>to</em>−<em>p o i n t e r i n i t i a l i z a t i o n o f t h e board </em><strong>int </strong>∗∗chess board ;

<em>// p r i v a t e member f u n c t i o n : r e t u r n s ’ f a l s e ’ i f // t h e ( row , c o l ) p o s i t i o n i s not s a f e . </em><strong>bool </strong>is this position safe (<strong>int </strong>row , <strong>int </strong>col )

{

<em>//      w r i t e     t h e       a p p r o p r i a t e        code      on      your      own      t h a t      r e t u r n s</em>

<table width="367">

 <tbody>

  <tr>

   <td width="18"> </td>

   <td width="42"><em>//</em></td>

   <td width="33"><em>” t r u e ”</em></td>

   <td width="146"><em>i f         t h e        ( row , c o l )         p o s i t i o n</em></td>

   <td width="128"><em>i s       s a f e .         I f     i t     i s</em></td>

  </tr>

  <tr>

   <td width="18"> </td>

   <td width="42"><em>//</em></td>

   <td width="33"><em>u n s a f e</em></td>

   <td width="146"><em>( i . e .            some       o t h e r       queen        can</em></td>

   <td width="128"><em>t h r e a t e n            t h i s        p o s i t i o n )</em></td>

  </tr>

  <tr>

   <td width="18">}</td>

   <td width="42"><em>//</em></td>

   <td width="33"><em>r e t u r n</em></td>

   <td width="146"><em>” f a l s e ”</em></td>

   <td width="128"> </td>

  </tr>

  <tr>

   <td width="18"><em>//</em></td>

   <td width="42"><em>p r i v a t e</em></td>

   <td width="33"><em>member</em></td>

   <td width="146"><em>f u n c t i o n :               i n i t i a l i z e s        t h e</em></td>

   <td width="128"><em>( n     x    n )      c h e s s b o a r d</em></td>

  </tr>

 </tbody>

</table>

<strong>void </strong>initialize (<strong>int </strong>n)

{

size = n;

<em>//      w r i t e     t h e       a p p r o p r i a t e        code       t h a t      u s e s     t h e         p o i n t e r </em>−<em>to</em>−<em>p o i n t e r</em>

<em>// method to i n i t i a l i z e t h e ( n x n ) c h e s s b o a r d . Once i n i t i a l i z e d , // put z e r o s in a l l e n t r i e s . L a t e r on , i f you p l a c e d a queen in // t h e ( i , j )</em>− <em>th p o s i t i o n , then c h e s s b o a r d [ i ] [ j ] w i l l be 1 .</em>

}

<em>// p r i v a t e member f u n c t i o n : p r i n t s t h e board p o s i t i o n </em><strong>void </strong>print board ()

{

std :: cout <em>&lt;&lt; </em>size <em>&lt;&lt; </em>”−Queens Problem Solution” <em>&lt;&lt; </em>std :: endl ;

<em>//      w r i t e     t h e       a p p r o p r i a t e        code        here      to      p r i n t       out     t h e     s o l v e d</em>

<em>//       board      as       shown       in     t h e       a s s i g n m e n t        d e s c r i p t i o n</em>

}

<em>// p r i v a t e member f u n c t i o n : r e c u r s i v e b a c k t r a c k i n g </em><strong>bool </strong>solve (<strong>int </strong>col ) {

<em>//         implement         t h e       r e c u r s i v e         b a c k t r a c k i n g        p r o c e d u r e        d e s c r i b e d       in</em>

<em>//      p s e u d o c o d e         format        in      f i g u r e      1    o f     t h e        d e s c r i p t i o n       o f     t h e      f i r s t</em>

<em>//                        programming   a s s i g n m e n t </em>}

<strong>public </strong>:

<em>// S o l v e s t h e n</em>−<em>Queens problem by ( r e c u r s i v e ) b a c k t r a c k i n g </em><strong>void </strong>nQueens( <strong>int </strong>n)

{ initialize (n);

<strong>if </strong>( solve (0)) print board ();

<strong>else</strong>

std :: cout <em>&lt;&lt; </em>”There is no solution to the ” <em>&lt;&lt; </em>n <em>&lt;&lt; </em>”−QueensProblem” <em>&lt;&lt; </em>std :: endl ;

}

};

<strong>#endif</strong>

Figure 3: f16 prog1 hint.h: C++ code to help you with Programming Assign-

Figure 4: Sample output of the code shown in figure 2.

<table width="192">

 <tbody>

  <tr>

   <td width="60"><em>N </em>× <em>N</em></td>

   <td width="132">Total #of Solutions</td>

  </tr>

  <tr>

   <td width="60">8 × 8</td>

   <td width="132">92</td>

  </tr>

  <tr>

   <td width="60">9 × 9</td>

   <td width="132">352</td>

  </tr>

  <tr>

   <td width="60">10 × 10</td>

   <td width="132">724</td>

  </tr>

  <tr>

   <td width="60">11 × 11</td>

   <td width="132">2,680</td>

  </tr>

  <tr>

   <td width="60">12 × 12</td>

   <td width="132">14,200</td>

  </tr>

  <tr>

   <td width="60">13 × 13</td>

   <td width="132">73,712</td>

  </tr>

  <tr>

   <td width="60">etc.</td>

   <td width="132">etc</td>

  </tr>

 </tbody>

</table>

Table 1: #Solutions to the <em>N</em>-Queens problem as a function of <em>N</em>.

Figure 5: Sample output of the code that computes all solutions to the <em>N</em>Queens Problem. This is for <em>N </em>= 4.

Figure 6: Sample output of the code that computes all solutions to the <em>N</em>Queens Problem. This is for <em>N </em>= 8.

Figure 7: Sample output of the code that computes all solutions to the <em>N</em>Queens Problem. This is for <em>N </em>= 11.