Download Link: https://assignmentchef.com/product/solved-cs1301-lab-03-parsing-tweets-with-the-string-class
<br>
Good programmers think before they begin coding. Part I of this assignment involves brainstorming with a group of peers with no computers to talk about a strategy for solving this week’s lab. Breakup into groups based on your seating (3-4 people per group) and brainstorm about how to solve the problems below. Make sure everyone understands the problem and sketch out potential ways to move toward a solution.  You may find it helpful to look over the required readings for this week.

<strong>Note: Brainstorms are to help you get started with the lab and get you in the habit of designing before you code.  You won’t submit them to eLC. </strong>

Introduction

Twitter and similar micro-blogging platforms allow users to broadcast short messages to a potentially large audience. With Twitter, the messages are called “tweets” and consist of 140 characters or less. Tweets are often sent from mobile phones, and tweeters can choose whether their tweets are public or not.

The platforms allow people to communicate in ways that were not possible even a few years ago, and they have already had a profound effect on society. They even affect how society reacts to natural and manmade disasters—ordinary citizens can now broadcast timely and location specific information that is of vital importance to both emergency management agencies and members of the public.

Sifting through the tweets for useful information is difficult, however. As a result, there have been proposals to manually add structure to tweets sent during disasters. One proposal is called Tweak the Tweet (TtT).<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a> In TtT, information is marked using a “hashtag”  such as <strong>#loc </strong>(for location):

<strong>MT @carlseelye: #lovelandfire #Wind just switched and now the smoke is thick around our house #loc 40.352,-105.2045</strong>

Adding the structure makes it far easier for a computer to classify the tweets.

In this lab, you will use methods of the <strong>String</strong> class to process messages similar to TtT tweets (the data is made from real TtT data but it has been altered to suit the lab). You will use the <strong>substring</strong> and other methods to pull out information from the text, manipulate it, and print it out to the screen.

<h2>Lab Objectives</h2>

By the end of the lab, you should:

<ul>

 <li>understand how <strong>String</strong> constants and String objects are represented in Java;</li>

 <li>be able to declare, initialize, and assign variables of type <strong>String</strong>;</li>

 <li>perform string processing using the methods of the <strong>String</strong> class;</li>

 <li>concatenate strings (and other values) together using the ‘<strong>+</strong>‘ operator.</li>

</ul>

<strong> </strong>

Prerequisites

The lab deals with material from Chapter 2 (specifically, the discussions of the <strong>String</strong> class). It assumes you know how define simple classes in Java, and that you can declare and assign values to variables.

<h2>Exercise – Parsing Tweets</h2>

The class <strong>ParseTheTweet</strong> will read in a single tweet from the keyboard, and so when writing your program, you will need to use the <strong>Scanner</strong> class in addition to the <strong>String</strong> class.  As usual, almost everything you write will go in the <strong>main</strong> method of the <strong>ParseTheTweet</strong> class.




The tweets processed by the call all encode the following information using so-called “hashtags”:

The report <em>type</em> (<strong>#typ</strong>); some further <em>detail</em> (<strong>#det</strong>); a location (<strong>#loc</strong>) such as a street address; and latitude (<strong>#lat</strong>) and longitude (<strong>#lng</strong>). The type indicates the meaning of the tweet (i.e., whether it is a request for help or reports factual information), and the report detail provides additional information.  Each of the hashtags is followed by some value (such as an actual latitude or longitude value).

When writing your code, you can assume that all of the tweets to process have the following format:

<strong>#typ </strong><em>value</em><strong>; #det</strong><em> value</em><strong>; #loc</strong><em> value</em><strong>; #lat </strong><em>value</em><strong>; #lng </strong><em>value</em><strong>; </strong>

That is, they consist of a series of hashtags, each followed by a value, and each value followed by a semicolon (<strong>;</strong>). 9 sample tweets are provided at the end of this document.  You should test your code on them.

Instructions

<ol>

 <li>At the top of your source file, include a comment stating your Java class name, your name, the date, the program purpose, and containing the statement of academic honesty as you did in previous labs.</li>

 <li>Use the <strong>Scanner </strong>class (as discussed in lecture) to read in a tweet entered by the user and store it in a <strong>String</strong> variable named <strong>tweet</strong>.</li>

</ol>

&#x25aa; <strong><u>Hint</u></strong><u>:</u> Using the <strong>Scanner </strong>class involves 1) importing a package, 2) creating a

Scanner object, and 3) using the appropriate method to read in a whole line of text.

<ol start="3">

 <li>You will be splitting up (parsing) the information in the tweet into the 5 different types of information specified by the hashtags (type, location, detail, latitude, &amp; longitude). Declare variables to store each of these pieces of information. Be sure to give these variables the appropriate data types and meaningful names.</li>

 <li>Now you actually need to divide the information in the tweet into the separate substrings of information. Declare 2 variables (<strong>start </strong>and <strong>finish</strong>) to hold the indices of where each substring starts and finishes.</li>

</ol>

&#x25aa; <strong><u>Hint</u></strong><u>:</u> Each substring <em>starts</em> with a hashtag and <em>finishes</em> with a semicolon ( Is there a

String class method that you can use to get the index of  “#typ” or a ‘;’ ?)




start                finish




<strong>#typ </strong><em>value</em><strong>; #det</strong><em> value</em><strong>; #loc</strong><em> value</em><strong>; #lat </strong><em>value</em><strong>; #lng </strong><em>value</em><strong>; </strong>




<ol start="5">

 <li>Once you have numbers assigned to <strong>start</strong> and <strong>finish</strong>, we want to discard the #tag and extract only the value. We know that the ‘;’ is where the value finishes – but we need to find the index where the actual <em>value </em> Hint: our <strong>start</strong> variable currently points to the index of the “#” – and we know that all hashtag identifiers have the format, hashtag, 3 letters, and a space. Can we do simple math here to figure out the starting position of our <em>value?</em></li>

 <li>Once we have the correct starting and ending positions for the value, we want to extract the substring at those positions and assign it to the appropriate variable declared in step 3.

  <ul>

   <li>The <strong>trim()</strong> method removes leading and trailing white spaces (if any) from a<strong> String</strong>. Use the <strong>t</strong>rim() method on each resultant <strong>String</strong>.</li>

   <li><strong><u>Hint</u></strong><u>:</u> The <strong>trim()</strong> method returns a modified <strong>String</strong>, but does not alter the <strong>String</strong> object that calls it. Ensure you are (re-)assigning a <strong>String</strong> to the result of <strong>trim()</strong>.</li>

  </ul></li>

</ol>

<strong>Example </strong>

String original = ”  text here   “;

String trimmed = original.trim(); //trimmed contains “text here”  //At this point, the original string still contains — ”  text here   ”

<ol start="7">

 <li>After extracting the value encoded by each hashtag, we discard that part of the tweet String – we are finished with it and are ready to repeat these steps for the next hashtag. We can use the <strong>substring</strong> method to extract the substring of our tweet variable starting where the last hashtag <em>finished </em><strong>( </strong>Hint: we know it finishes at a semicolon – and we have that index stored in our finish variable, and we want to start right <strong>after</strong> that semicolon – Also, remember that if we pass the substring method only 1 value, it begins at that index and goes until the end of the String).</li>

</ol>

<strong> </strong>

DISCARD                                          SUBSTRING STORED IN TWEET




<strong> </strong>




<ol start="9">

 <li>The <strong>type</strong> values come from a very small set of values, and we want to make them all caps. To do this, use the <strong>toUpperCase</strong> method of the <strong>String</strong></li>

 <li>We also want to ensure that the <strong>detail</strong> and <strong>location</strong> values are free of commas (which might pose an obstacle to further processing). Use the <strong>replace</strong> method of the <strong>String</strong> class to do this. Replace each comma with a single hyphen (-).</li>

 <li>Now use <strong>out</strong> and <strong>print </strong>or <strong>println</strong> statements to produce formatted output, as shown in the included examples.</li>

</ol>

<strong>HINT:</strong> Use the escape sequence <strong>t</strong> to include tabs as needed.













<h1>Additional Requirements</h1>

These are things that make the graders lives easier, and ultimately, you will see in the real world as well. Remember the teaching staff does not want to touch your code after they gave you requirements; they want to see the perfect results they asked for! Here is a checklist of things you can<strong> lose points</strong> for:




<ul>

 <li>(10 points) If the source file(s)/class(es) are named incorrectly (case matters!)</li>

 <li>(10 points) If your source file(s) have a package declaration at the top</li>

 <li>(10 points) If any source file you submit is missing your Statement of Academic Honesty at the top of the source file. All submitted source code files must contain your Statement of Academic Honesty at the top of each file.</li>

 <li>(10 points) If you have more than one instance of Scanner in your program. Your program should only have one instance of Scanner.</li>

 <li>(15 points) Inconsistent I/O (input/output) that does not match our instructions or examples exactly (unless otherwise stated in an assignment’s instructions). Your program’s I/O (order, wording, formatting, etc.) must match our examples and instructions.</li>

 <li>(100 points) If the source file(s) are not submitted before the specified deadline’s late period ends (48 hours after the deadline) or if they do not compile.</li>

 <li>(25 points) Late penalties will be deducted as per the course syllabus.</li>

 <li>If your (10 points) comments or (10 points) variables are “lacking” o Here, “lacking” means that you or a TA can find <strong>any</strong> lines of code or variables that take more than 10 seconds to understand, and there is no comment, or the variable name does not make sense (variable names like <strong>b</strong>, <strong>bb</strong>, <strong>bbb</strong>, etc. <strong>will</strong> <strong>almost never be acceptable) </strong></li>

 <li>(10 points) Indentation is not consistent throughout your source code o Refresh your memory of indentation patterns in chapter 2 in the course textbook</li>

</ul>

o Be careful of a combination of tabs and spaces in your files (use one or the other)!




If any of the above do not make sense to you, talk to a TA, or ask on Piazza!




<a href="#_ftnref1" name="_ftn1"><u>[1]</u></a> <a href="http://epic.cs.colorado.edu/?page_id=11">http://epic.cs.colorado.edu/?page_id=11</a>