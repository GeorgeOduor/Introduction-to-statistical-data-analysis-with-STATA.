
<body>
<h1>Introduction to Data analysis with stata.</h1>

<p>Stata is a powerfull statistical analysis program.It is used in a wide range of areas and offers seamless data analysis environment.In this module you are going to learn basic things you can do to get started quickly.</p>
<h4>Contents of this Kernel</h4>
<div class="toc">
<ul>
<li><a href="#h-1"><span class="toc-secnum">1&nbsp;</span> Setting up a working directory.</a>
</li>
<li><a href="#h-2"><span class="toc-secnum">2&nbsp;</span> Creating a log file.</a>
</li>
<li><a href="#h-3"><span class="toc-secnum">3&nbsp;</span> Creating a do file.</a>
</li>
<li><a href="#h-4"><span class="toc-secnum">4&nbsp;</span> Reading Data in STATA.</a>
<ul>
<li><a href="#h-4-1"><span class="toc-secnum">4.1&nbsp;</span> STATA datasets</a>
</li>
<li><a href="#h-4-2"><span class="toc-secnum">4.2&nbsp;</span> Other Data sets</a>
<ul>
<li><a href="#h-4-2-1"><span class="toc-secnum">4.2.1&nbsp;</span> CSV files</a>
</li>
<li><a href="#h-4-2-2"><span class="toc-secnum">4.2.2&nbsp;</span> Excel Files.</a>
</li>
<li><a href="#h-4-2-3"><span class="toc-secnum">4.2.3&nbsp;</span> Other file types.</a>
</li>
</ul>
</li>
</ul>
</li>
<li><a href="#h-5"><span class="toc-secnum">5&nbsp;</span> Saving Stata Files</a>
</li>
<li><a href="#h-6"><span class="toc-secnum">6&nbsp;</span> Saving Stata Files-Other Formats.</a>
</li>
<li><a href="#h-7"><span class="toc-secnum">7&nbsp;</span> Built in Datasets.</a>
</li>
<li><a href="#h-8"><span class="toc-secnum">8&nbsp;</span> Conclusion</a>
</li>
</ul>
</div>
<h2 id="h-1"><span class="heading-secnum">1&nbsp;</span> Setting up a working directory.</h2>

<p>Working directory is very important since it will enable you to easily manage your work flow.</p>

<p>Below is a simple code that can be used for checking and setting up a working directory.</p>
<div style="position:relative"><pre id="stlog-1" class="stlog"><samp><span class="stinp">. <span class="stcmt">//checking a working dir</span></span>
<span class="stinp">. pwd</span>
<span class="stres">C:\Users\RuralNet011\Documents\MAY\stataClass\tutorials\introduction</span>

<span class="stinp">. <span class="stcmt">//setting up a working dir</span></span>
<span class="stinp">. cd C:\Users\RuralNet011\Documents\MAY\stataClass\tutorials\introduction</span>
<span class="stres">C:\Users\RuralNet011\Documents\MAY\stataClass\tutorials\introduction</span>
</samp></pre><a href="" target="_blank" class="btn btn-default btn-sm" style="position:absolute; top:10px; right:10px">Code</a></div>
<h2 id="h-2"><span class="heading-secnum">2&nbsp;</span> Creating a log file.</h2>

Stata logfiles record everything you do with stata in the background.Logfiles can be opende by any text editor application or word processor.They come in handy when you want to refer back to your steps.

<p>Lets see how this is done.</p>

<pre>
log using intro,text replace
</pre>

<p>By running the above code if we go to our working directory we will find <strong>intro.log</strong> file.</p>

<p>You can also append content to an existing log file by simply  adding <code>append</code> suboption to the above code as shown below.</p>

<pre>
log using mylog.log, append
</pre>

<p>To close the log file simpry use,</p>
 <pre>log close</pre>

 <h2 id="h-3"><span class="heading-secnum">3&nbsp;</span> Creating a do file.</h2>

 <p>Like an IDE in other languages,do files make your work reproducible.Do files store your codes and you can run them anytime and share them with others.</p>

 <p>To create a do file in stata ,its simple,just run the code below.</p>

 <pre>doedit</pre>

<p>This will open up a do file editor window where you can start typing your codes.Later you can save this file with your prefered name.</p>

<h2 id="h-4"><span class="heading-secnum">4&nbsp;</span> Reading Data in STATA.</h2>

<h3 id="h-4-1"><span class="heading-secnum">4.1&nbsp;</span> STATA datasets</h3>

<p>STATA unlike other packages like R and Python allows only one dataset to be loaded at a given time.</p>

<p>To read a Stata file a Stata working environment ,you can use the following comand.</p>
<div style="position:relative"><pre id="stlog-2" class="stlog"><samp><span class="stinp">. use trees.dta,clear</span>
</samp></pre><a href="" target="_blank" class="btn btn-default btn-sm" style="position:absolute; top:10px; right:10px">Code</a></div>
<p>The above code applies if the data is located in the same working directory as the one your do file is in.If otherwise ,the you will have to specify the corect file path.</p>

<p>The <code>clear</code> comand is used to clear the stata memory of any other dataset in the current working space.This essential since Stata will only work with one dataset at a time.</p>

<h3 id="h-4-2"><span class="heading-secnum">4.2&nbsp;</span> Other Data sets</h3>

<p>STATA supports other datasets as well and it will be possible to load them into the working space.This can be done through a series of steps in the UI and also in the command line as shown below.</p>

 <h4 id="h-4-2-1"><span class="heading-secnum">4.2.1&nbsp;</span> CSV files</h4>

 <P>Comma Separated values can be loaded into STATA by simply specifying he delimiter and how to treat the first row.</P>
<div style="position:relative"><pre id="stlog-3" class="stlog"><samp><span class="stinp">. import delimited mydata.csv, clear </span>
(128 vars, 395 obs)
</samp></pre><a href="" target="_blank" class="btn btn-default btn-sm" style="position:absolute; top:10px; right:10px">Code</a></div>
<p>In the above code example ,"mydata.csv" is imported into the work space and the existing file in the memory has been cleared by specifying the clear comand.The <code>import</code> and <code>delimited</code> key words are specified to tell Stata that we are now importing an external file type.</p>

<h4 id="h-4-2-2"><span class="heading-secnum">4.2.2&nbsp;</span> Excel Files.</h4>
<div style="position:relative"><pre id="stlog-4" class="stlog"><samp><span class="stinp">. import excel "mydata2.xlsx", sheet("mydata") firstrow clear</span>
</samp></pre><a href="" target="_blank" class="btn btn-default btn-sm" style="position:absolute; top:10px; right:10px">Code</a></div>
<p>In the above example ,<code>sheet</code> and <code>firstrow</code> keywords are specified to tell stata the sheet of the excel workbook to import and how to treet the workbook respectively.</p>


<h4 id="h-4-2-3"><span class="heading-secnum">4.2.3&nbsp;</span> Other file types.</h4>

<p>STATA offers an excelent ui for importing other file types which can be applied in case of a need to import other file types.
</p>

<p>In case of need one can just pull open -> import from the main menu then chose the correct data type. </p>

<h2 id="h-5"><span class="heading-secnum">5&nbsp;</span> Saving Stata Files</h2>

<p>Sometimes after modifying the data , you might need to save your data.To do this you will run the lines below in the comand line.The line will save the current data in the memory.<CODE>replace</CODE> comand can be specified to replace an existing file in the directory with the same name.</p>

<p>Also note that the saved file will be in a STATA format.</p>
<div style="position:relative"><pre id="stlog-5" class="stlog"><samp><span class="stinp">. save mydata3,replace</span>
file mydata3.dta saved
</samp></pre><a href="" target="_blank" class="btn btn-default btn-sm" style="position:absolute; top:10px; right:10px">Code</a></div>
<h2 id="h-6"><span class="heading-secnum">6&nbsp;</span> Saving Stata Files-Other Formats.</h2>

<p>Saving can also be done as other formats.In stata this is called Exporting.</p>

<p>Lets take a look at how you can do this.</p>
<div style="position:relative"><pre id="stlog-6" class="stlog"><samp><span class="stinp">. export delimited using "mydata4", replace</span>
file mydata4.csv saved
</samp></pre><a href="" target="_blank" class="btn btn-default btn-sm" style="position:absolute; top:10px; right:10px">Code</a></div>
This will export the current dataset in the memory as a csv and replace an existing one.

<h2 id="h-7"><span class="heading-secnum">7&nbsp;</span> Built in Datasets.</h2>

<P>STATA comes in with sample datasets that you can use for quick practice.To load a new dataset from the system ,the <code>sysuse</code> keyword is used folowed by the dataset name.</P>
<div style="position:relative"><pre id="stlog-7" class="stlog"><samp><span class="stinp">. sysuse auto.dta help dta_contents</span>
(1978 Automobile Data)
</samp></pre><a href="" target="_blank" class="btn btn-default btn-sm" style="position:absolute; top:10px; right:10px">Code</a></div>
<h2 id="h-8"><span class="heading-secnum">8&nbsp;</span> Conclusion</h2>

<p>We can see that working with STATA is very easy and that it can be used quite easily than any other statistical package.</p>
</body>
