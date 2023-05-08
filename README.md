Download Link: https://assignmentchef.com/product/solved-project-2-overview-computer-science-143
<br>
<h1>Prerequisite</h1>

Prerequisites are the same as with Project 1 (how convenient!). We expect familiarity with the Unix environment as well as the ability to code effectively in Python, or can quickly get up to speed. We expect the resources and links on the project pages will provide you with enough information to get you started even in case you are not familiar with either one.

While Spark was initially developed to work natively with Scala, it was later extended to work natively with Python, so we will use Python for this project.

<h2>System Setup</h2>

To help students set up the uniform environment for the class project, we will again be using <a href="https://www.virtualbox.org/">VirtualBox</a><u>​</u> to run the Linux operating system in a <u>​</u><a href="https://www.virtualbox.org/manual/ch01.html">virtual machine</a>​. VirtualBox allows a single machine to share resources and run multiple operating systems simultaneously. You will need to download the following files

<ul>

 <li><a href="https://www.virtualbox.org/wiki/Downloads">VirtualBox binary file</a> <u>​ </u>for your host Operating System if you haven’t already</li>

 <li>VirtualBox Image: <u>​</u><a href="https://drive.google.com/file/d/1LZXL8BSvTceD0lmzJJvF1SRKxZSDLje1/view?usp=sharing">CS143-P2.ova</a>​ (requires UCLA BOL login) – This is a very large file (~3-4GB), so it may take a while to download.</li>

</ul>

As of 5/12/19 1:30pm, the proper hash for CS143-P2.ova is 7158ebb33d11d27665961fb7a58c78e1​ (MD5) and e3ee5b39bf15dc6122a8874556f6d884f71590db​ (SHA1).




Please follow our ​<a href="https://docs.google.com/document/d/1hILSiWyDTeyb3HVvSWyYadzx3zfFh_DMuBp4xokuInM/edit#heading=h.fmzhf2fws11j">VirtualBox setup instruction</a>​ to install VirtualBox on your own machine.

The provided virtual machine image is based on Ubuntu 19.04, PostgreSQL 11.2 (for homework), Apache 2.4.27, Python 3.7.3, IPython 7.5.0, Spark 2.4.3 and R 3.5.2.

If you have access to an equivalent machine that has these packages, you may use it instead of the virtual machine image. However, please note that we cannot provide support for systems other than the virtual machine image, and that your project MUST be runnable on the provided virtual machine. We will be using the virtual machine image for grading purposes, and if your submission does not work within this setup, you may get zero points. We cannot make any exceptions to your project schedule for problems incurred by using your own computing facilities.










<h1>Project</h1>

Reddit (reddit.com) is a hybrid URL bookmark and/or news site, and a forum. Redditors post articles, links, or text on specific topics and other Redditors vote the submission up (meaning “like”) or down (meaning “don’t like”), and can also write comments in response to the submission. These comments can be nested very deeply in a submission.




Reddit is divided up into thousands of “subreddits” which are essentially forums dedicated to a particular topic.

Politics is the subject that everyone either loves, hates or loves to hate. But, it is also a very polarizing and emotional subject, so it provides a good basis for doing some machine learning. It is also the most active subreddit on Reddit, so there is a lot of data we can use. An election year is coming up, so we will use this Reddit data to find the sentiment across time, across topics, and across states regarding President Trump.  I do not know what results we will get. It may be that this data is useless, but we do not know until we try to use it!

<em><u>Caveat:</u></em>​ ​/r/politics, and Reddit in general, is known to bias heavily towards young (18-29, 59%) males (71%) that lean liberal / progressive / left (47% of overall users, but much higher ​<em>anecdotally</em> in /r/politics), so we are already starting with biased data, but still, let’s see what we can get from it.

<a href="https://pushshift.io/">Jason Baumgartner</a>​ has collected every Reddit submission and every Reddit comment posted on the site since 2005. This data is available on his website in ​bz2​ or ​xz​ format.

Your project is to parse the comments (Python or Scala), use what you have learned in 143 about joins etc. to massage the data into the proper format (Spark and/or SQL in Spark) for training a <em>sentiment classifier </em>​(Spark MLLib)​<em>. </em>​Then, generate a document containing your findings with plots and answers to some questions.




<h2>Part A: Text Parsing</h2>

In Part A, you will write a function, in Python to take horribly messy text from Reddit comments, and parse them into a smooth format that we can eventually use to train a classifier. <em>Due Date: </em>​Monday, May 20, 2019, 11:59pm




<h2>Part B: Transforming Data, Training and Evaluating a Classifier and</h2>

In this part, you will use the function you wrote for Part A to parse the text (if you didn’t already do it in Part A), into a data frame containing not only text, but several other features using Spark SQL. You will then train a classifier using a Spark package called mllib. You will then use this classifier to study the wider population on Reddit. You will then prepare a “mini-report” that has several plots and answers questions about the data.







Project 2 Part A

<h1>Partners</h1>

The CS143 project may be completed in teams of one or two students. The choice is up to each student. Partnership rules consist of the following:




<ul>

 <li>An identical amount of work is expected and the same grading scale is used regardless of the size of your team.</li>

 <li>If you work in a team of two, choose your partner carefully. Partners are permitted to “divorce” at any time during the course, and “single” student may choose to find a partner as the project progresses. However students from divorced teams may not form new teams or join other teams.</li>

 <li>Partners in a team will receive exactly the same grade for each project part submitted jointly.</li>

</ul>

If you have two students in your team, please make sure to submit your work jointly – do <em>not</em>​ ​ turn your project in twice, once for each partner.




<h1>Scope</h1>

The primary purpose of Part A is the following:




<ol>

 <li>To provide you with sample data you need to complete the project. (More to follow) 2. To make sure the VirtualBox image is working correctly to ensure your further success.</li>

 <li>Write a transformer that parses really messy Reddit comments into nice text we can use to train a classifier.</li>

</ol>




We provide you with a whole bunch of basic information to get everyone up-to-speed on our computing systems and the languages and tools we will be using. Those of you who have used a database server before (remember, we do not expect any familiarity), will find this part nearly trivial. Those of you who haven’t will find it mostly straightforward. With all that said, ​<em>please don’t start at the last minute</em>​ — as with all programming and systems work, everything takes a bit of time, and unforeseen snafus do crop up.
















<h1>System Setup</h1>

We will be using VirtualBox to run the Linux operating system in a virtual machine. VirtualBox allows a single machine to share resources and run multiple operating systems simultaneously. Read our VirtualBox setup instruction and follow the instructions to install VirtualBox and our virtual-machine image on your own machine.




The provided virtual machine image is based on Ubuntu 19.04, PostgreSQL 11.2, Python 3.7, R 3.4.5, Spark 2.4.3. You will need to use the provided VirtualBox guest OS to develop and test all projects for this class.




Your VirtualBox guest is essentially a Linux machine. Your guest is accessible from your host through secure shell (SSH) at ​localhost​ port ​<strong>1422</strong>​ with username ​cs143​ and password ​cs143​. There is a second port forward defined for port ​<strong>4040 </strong>​which will be used for Project 2B.




<strong>If you have any problems with the image, let the TAs know ASAP on Piazza. </strong>




<u>Remember, the goal of this project is to learn something timely and also to have some fun.</u>




There may be parts of the project that are vague. This usually means I am not particularly worried about certain nuances, or want you to struggle through it a bit, but do feel free to ask us on Piazza and I will clarify if I do have expectations.

<h2>Text Parsing</h2>

Most software engineers and data scientists focus a lot on working with numbers, structured data, and working with rather regular data (this is an understatement). Text mining (as well as other fields such as image processing, computer vision etc.) is becoming much more important as computer systems evolve and are able to process more and more data in more sophisticated ways. Knowing how to work with unstructured data is very important as a data scientist, or as a software engineer, particularly if you are interested in working in any kind of “data” space (i.e. data science, machine learning, whatever).




In Project 2A, you will write a function, in Python, that parses Reddit comments and takes them from raw messy text into a cleaner effluent that we can then use for analysis or training sentiment analysis model on.




This may sound daunting, but it isn’t.







<h2>The Great Beyond</h2>

I might regret saying this, but if you are adventurous, you may want to use other computing resources, such as a personal server, some UCLA server, that provides more resources than a VM, but the VM should work. We cannot provide technical support, but there are some ​<a href="https://medium.com/@josemarcialportilla/installing-scala-and-spark-on-ubuntu-5665ee4b62b1">great tutorials on</a> <a href="https://medium.com/@josemarcialportilla/installing-scala-and-spark-on-ubuntu-5665ee4b62b1">setting up Spark on Ubuntu</a><u>​</u><a href="https://medium.com/@josemarcialportilla/installing-scala-and-spark-on-ubuntu-5665ee4b62b1">.</a> Spark works well in local mode, but the real power comes on a powerful server, or a cluster..







<h1>The Data</h1>

The data you will use for 2B comes from ​<a href="https://www.reddit.com/r/politics">Reddit</a> <u>​</u><a href="https://www.reddit.com/r/politics">/r/politics</a>​ and covers submissions and comments from October 2016 (right before the election) to the latest data dump covering to February 2019. It also includes all comments and submissions made to other subreddits made by users that post to ​/r/politics​. This data can be used to detect highly partisan Reditors, bots (or possibly Russian interference as Reddit was used as a propaganda vehicle in addition to Facebook). I do not want to take over your entire hard drive, so I further limited the data to only comments between 50 and 100 words in length. For 2A, <u>​</u><a href="https://drive.google.com/file/d/17t2wumBvjgEut9LmLCjicCQOr8UVzOkU/view?usp=sharing">you will use a very small sample of the data in a file called</a> <a href="https://drive.google.com/file/d/17t2wumBvjgEut9LmLCjicCQOr8UVzOkU/view?usp=sharing">sample.json</a>​.




<ul>

 <li>comments-minimal.json.bz2​ contains comments in JSON format. See the appendix for a JSON schema.</li>

 <li>json.bz2​ contains submissions in JSON format. It has the following keys. Most of them are irrelevant and are related to, you guessed it, ad tracking. This list is not comprehensive since you will use submissions less than comments.</li>

</ul>

For advanced students, you will note that this data, if put into a table, is ​<em>not </em>​normalized. It has redundant data, particularly user data.




<h1>Investigating the Data</h1>

There is a sample data file for you to debug with ​<a href="https://drive.google.com/file/d/17t2wumBvjgEut9LmLCjicCQOr8UVzOkU/view?usp=sharing">here</a><u>​</u><a href="https://drive.google.com/file/d/17t2wumBvjgEut9LmLCjicCQOr8UVzOkU/view?usp=sharing">.</a>




You can then use your favorite Eggert UNIX tools to investigate the data… but wait… there’s more! You can install a tool called ​<a href="https://stedolan.github.io/jq/">jq</a>​ that is basically grep for JSON files!!!




<h1>The Actual Project 2A</h1>

Your first goal is to write a Python function called ​sanitize​ in a file called ​cleantext.py​ that takes a string as an argument, parses and tokenizes messy text into something standardized and returns a list containing four strings. These four strings are described later. ​<u>You may not use any</u> <u>libraries that are not part of the standard libraries: </u><u>​</u><u>re</u><u>​ is a standard library, but </u><u>​</u><u>nltk</u><u>​ is not because it</u> <u>must be installed.</u>




<em>Please use this </em><a href="https://drive.google.com/file/d/1eacs92rM_LKfi6VOwzvzr2RZzbRph44t/view?usp=sharing">​</a><a href="https://drive.google.com/file/d/1eacs92rM_LKfi6VOwzvzr2RZzbRph44t/view?usp=sharing"><em>template</em></a><a href="https://drive.google.com/file/d/1eacs92rM_LKfi6VOwzvzr2RZzbRph44t/view?usp=sharing">​</a> <em>for your coding. </em>

<em> </em>

I wrote a function to do this at Facebook, and I now use it for everything including my dissertation. Your job is to reproduce this similar function.




Your function <u>​must</u><u>​</u> do the following:




<ol>

 <li>Replace new lines and tab characters with a single space.</li>

 <li>Remove URLs. Replace them with what is inside the []. URLs typically look like ​[some text](http://www.ucla.edu)​ in the comment text but also have the standard form http(s)://…. Remove all URLs. ​<strong>The online tool may not match this. </strong></li>

 <li>(NEW!) Do the same with links to subreddits and users that are encoded like in #2 using Markup links. For raw references to subreddits and users (​/r/subredditname​ and /u/someuser​) leave them in the text as is, but it is OK if the first slash is removed by an earlier part of the script. ​<strong>The online tool may not match this. </strong></li>

 <li><strong>We will not use test cases that involve #2, 3 and will instead check manually since this was not clear. If your implementation is reasonable, you will not lose points. </strong></li>

 <li>Split text on a single space. If there are multiple contiguous spaces, you will need to remove empty tokens after doing the split.</li>

 <li>Separate all ​<em>external </em>​punctuation such as periods, commas, etc. into their own tokens (a token is a single piece of text with no spaces), but maintain punctuation ​<em>within </em>​words (otherwise ​he’ll​ gets parsed to ​hell​ and ​thirty-two​ gets parsed to ​thirtytwo)​ . The phrase “The lazy fox, jumps over the lazy dog.​ ​” should parse to “t​he lazy fox , jumps over the lazy dog .”​</li>

 <li>Remove all punctuation (including special characters that are not technically punctuation) <em>except</em>​ punctuation that ends a phrase or sentence and ​<em>except </em>​embedded punctuation (so thirty-two remains intact). Common punctuation for ending sentences are the period (.), exclamation point (!), question mark (?). Common punctuation for ending phrases are the comma (,), semicolon (;), colon (:). ​<em>While quotation marks and parentheses also start and end phrases, we will ignore them as it can get complicated. We can also ignore RRR’s favorite em-dash (–) as it varies (two hyphens, one hyphen, one dash, two dashes or an em-dash). </em></li>

 <li>Convert all text to lowercase.</li>

 <li>The order of these operations matters, but you are free to experiment and you ​<em>may</em>​ get the same results.</li>

 <li>Your function should return one data structure containing four collections: a string containing the parsed text, a string of all unigrams (single tokens) in any order separated by a space, a string of all bigrams (a pair of tokens in sequence contained within each phrase/sentence without bounding punctuation) separated by spaces with an underscore between words in the bigram, and a string of all trigrams (a triple of tokens in sequence contained within each phrase/sentence without bounding punctuation) separated by spaces with an underscore between words in the trigram.</li>

 <li>This is not as simple as it seems and you will see why.</li>

</ol>




Example Comment:

I’m afraid I can’t explain myself, sir. Because I am not myself, you see?




Parsed Comment (Returned String 1):

i’m afraid i can’t explain myself , sir . because i am not myself , you see ?

Unigrams (Returned String 2):

i’m afraid i can’t explain myself sir because i am not myself you see

Bigrams (Returned String 3):

i’m_afraid afraid_i i_can’t can’t_explain explain_myself because_i i_am

am_not not_myself you_see




Trigrams (Returned String 4):

i’m_afraid_i afraid_i_can’t i_can’t_explain can’t_explain_myself

because_i_am i_am_not am_not_myself




You will note that this function cannot be perfect. It takes a lot of finesse to write a good implementation. <u>We are not expecting perfection, but we do expect code that meets the spec.</u>​   Parsing (and optimization) is a never ending task, and learning ​<em>when to stop </em>​is a very good skill for any software engineer to learn: the law of diminishing returns.




When I parse text, I do the main steps. Then I sample a couple hundred rows, identify unresolved problems, and determine how many records are affected by those problems. At a certain point, problems only affect less &lt;1% of the data, and I stop (Project 2A will not be that thorough and that is OK).










You don’t necessarily need to use Spark for part 2A, though it is likely helpful in case there is some weird translation issue moving from raw code to Spark-run code.













Submission Instruction

<h1>Preparing Your Submission</h1>

Please create a folder named with your UID, put all your files into the folder, then compress this folder into a single zip file called “P2A.zip”. That is, the zip file should have the following structure.

P2A.zip

|

+- Folder named with Your UID, like “904200000” (without quotes)

|

+- readme.txt

|

+- team.txt

|

+- cleantext.py




Please note that the file names are case sensitive, so you should use the exact same cases for the file names. (For team work, only the submitter’s UID is needed to name the folder.) Here is more detailed description of each file to be included in the zip file:

<ul>

 <li>txt:​ Readme File</li>

 <li>txt:​ A plain-text file (no word or PDF, please) that contains the UID(s) of every member of your team. If you work alone, just write your UID (e.g. 904200000).</li>

</ul>

If you work with a partner or a group, write all UIDs separated by a comma (e.g. 904200000, 904200001). Do not include any other content in this file!

<ul>

 <li>py:​ The file containing your sanitize function.</li>

</ul>

<h1>Testing of Your Submission</h1>

Grading is a difficult and time-consuming process, and file naming and packaging convention is very important to test your submission without any error. In order to help you ensure the correct packaging of your submission, you can test your packaging by downloading this <u>​</u><a href="http://ryanrosar.io/teaching/ucla/18s/cs143/p2a_test">test script</a>​. In essence, this script unzips your submission to a temporary directory and tests whether or not you have included all your submission files. Once you download the test script, it can be executed like:




<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="d8bbabe9eceb98bbabe9eceb">[email protected]</a>:~$ ./p2a_test &lt;Your UID&gt;




(Put your P2A.zip file in the same directory with this test script, you may need to use “​chmod +x p2a_test​” if there is a permission error).




You MUST test your submission using the script before your final submission to minimize the chance of an unexpected error during grading. Significant points may be deducted if the grader encounters an error during grading. When everything runs properly, you will see an output similar to the following from this script:




Check File Successfully. Please upload your P2A.zip file to CCLE.




<h1>Appendix</h1>

This appendix contains schemas for the Reddit JSON data as of Spring 2018. These schemas may have slightly changed after that.

Schema for Comments

<table width="624">

 <tbody>

  <tr>

   <td width="208"><strong>Field Name </strong></td>

   <td width="208"><strong>Data Type </strong></td>

   <td width="208"><strong>Description </strong></td>

  </tr>

  <tr>

   <td width="208">id</td>

   <td width="208">String</td>

   <td width="208">Unique identifier for this comment.</td>

  </tr>

  <tr>

   <td width="208">author</td>

   <td width="208">String</td>

   <td width="208">The username of the author of the comment. To see infoabout a particular user, use theURLhttp://www.reddit.com/user/USERNAME</td>

  </tr>

  <tr>

   <td width="208">subreddit_id</td>

   <td width="208">String</td>

   <td width="208">Remember youtube_video id?subreddit_id is an alphanumeric code that uniquely identifies a subreddit. It is not the subreddit’s name.</td>

  </tr>

  <tr>

   <td width="208">Subreddit</td>

   <td width="208">String</td>

   <td width="208">The case-sensitive name of the subreddit. It looks like /r/politics</td>

  </tr>

  <tr>

   <td width="208">Stickied</td>

   <td width="208">Boolean</td>

   <td width="208">Is the comment stickied to the top of all comments? This is usually initiated by a moderator to keep discussions on track.</td>

  </tr>

  <tr>

   <td width="208">score</td>

   <td width="208">Integer</td>

   <td width="208">Represents some computation of upvotes and downvotes.</td>

  </tr>

 </tbody>

</table>




<table width="624">

 <tbody>

  <tr>

   <td width="208"> </td>

   <td width="208"> </td>

   <td width="208">This is the number that is seen as points on each comment.</td>

  </tr>

  <tr>

   <td width="208">retrieved_on</td>

   <td width="208">Timestamp</td>

   <td width="208">Ignore. The date/time thatMichael scraped this comment.</td>

  </tr>

  <tr>

   <td width="208">permalink</td>

   <td width="208">URL</td>

   <td width="208">Useful for debugging.Copypasta this link to see the original comment in all its glory.</td>

  </tr>

  <tr>

   <td width="208">parent_id</td>

   <td width="208">String</td>

   <td width="208">Alphanumeric code denoting the parent comment, if this is a reply. This key may be missing.</td>

  </tr>

  <tr>

   <td width="208">is_submitter</td>

   <td width="208">Boolean</td>

   <td width="208">Is this comment posted by the OP (original poster)?</td>

  </tr>

  <tr>

   <td width="208">gilded</td>

   <td width="208">Boolean</td>

   <td width="208">This comment was so good, or so useful, that another user “gilded” them with Reddit Gold. Reddit Gold is the ad-free version of Reddit. Gilding only lasts a certain period of time.</td>

  </tr>

  <tr>

   <td width="208">edited</td>

   <td width="208">Boolean</td>

   <td width="208"> </td>

  </tr>

  <tr>

   <td width="208">distinguished</td>

   <td width="208">Boolean</td>

   <td width="208">I don’t know what this is.</td>

  </tr>

  <tr>

   <td width="208">created_utc</td>

   <td width="208">Timestamp</td>

   <td width="208">The date/time the comment was posted by the user.</td>

  </tr>

  <tr>

   <td width="208">controversiality</td>

   <td width="208">Integer; 0/1</td>

   <td width="208">Whether or not the comment is controversial based on number of upvotes and downvotes. This is some ratio that is Reddit proprietary.</td>

  </tr>

  <tr>

   <td width="208">can_gild</td>

   <td width="208">Boolean</td>

   <td width="208">Whether or not the user that made the comment has the power to gild other Redditors.</td>

  </tr>

  <tr>

   <td width="208">body</td>

   <td width="208">String</td>

   <td width="208">The text.</td>

  </tr>

  <tr>

   <td width="208">link_id</td>

   <td width="208">String</td>

   <td width="208">Links a comment back to the submission it appears on.</td>

  </tr>

 </tbody>

</table>




<table width="624">

 <tbody>

  <tr>

   <td width="208">author_flair_text</td>

   <td width="208">String</td>

   <td width="208">This may be useful. When a user writes a comment, or posts a submission, they have theoption of adding a “flair” next to their username. Flair just represents something interesting about the user. In /r/politics​, it can be political affiliation, whichcandidate they support(ed). More importantly, many users add their STATE(i.e. California) as their flair. In ​/r/ucla​, it is typically the student’s major and graduation year. For alumni, it is typically the degrees earned (year optional).For example: ​”MathematicsB.S., Computer ScienceM.S., Statistics,Ph.D.” Or in /r/MTB it might the bike someone rides:i.e. “Specialized Stumpjumper FSR Comp6Fattie” </td>

  </tr>

  <tr>

   <td width="208">author_flair_css_class</td>

   <td width="208">String</td>

   <td width="208">Probably not useful. A name ofthe CSS class used to displaytheir flair. In /r/politics, it might be red or blue to denote party affiliation, but I have not seen it often.</td>

  </tr>

  <tr>

   <td width="208">author_cakeday</td>

   <td width="208">Boolean</td>

   <td width="208">I believe this represents whether or not the post date was the user’s “Reddit Birthday” sometimes called a “cake day” where a little icon of a cake may be</td>

  </tr>

  <tr>

   <td width="208"> </td>

   <td width="208"> </td>

   <td width="208">displayed.</td>

  </tr>

 </tbody>

</table>






















Schema for Submissions




<table width="624">

 <tbody>

  <tr>

   <td width="112"><strong>Field</strong></td>

   <td width="105"><strong>Datatype</strong></td>

   <td width="407"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="112">id</td>

   <td width="105">String</td>

   <td width="407">Unique identifier for a submission.</td>

  </tr>

  <tr>

   <td width="112">title</td>

   <td width="105">String</td>

   <td width="407">The title submitted by the submitter.</td>

  </tr>

  <tr>

   <td width="112">thumbnail</td>

   <td width="105">URL</td>

   <td width="407">Raw URL pointing to the submission’s thumbnail (if webpage or news article).</td>

  </tr>

  <tr>

   <td width="112">spoiler</td>

   <td width="105">Boolean</td>

   <td width="407">Used mainly for TV shows, but can also be used for election results.</td>

  </tr>

  <tr>

   <td width="112">subreddit_id</td>

   <td width="105">String</td>

   <td width="407">Same as with comments</td>

  </tr>

  <tr>

   <td width="112">subreddit</td>

   <td width="105">String</td>

   <td width="407"> Same as with comments.</td>

  </tr>

  <tr>

   <td width="112">stickied</td>

   <td width="105">Boolean</td>

   <td width="407">The submission is stuck to the top of the subreddit page.</td>

  </tr>

  <tr>

   <td width="112">selftext</td>

   <td width="105">String</td>

   <td width="407">The text of a post, if it is not a link or article. For example,/r/ucla is mostly selftext… people asking questions or jokes about Gene Block.</td>

  </tr>

  <tr>

   <td width="112">score</td>

   <td width="105">Integer</td>

   <td width="407">Same as with comments, but displayed next to the story.</td>

  </tr>

  <tr>

   <td width="112">pinned</td>

   <td width="105">Boolean</td>

   <td width="407">Similar to stickied.</td>

  </tr>

  <tr>

   <td width="112">permalink</td>

   <td width="105">URL</td>

   <td width="407">A permalink to the submission.</td>

  </tr>

  <tr>

   <td width="112">over18</td>

   <td width="105">Boolean</td>

   <td width="407">If this post is NSFW (not safe for work) and is for 18+ audience.</td>

  </tr>

  <tr>

   <td width="112">author</td>

   <td width="105">String</td>

   <td width="407">Same as with comments.</td>

  </tr>

  <tr>

   <td width="112">locked</td>

   <td width="105">Boolean</td>

   <td width="407">Very common in /r/politics. Once a thread becomes toxic, the entire discussion is usually locked so nobody can participate and it becomes read only.</td>

  </tr>

  <tr>

   <td width="112">num_comments</td>

   <td width="105">Integer</td>

   <td width="407">The number of comments.</td>

  </tr>

  <tr>

   <td width="112">user_info</td>

   <td width="105">A bunch.</td>

   <td width="407">The same data that was provided for comments.</td>

  </tr>

 </tbody>

</table>







Project 2B Specification

Computer Science 143 – Spring 2019

Project 2 Part B

<strong>Due Sunday, 06/02/2019 by 11:59pm </strong>

<strong> </strong>

<em>Please start early.  </em>

<strong> </strong>

<strong>Download the data: </strong><u>​</u><a href="https://s3.us-east-2.amazonaws.com/cs143-rosario/comments-minimal.json.bz2"><strong>file 1</strong></a><u>​</u><a href="https://s3.us-east-2.amazonaws.com/cs143-rosario/comments-minimal.json.bz2"><strong>,</strong></a> ​<a href="https://s3.us-east-2.amazonaws.com/cs143-rosario/submissions.json.bz2"><strong>file 2</strong></a><u>​</u><a href="https://s3.us-east-2.amazonaws.com/cs143-rosario/submissions.json.bz2"><strong>,</strong></a> <u>​</u><a href="https://s3.us-east-2.amazonaws.com/cs143-rosario/labeled_data.csv"><strong>file 3</strong></a>​<strong>. </strong>​These files are hosted on an AWS Educate account with promotional credits, so if the files become unavailable, please contact us immediately.

<h1>Preface</h1>

<ol>

 <li>This project is going to require a lot of Googling and StackOverflow work, which is an important skill to master. This simulates a project you may do outside of school. The only caveat is that if you ​<em>copy/paste</em>​ anything from StackOverflow etc, just cite it either in a comment, or in ​txt​. If you do your research correctly, you may find this project to be easily manageable. This is a skill that takes practice, so there is no better time to start than now.</li>

 <li>Unlike Project 1, Project 2 contains tasks and QUESTIONS. Please answer the questions in <u>your final deliverable report</u><u>​</u>.</li>

 <li>If you have access to a server and you wish to install Spark, you can use that, but we cannot provide support and your code must run in the VirtualBox image. If you have ​<strong>free </strong>​student credits on Amazon Web Services (AWS) or Google Cloud (GCP), you should feel free to use them, but again, we cannot provide support and your code must run on the VirtualBox image.</li>

</ol>




Project 2B consists of several tasks. These tasks are designed to keep you on track, and are how your professor approached the problem. You should try to stick to the tasks given in this specification. If you deviate, you may run into problems that then require you to backtrack and try another approach, so proceed with caution.




Now that we have warmed up by writing a text parsing function, we can now train a machine learning model that attempts to determine the sentiment of a particular Reddit Politics comment. But it is not that simple — (an em dash) we must first transform the data into a structure that allows us to train such a model. 95% of machine learning, data science, whatever, is cleaning data. It is crucial to get it right or we might get a bad model.​<em> For CS 143, we are not judging accuracy the accuracy/performance of the model. There are other classes for that. </em>




What is a Classifier?

A classifier is essentially a function ​<em>f</em>​ that maps a set of features ​<em>X</em>​ to a label ​<em>Y</em>​. A ​<em>feature</em>​ is some attribute that we believe will help us predict label ​<em>Y</em>​. We will use many kinds of features: unigrams, bigrams and trigrams. ​<em>Y</em>​, the label (sometimes called the target) is some measure of sentiment. It can be {-1, +1} to represent negative and positive respectively. It can also be a vector, where each element in the vector is a probability that the comment is positive, and the probability that the comment is negative. We will train two classifiers for each dimension (more on this in a bit): one for positive, and one for negative. Why? Positive and negative are not necessarily opposites. The opposite of positive is not positive and the opposite of negative is not negative. If they were in fact opposites, we would use one classifier. It is our hope that a comment is either positive/not negative, negative/not positive, not positive/not negative. ​<em>f</em>​ can take on many forms. It can be linear, or nonlinear. If our goal were to predict continuous values, the simplest model ​<em>f</em>​ is linear regression from Stats 10. In classification, the simplest linear model is called ​<a href="https://christophm.github.io/interpretable-ml-book/logistic.html"><em>logistic regression</em></a><a href="https://christophm.github.io/interpretable-ml-book/logistic.html">​</a><a href="https://christophm.github.io/interpretable-ml-book/logistic.html">.</a>




Some other forms of ​<em>f</em>​ include ​<a href="http://cs229.stanford.edu/notes/cs229-notes3.pdf">support vector machines</a>​ (SVM), ​<a href="https://www.stat.berkeley.edu/~breiman/RandomForests/cc_home.htm">random forests</a><u>​</u><a href="https://www.stat.berkeley.edu/~breiman/RandomForests/cc_home.htm">,</a> ​<a href="https://medium.com/machine-learning-101/chapter-1-supervised-learning-and-naive-bayes-classification-part-1-theory-8b9e361897d5">naive bayes</a>​ (based on Bayes rule and conditional probability) and <a href="https://www.deeplearningbook.org/">neural networks and the ever prescient “Dee</a><u>​  </u><a href="https://www.deeplearningbook.org/">p</a> <a href="https://www.deeplearningbook.org/">Learning.”</a>




Training a classifier is as simple as fitting a model to the data. But we have to be careful what data we use. We will eventually want to know how accurate our classifier is. At first, we can train the model using some part of the data, and then evaluate accuracy on the same part of data. This is called the ​<em>training accuracy</em>​, and gives us an indicator of whether or not we are even in the right ballpark of classifier choice. But we cannot rely on only the training accuracy. The sample of data on which we trained the classifier may not be representative of all of the data we may see. If we only use training accuracy, we may as well just have a classifier that memorizes the dataset. That is, the data do not form a random sample of all Reddit Politics comments.




Take this ridiculous extreme example. Suppose we train a model by simply memorizing the data and their associated sentiment labels. We can get 100% accuracy on this training set. But if we run unseen text through the classifier to make predictions, the accuracy will likely be terrible. So, we divide the data into two sets: a training set, and a testing set. We train, or fit, a model ​<em>f</em>​ on the training set. To measure accuracy, we then apply the classifier to the test set. Your professor tends to pick a 70/30 or 80/20 split on training and testing data. However, we do not have much labeled data, so we may take a different approach.




<h1>The Data</h1>

In 2018, your professor took a sample of 2,000 Reddit Politics comments and posted them to

<a href="https://www.mturk.com/">Mechanical Turk</a><u>​</u><a href="https://www.mturk.com/">,</a> a service where humans perform small human intelligence tasks for a small wage (10 cents is typical). In this task, the Turker read the comment, and then rated the sentiment of the comment (positive, negative, neutral, not applicable) on three dimensions:




<ol>

 <li>sentiment towards Democrats,</li>

 <li>sentiment towards President Trump,</li>

 <li>and sentiment towards Republicans.</li>

</ol>

This year, we will only use #2.







Each comment was shown to three different individuals, and the eventual “true” sentiment label for the comment was determined to be the most common response for each of the three dimensions. Unfortunately, Mechanical Turk generally yields very poor results unless the task specification is crystal clear, and the task is targeted to particular subpopulations.




The file <a href="https://s3.us-east-2.amazonaws.com/cs143-rosario/labeled_data.csv">labeled_data.cs</a>​       <a href="https://s3.us-east-2.amazonaws.com/cs143-rosario/labeled_data.csv">v</a> contains a comment_id and sentiment labels on three dimensions​    (Democrat, Republican, Trump specifically).




<ol>

 <li>-1 means negative</li>

 <li>1 means positive</li>

 <li>0 means neutral</li>

 <li>-99 means not applicable</li>

</ol>

We will only work with positive and negative labels.




<h2>Getting the Data Ready for Training and Testing a Model</h2>

We need to gather our features. The three sets of features are the unigrams, bigrams and trigrams you computed with the ​sanitize​ function. We will now use this function to add to a Spark DataFrame.




Loading a BZ2 file containing JSON objects into Spark is easy:




from pyspark.sql import SQLContext sqlContext = SQLContext(sc) sc.addPyFile(“cleantext.py”)

comments = sqlContext.read.json(“comments-minimal.json.bz2”) submissions = sqlContext.read.json(“submissions.json.bz2”)




What is with the ​addPyFile​ call? Spark is a distributed framework. It is most powerful running on a cluster such as Mesos or Yarn, but for this class we will run Spark locally. Still, Spark ​<em>may</em>​ use additional cores on your machine by forking separate processes. These other processes may be forked off somewhere else that cannot access your ​cleantext.py​. So, we tell Spark to add cleantext.py to a distributed cache, which is accessible to all nodes in the Spark cluster, even if it​    is local.




Data Management Tasks

You will want to read Spark documentation for these tasks:

<ol>

 <li><a href="https://spark.apache.org/docs/latest/sql-programming-guide.html">Spark SQL and Data Frames</a></li>

 <li><a href="https://docs.databricks.com/spark/latest/spark-sql/index.html">Spark SQL Guide (includes information about User Defined Functions)</a></li>

 <li><a href="https://spark.apache.org/sql/">Open Source Spark SQL Guide</a></li>

 <li><a href="https://spark.apache.org/docs/latest/ml-features.html">Extracting and Constructing Features</a>​ in Spark MLLib</li>

 <li>There are two ways to work with the relational model in Spark: 1) use Spark primitives such as ​join​, ​select​, 2) use SQL with the ​sql​ function.</li>

</ol>




<u>I M P O R T A N T</u><u>​</u>: All tasks must be completed in one Python file called ​reddit_model.py (underscore, not hyphen) and your main entry point must be accessible via the main​     ​ guard. <u>​</u><a href="http://blog.appliedinformaticsinc.com/how-to-write-spark-applications-in-python/">Click</a> <a href="http://blog.appliedinformaticsinc.com/how-to-write-spark-applications-in-python/">here for an example of some Python code.</a><u>​</u> ​<a href="https://gist.github.com/RyanRosario/7ef4eef7a1c780eb541a698180876938">Click here for the coding template</a>​.




<u>N O T E</u><u>​</u>: Spark also uses the word “tasks” to refer to a particular computation. The word “task” in this spec should not be confused with Spark’s definition.




<strong>TASK 1:</strong>​ Load the comments (BZ2 JSON), submissions (BZ2 JSON) and labeled data (CSV) into PySpark. This may take a while. To prevent having to wait 10 mins each time the data are loaded, you can write it to your shared directory as a ​<a href="https://parquet.apache.org/">parquet file</a><u>​</u><a href="https://parquet.apache.org/">.</a>




some_data_frame_name.write.parquet(“somefilename”)




and then load it quickly. You may need to import a library to get this to work though.




<strong>TASK 2: </strong>​To train a classifier, we only need to work with the labeled data, but ​labeled_data.csv ONLY contains a ​comment_id​, and 3 sentiment labels. The comments file contains the actual comments and a bunch of other information. We need to do something with these two data frames so we only have data associated with the labeled data.




<strong>QUESTION 1:</strong>​ Take a look at ​labeled_data.csv​. Write the functional dependencies ​<strong>implied</strong>​ by the data.




<strong>QUESTION 2:</strong> Take a look at the schema for comments. Forget BCNF and 3NF. Does the data​            frame <em>look</em>​ ​ normalized? In other words, is the data frame free of redundancies that might affect insert/update integrity? If not, how would we decompose it? Why do you believe the collector of the data stored it in this way?




<strong><span style="text-decoration: line-through;">TASK 3:</span></strong><span style="text-decoration: line-through;">​ We also need to add in features that denote which subreddits each user contributes to</span> <span style="text-decoration: line-through;">either via comment or via submission. We have this information in both BZ2 files.</span> We are only using​       text features this quarter.




<strong>TASK 4: </strong>​Generate the unigrams, bigrams and trigrams for each comment in the labeled data and store all of them combined into one column. You have already written this function in project 2A, but we cannot just call it like we would for other Python code. You will need to write a UDF (user defined function) — a special function that Spark understands.




<strong>TASK 5:</strong> To train a model, we must have all features in one column, as an array of strings. Combine​  the unigrams, bigrams, trigrams ​<span style="text-decoration: line-through;">and participating subreddits</span><span style="text-decoration: line-through;">​</span> into the same column. You may need to write a UDF for this.




That is, your sanitize function returns something like the following:

[‘a string of unigrams’, ‘a string of bigrams’, ‘a string of trigrams’]

We want the following representation instead:

[‘a’, ‘string’, ‘of’, ‘unigrams’, ‘a’, ‘string’, ‘of’, ‘bigrams’, ‘a’,

‘string’, ‘of’, ‘trigrams’]




You can either modify your sanitize function, or call your function as is and reorganize the return value so it matches the above.




For this task, you will want to review the Spark documentation for ​CountVectorizer​.




<strong>TASK 6A</strong>​: Use a binary ​CountVectorizer​ to turn the raw features into a sparse feature vector, a data structure that Spark ML understands. Only use tokens that appear more than 10 times across the entire dataset (the ​minDf​ parameter). A feature vector is a standardized way of representing which features are in a particular observation. Each feature may have a value associated with it such as a count or a TF-IDF value. For our purposes, it is just 0/1 (absent/present). Since the representation is sparse, you will only see 1s (as well as a bunch of integers that index tokens in the vocabulary). Taking advantage of sparseness is a great way to preserve RAM.




<strong>TASK 6B:</strong> Create two new columns representing the positive and negative labels. Take the original​    labels {1, 0, -1, -99} and do the following. Construct a column for the positive label that is 1 when the original label is 1, and 0 everywhere else. Construct a column for the negative label that is 1 when the original label is -1 and 0 everywhere else.




Machine learning requires a TON of data management, so careers in these fields (or data science, whatever) requires strong understanding of relational databases, whether you use SQL in Spark, or Spark natives.




<h1>Model Fitting Tasks</h1>

Now it is time to fit a model! Since this is a Databases class and not a Machine Learning class, we will focus more on Spark and working “big data” (though this is far from big data on a VM… but the principle remains the same if we use a cluster with TBs of data). We will use a model called Logistic Regression, which is similar to Linear Regression you learned in Stats 10.




In linear regression we have,










where the left hand side just represents an average prediction of ​<em>y</em>​ given data ​<em>x</em>​. In logistic regression, we have










where the left-hand side is called the ​<em>logit</em>​. Given data ​<em>x, </em>​we can predict the probability that​<em> y = </em>​1 (if ​<em>y </em>represents positivity, then ​<em>y = 1</em>​ means positive, but if ​<em>y </em>​represents negative sentiment, then y = 1 means negative), as













where the betas are estimated using some optimization algorithm such as ​<a href="https://web.stanford.edu/class/archive/cs/cs109/cs109.1178/lectureHandouts/220-logistic-regression.pdf">maximum likelihood</a> <a href="https://web.stanford.edu/class/archive/cs/cs109/cs109.1178/lectureHandouts/220-logistic-regression.pdf">estimation</a><u>​</u><a href="https://web.stanford.edu/class/archive/cs/cs109/cs109.1178/lectureHandouts/220-logistic-regression.pdf">,</a> ​<a href="https://www.stat.cmu.edu/~cshalizi/350/lectures/26/lecture-26.pdf">Newton-Raphson Method</a>​, or <u>​</u><a href="https://courses.cs.washington.edu/courses/cse547/16sp/slides/logistic-SGD.pdf">Stochastic Gradient Descent</a><u>​</u><a href="https://courses.cs.washington.edu/courses/cse547/16sp/slides/logistic-SGD.pdf">,</a> and <em>x </em>​ ​is the data.




<strong>TASK 7:</strong>​ Train a logistic regression model on the features (unigrams, bigrams and trigrams). Instead of dividing the data into a training and testing set, we will use a method called ​<em>k </em>​fold cross-validation.










With ​<a href="https://en.wikipedia.org/wiki/Cross-validation_(statistics)#k-fold_cross-validation"><em>k </em></a><a href="https://en.wikipedia.org/wiki/Cross-validation_(statistics)#k-fold_cross-validation">​</a><a href="https://en.wikipedia.org/wiki/Cross-validation_(statistics)#k-fold_cross-validation">fold cross-validation</a>​, we divide the data into ​<em>k </em>​non-overlapping parts. At each iteration, we pick one of the parts (folds) to use as the testing set (20% for 5 folds) and we use the rest (80% for 5 folds) to train the model. In the next iteration, we choose a new testing fold, and so on. This yields ​<em>k </em>models, and ​<em>k </em>​sets of accuracy metrics. The “overall” accuracy or performance of a model is usually the ​<em>average </em>​performance across the ​<em>k</em>​ iterations.










We typically use ​<em>k </em>​fold cross-validation when we are not working with a lot of training data (our case here), or when we have reason to suspect that a simple train/test split will yield biased results.

Since this is not a machine learning class, you can use the following code to train the positive and negative models for Trump.




<strong>You will want to walk to the farthest away Starbucks to get a cup of coffee, because this process may take a while. </strong>




# Bunch of imports (may need more)

from pyspark.ml.classification import LogisticRegression from pyspark.ml.tuning import CrossValidator, ParamGridBuilder from pyspark.ml.evaluation import BinaryClassificationEvaluator




# Initialize two logistic regression models.

# Replace labelCol with the column containing the label, and featuresCol with the column containing the features. poslr = LogisticRegression(labelCol=”poslabel”, featuresCol=”features”, maxIter=10)

neglr = LogisticRegression(labelCol=”neglabel”, featuresCol=”features”, maxIter=10)

# This is a binary classifier so we need an evaluator that knows how to deal with binary classifiers. posEvaluator = BinaryClassificationEvaluator() negEvaluator = BinaryClassificationEvaluator()

# There are a few parameters associated with logistic regression. We do not know what they are a priori.

# We do a grid search to find the best parameters. We can replace [1.0] with a list of values to try.

# We will assume the parameter is 1.0. Grid search takes forever.

posParamGrid = ParamGridBuilder().addGrid(poslr.regParam, [1.0]).build() negParamGrid = ParamGridBuilder().addGrid(neglr.regParam, [1.0]).build()

# We initialize a 5 fold cross-validation pipeline. posCrossval = CrossValidator(     estimator=poslr,     evaluator=posEvaluator,     estimatorParamMaps=posParamGrid,     numFolds=5) negCrossval = CrossValidator(     estimator=neglr,     evaluator=negEvaluator,     estimatorParamMaps=negParamGrid,     numFolds=5)

# Although crossvalidation creates its own train/test sets for # tuning, we still need a labeled test set, because it is not

# accessible from the crossvalidator (argh!)

# Split the data 50/50

posTrain, posTest = pos.randomSplit([0.5, 0.5]) negTrain, negTest = neg.randomSplit([0.5, 0.5])

# Train the models

print(“Training positive classifier…”) posModel = posCrossval.fit(posTrain) print(“Training negative classifier…”) negModel = negCrossval.fit(negTrain)




# Once we train the models, we don’t want to do it again. We can save the models and load them again later. posModel.save(“project2/pos.model”) negModel.save(“project2/neg.model”)




<em>You may find a better way to write this code, but this is a quick template to get you going. </em>




For those that care about machine learning: The grid search attempts to find the best regularization parameter. We won’t worry about what that means, but for those that care: to figure out the values for the betas, we must minimize the classification error as described by a ​<em>loss function</em>​.  This is similar to an objective function as taught in CS 161. For logistic regression, the loss function is the logistic loss. But many times, just minimizing the loss is not enough. We sometimes also want to penalize models that have too much features (as we do here), or constrain wildly large weights. Left alone, these models are overly complex and tend to not generalize well to new data. We can choose to penalize overly complex models by increasing their loss using a regularization term represented by lambda.










where y​(i) represents a true value for y (0 or 1) and h(x​ ​(i))​ is the predicted value of y, given data x, and theta is just beta for this model. Lambda is the regularization parameter and ​<em>m </em>​is the number of data points. Ok, enough of that…




<h1>Model Evaluation Task</h1>




<strong>CAUTION!</strong>​ In these tasks, you need to be very, very careful how you set up your joins. Remember what we learned in Chapter 12. You may also need to read documentation about how joins are implemented in Spark. If you receive ​OutOfMemoryError​, it means you did not structure your join correctly with respect to Spark. When you take advantage of the features of a package like Spark, it is amazing how much data you can work with on a limited system. <u>​Hint</u>​: Check the ordering of a sample of contiguous rows. You can manually simulate a merge join, and Spark has a way of doing an indexed join. Or is there something even simpler we can do?

<strong> </strong>

<strong>IF AFTER YOU’VE TRIED EVERYTHING, YOU STILL GET OUTOFMEMORY ERRORS, USE A </strong>

<strong>SAMPLE OF THE DATAFRAME, TRY 50% AND IF THAT DOESN’T WORK, USE 20% FROM </strong>

<strong>THIS POINT ON</strong>​. Write in your ​README.txt​ what you did.




<strong> </strong>

<strong> </strong>

<strong>Task 8:</strong>​ You will now read in the full file ​comments-minimal.json.bz2​. For the final deliverable, we are going to need a few more things:




<ol>

 <li>The timestamp when the comment was created.</li>

 <li>The title of the submission (post) that the comment was made on.</li>

 <li>The state that the commenter is from.</li>

</ol>

#2 can be computed with a join on ​link_id​ (comments) and ​id​ (submissions). But what about #3?

Look again at the schema in the Project 2A Specification. There is a field called author_flair_text​ that sometimes contains the name of a state that the commenter votes in. You can use this as the State.




A special note on link_id: ​<u>the first three characters represent the type of link and looks like “</u><u>​</u><u>t3_</u><u>​”.</u> <u>This must be stripped off or your join will be the empty set.</u>




You may want to restrict your data frame to only these columns, the comment ID, and the comment text to save space.




<strong>Task 9:</strong>​ Run your classifiers on this text. ​<u>You will need to repeat Tasks 4, 5 and 6A (except with the</u> <u>CountVectorizer. Once you fit the CountVectorizer you don’t need to fit it again. Use the transform</u> <u>method to apply the CountVectorizer to the unseen data) so that the format of the new unseen data</u> <u>is identical to the format of the training data with a few exceptions: (1) remove any comments that</u> <u>contain “/s” (denoting that the comment is sarcastic… machine learning does not deal with sarcasm</u> <u>well, and (2) remove any comments that start with &amp;gt; this means the comment contains a quote of</u> <u>another comment and likely contains multiple sentiments not just one.</u>​ This will give you the probability that the comment is positive sentiment and a probability that the comment is negative sentiment. Then, we must threshold these probabilities to convert them into 0/1 indicating if the comment is positive sentiment and if the comment is negative sentiment (probabilities are not intuitive to work with). ​<u>If the positive probability is greater than 0.2, label it the positive sentiment a 1.</u> <u>If the negative probability is greater than 0.25, label the negative sentiment as 1. </u> These values were​               derived from the ROC curve, which is a visual diagnostic of how accurate a classifier is. While most may assume that the probabilities should be greater than 0.5 (a coin flip), this data is imbalanced, that is, the number of positive labeled comments is not the same as the number of negative labeled comments. Instead, we use this proportion as the cutoff, to represent a result that is obtained solely by chance, but enough of that. ​<strong>You are free to pick your own cutoff, but this typically requires looking at the ROC curve (or doing a grid search over all possible cutoffs). </strong>




Construct two new columns “pos” and “neg” that contain 0 or 1 based on the thresholding. It is possible that a comment has a 0 for both, or a 1 for both. So don’t worry about that.




Below is an example of how to apply the classifier to unseen data to get predicted probabilities. You will then convert these probabilities to 0/1. You may have to play with this:




posResult = posModel.transform(dataframe_task9) negResult = negModel.transform(dataframe_task9) This will give you three new columns in posResult and negResult. One of them is called probability ​and is a vector of doubles and index 1 is the probability that a comment is positive in the positive result, and negative in the negative result. You will convert this value to 0/1 based on the thresholds I gave above. There is also ​rawPrediction​ and  ​prediction​.  Unfortunately, it is not clear what threshold these predictions use so we will ignore them. Unless you used setThreshold, then it is based on that threshold. You can either manually convert the probabilities into labels, or you can add use ​setThreshold()​ on the​ LogisticRegression ​object .




<strong>Task 10:</strong>​ Perform the following computations:




<ol>

 <li>Compute the percentage of comments that were positive and the percentage of comments that were negative across all submissions/posts. You will want to do this in Spark.</li>

 <li>Compute the percentage of comments that were positive and the percentage of comments that were negative across all days. Check out from ​from_unixtime​</li>

 <li>Compute the percentage of comments that were positive and the percentage of comments that were negative across all states. There is a Python list of <a href="https://gist.github.com/RyanRosario/856d6864b443fd71a984980d07b6b507">US States her</a>​ <a href="https://gist.github.com/RyanRosario/856d6864b443fd71a984980d07b6b507">e</a><a href="https://gist.github.com/RyanRosario/856d6864b443fd71a984980d07b6b507">.</a><u>​</u> Just copy and paste it.</li>

 <li>Compute the percentage of comments that were positive and the percentage of comments that were negative by comment and story score, independently. You will want to be careful about quotes. Check out the ​quoteAll​</li>

</ol>

Store your results in dataframes and write them to disk.




<h1>Final Deliverable</h1>

This final deliverable will be a mini-report of your findings. You will take the data frames you wrote to disk (CSV, tab delimited, whatever makes sense) and import them either into Python (or R) and create a few plots for us. R and Python are not necessarily memory efficient, so we suggest sampling the final data frame (if you haven’t already), and loading that sampled data frame into R or Python instead.




Since Spark is a distributed system that partitions data onto different nodes (in a cluster at least), writing a single CSV file is not trivial. But we can use a special driver to do it, by first repartitioning the data to only contain one partition. This will create a directory containing one CSV file (and a file called _SUCCESS).




myCoolDataFrame.repartition(1).write.format(“com.databricks.spark.csv”).op tion(“header”, “true”).save(“myCoolData.csv”)




Then produce the following in your​ report.pdf. <u>​</u><a href="https://gist.github.com/RyanRosario/4c1e12819d0406237b1c4834bb5be5d1">If you like R, use this code to generate the plots.</a> It may need to be modified for your data files. <u>​</u><a href="https://gist.github.com/RyanRosario/2eb299b5fffc3b22bdcc45d77a4e6f9b">If you prefer Python, use this example code for the</a> <a href="https://gist.github.com/RyanRosario/2eb299b5fffc3b22bdcc45d77a4e6f9b">plots.</a> This code may need to be adapted for use with this year’s course offering.​

<a href="https://gist.github.com/RyanRosario/2eb299b5fffc3b22bdcc45d77a4e6f9b"> </a>

<ol>

 <li>Create a time series plot (by day) of positive and negative sentiment. This plot should contain two lines, one for positive and one for negative. It must have data as an X axis and the percentage of comments classified as each sentiment on the Y axis.</li>

 <li>Create 2 maps of the United States: one for positive sentiment and one for negative sentiment. Color the states by the percentage.</li>

 <li>Create a third map of the United States that computes the​<em> difference: </em>​%Positive – %Negative.</li>

 <li>Give a list of the top 10 positive stories (have the highest percentage of positive comments) and the top 10 negative stories (have the highest percentage of negative comments). ​<u>This is</u> <u>easier to do in Spark.</u></li>

 <li>Create TWO scatterplots where the X axis is the submission score, and a second where the X axis is the comment score, and the Y access is the percentage positive and negative. Use two different colors for positive and negative. This allows us to determine if submission score, or comment score can be used as a feature.</li>

 <li>Write a paragraph summarizing your findings. What does /r/politics think about President Trump? Does this vary by state? Over time? By story/submission?</li>

</ol>

You must also answer the following questions in your report:




<strong>QUESTION 1</strong>​: Take a look at ​labeled_data.csv​. Write the functional dependencies implied by the data.




<strong>QUESTION 2: </strong>​Take a look at the schema for the comments dataframe. Forget BCNF and 3NF. Does the data frame ​<em>look</em>​ normalized? In other words, is the data frame free of redundancies that might affect insert/update integrity? If not, how would we decompose it? Why do you believe the collector of the data stored it in this way?




<strong>QUESTION 3:</strong>​ Pick one of the joins that you executed for this project. Rerun the join with .explain()​ attached to it. Include the output. What do you notice? Explain what Spark SQL is doing during the join. Which join algorithm does Spark seem to be using?




We will be grading your code and execution, so not only is copying someone else’s images/results prohibited, it won’t work.




How Accurate is Accurate?

Since this is not a machine learning class, our main focus is ob data management and using the relational model (originally from JSON) rather than training a theoretically correct and accurate classifier, which is why I gave you the code. But, if you’re curious, R​3 got an AUC of 0.73 for the​ positive classifier and 0.76 for the negative classifier. In academia, these scores as so-so, but in real life, this is considered “fairly good.”Professor was pleasantly impressed that such messy data, and such messy labels (Mechanical Turk is not usually reliable) produced such a good result.

Can you do even better? If so, let us know in your final deliverable report and describe what you did!










Submission Instructions

<h2>Preparing Your Submission</h2>

This project contained multiple TASKS. Please clearly denote each task using the following comment style. Your comment MUST match the style below. This tells us which tasks you completed.




# TASK 1

# Code for task 1…




Use this style ​<em>only </em>​if you had to combine code for multiple tasks. Do not simply write one comment that mentions all tasks!




# TASKS 6A, 6B

# Code for tasks 6A and 6B




Please create a folder named with your UID, put all your files into the folder, then compress this folder into a single zip file called “P2B.zip”. That is, the zip file should have the following structure.

P2B.zip

|

+- Folder named with Your UID, like “904200000” (without quotes)

|

+- README.txt

|

+- team.txt

|

+- reddit_model.py

|

+- cleantext.py (p2a)

|

+- analysis.R or analysis.py

|

+- report.pdf (final deliverable, answers to our questions)




Please note that the file names are case sensitive, so you should use the exact same cases for the file names. (For teamwork, only the submitter’s UID is needed to name the folder.) Here is more detailed description of each file to be included in the zip file:

<ul>

 <li>txt:​ Readme File mentioning anything necessary.</li>

 <li>txt:​ A plain-text file (no word or PDF, please) that contains the UID(s) of every member of your team. If you work alone, just write your UID (e.g. 904200000).</li>

</ul>

If you work with a partner or a group, write all UIDs separated by a comma (e.g. 904200000, 904200001). Do not include any other content in this file!

<ul>

 <li>py<sup>:</sup>​ The file containing your Spark job.</li>

 <li>R ​or ​analysis.py​: File containing code for your graphics (we don’t need the data itself).</li>

 <li>pdf​: Your report, answers to our questions, etc.</li>

</ul>

<h2>Submitting Your Zip File</h2>

Visit the Project 2B submission page on CCLE to submit your zip file electronically by the deadline. Submit only the “P2B.zip” file! In order to accommodate the last minute snafu during submission, you will have 30-minute window after the deadline to finish your submission process. That is, as long as you start your submission before the deadline and complete within 30 minutes after the deadline, we won’t deduct your grade period without any penalty.




<h2>Real Life Lessons</h2>

This project is similar to one you might pursue if you were to be a data engineer or data scientist, but there are a lot of real-life lessons that you hopefully learned from doing this project that are highly applicable to software engineering:




<ol>

 <li>It is important to save intermediate results. Data can take a while to load, and having to reload it several times a day is inefficient. Instead, save it in an efficient format (we used Parquet here) so it is easier to load back. This trick also allows you to begin development where you left off instead of at the beginning.</li>

 <li>The power of sampling. Developing a minimum working example is an important skill. During development, the same is true. Instead of loading a 10TB file, and running your code on the 10TB file every single time you change something, use a small 1MB file until you are nearly certain it works properly. ​<em>This will save you hours or days of time</em>​.</li>

 <li>Set parameters as low as possible. In my model, I used a 10 fold cross validation. This took forever. While writing my code, I use a 2 fold cross validation, which yielded about a 5x speedup. Each time I failed, I only wasted 1 unit of time instead of 5 units of time.</li>

 <li>The world is vague. Sometimes you just need to experiment with different methods to find a method that works. Books and your manager/professor won’t always have the answer for you.</li>

 <li>Learn how to read documentation and find information quickly. Reading documentation is important, but perhaps even more important is to be able to Google for answers to your questions ​<em>and identify the salient points quickly</em>​. ​<em>That is exactly how I did this project and it is expected in industry… nobody knows everything. </em>​In an academic environment, we ask you to cite any sources you use though just because it’s what we do.</li>

 <li>You have trained your first machine learning classifier. Some of you have already done this before, but I do not expect anyone to have done it before. If this was your first time, congratulations! I hope you continue.</li>

 <li>Visualization is an easy way to communicate findings whether findings from data, or simplifying a complex concept to a non-technical or brand new audience.</li>

 <li>The conclusions made in academia and in industry are different. Academia is based on theory, which usually yields the “best case scenario.” We are taught that AUCs, accuracies, whatever must be as high as possible. ​<em>But this is not practical.</em>​ It is often the case that results that academia deems as “meh” are actually quite good for industry because contexts are much more complicated than they are in some toy example.</li>

 <li>Fail fast, so the rollback is less painful. Creating an ETL job or a regular software program can be visualized either as a linear process, or a tree-like process. The farther down the line (or down the tree) you get, the more difficult it is to fix issues earlier on in the process. Once you fix an issue, you may then have to fix the code after it so it is compatible with your bugfix. Failing early takes a lot of experience. You should experiment with one feature or operation at a time. You will eventually get good at understanding if what you are implementing is sound, or if it was just a patch job that will break farther down the line. This is part of good software design. If you fail early, all you need to do is rollback the one thing that failed, fix it, and then move along on your merry way. If you fail late, you may not only have to fix one operation in question, but several operations/assumptions that came before it. Writing unit tests for each operation will prevent you from making changes that will break later down the line.</li>

</ol>

(Good unit tests can usually save you from 2, 3, and 9.)


