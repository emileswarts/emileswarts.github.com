---
layout: post
title: Testing Haskell with Hspec
description: Build a minimal Haskell program by using tests.  We will be looking at Hspec, and building our own version of the zip function.
---

### Today I will be looking at <a href="http://hspec.github.io" target="_blank">Hspec</a>, a Haskell <a href="http://en.wikipedia.org/wiki/Behavior-driven_development" target="_blank">BDD</a> automated testing framework roughly based on Ruby's <a href="http://rspec.info/" target="_blank">RSpec</a>.

With Haskell being a <a href="http://www.haskell.org/haskellwiki/Typing" target="_blank">strongly typed language</a>, it is hard to imagine it being anything like RSpec.

Certainly the implementation has to be very different, because RSpec uses much of Ruby's dynamic nature to make it as concise and intuitive as it is.

One tiny detail I noticed straight off the bat is that RSpec has a capital S in the name while Hspec does not.

Let's try a small example and see what it is like.

What we will be testing
------------------------

By the end of this, we will have implemented a custom zip' recursive function which acts the same as <a href="http://www.haskell.org/hoogle/?hoogle=zip" target="_blank">zip</a> found in the <a href="http://www.haskell.org/onlinereport/standard-prelude.html" target="_blank">Prelude module</a>.
This is a very basic function that accepts a list of <a href="http://hackage.haskell.org/package/base-4.6.0.1/docs/Data-Tuple.html" target="_blank">tuples</a>, and retuns a list of tuples containing elements from both lists that occur in the same
positions.

<strong>Example:</strong>

<pre>
Input: zip [1,2,3] [9,8,7]

Output: [(1,9),(2,8),(3,7)]
</pre>

Setup
------

  There is a command line tool called <a href="http://www.haskell.org/cabal/" target="_blank">Cabal</a> that enables you to install Haskell packages and automatically deal with their dependencies.  By default cabal will look in <a href="http://hackage.haskell.org/" target="_blank">Hackage</a>, which is Haskell's central package archive.

  <pre>cabal update &amp;&amp; cabal install hspec</pre>

  This takes a few moments to execute, and it flagged some warnings regarding functions with a ' in the name, but did not break the install.
  (Having a ' in a function name is perfectly normal in Haskell and indicates that it is related to a preceding function with the same name but lacking the '.  This kind of function is called a <a href="http://stackoverflow.com/questions/10363206/what-does-apostrophe-means-in-haskell" target="_blank">prime</a>, just like a prime in algebra)

First test
-----------
  Let's create our first minimal spec file.

  <pre>mkdir ~/hspec_test &amp;&amp; cd ~/hspec_test<br />
touch zipSpec.hs</pre>


  It is Hspec convention to name spec files with "Spec" in the name, which enables automatic <a href="http://hspec.github.io/hspec-discover.html" target="_blank">spec discovery </a> when you want to run an entire suite.  You will also generally have one spec file per source file, but in this small example, I will be defining the code inline in the spec file.

  Ok lets see what happens when we run this blank spec file.

  <pre>runhaskell zipSpec.hs</pre>

  As expected, we get an error to help guide us along the way.

<pre style='color:red'>zipSpec.hs:1:33:
    Not in scope: `main'
    Perhaps you meant `min' (imported from Prelude)
</pre>

This error message tells us that there is no "main" action, and we certainly did not want to run the <a href="http://zvon.org/other/haskell/Outputprelude/min_f.html" target="_blank">min</a> function.

Like in C the <a href="https://publib.boulder.ibm.com/infocenter/comphelp/v8v101/index.jsp?topic=%2Fcom.ibm.xlcpp8a.doc%2Flanguage%2Fref%2Fmainf.htm" target="_blank">main</a> action is the required entry point into the program.  So let's create it.
<p>There is also some boilerplate to get this going is pretty minimal and we only need to import Hspec.</p>
Add the following to your zipSpec.hs file.

<pre>
import Test.Hspec

main = hspec $ do
  describe "zip'" $ do
    it "creates a list of tuples containing elements of both lists occuring in the same position" $ do
      zip' [1,2,3] [9,8,7] `shouldBe` [(1,9),(2,8),(3,7)]

</pre>

We have created a <a href="http://www.haskell.org/tutorial/monads.html" target="_blank">binding</a> for the main action, which is our spec declaration.
If you were wondering about some of strange syntax, dont worry.  It is the way that Haskell achieves such a high level of expressiveness.
This means that very few lines of code can convey an incredible amount of information.

I would like to point out in particular the <a href="http://stackoverflow.com/questions/940382/haskell-difference-between-dot-and-dollar-sign" target="_blank">$ sign</a>, which is simply syntactic sugar making it possible to omit the parentheses.

<p>We run our test again and get our first actual assertion error.</p>

<pre style='color:red'>
zipSpec.hs:6:5:
    Not in scope: zip'
    Perhaps you meant one of these:
      `zip3' (imported from Prelude), `zip' (imported from Prelude)
</pre>


Getting to Green
-----------------

We can now start filling out our program to satisfy the test.<br />
We start by defining our <a href="http://www.haskell.org/haskellwiki/Type_signature" target="_blank">type signature</a>.

<pre>
  import Test.Hspec

  <strong>zip' :: [a] -> [b] -> [(a,b)]</strong>

  main = hspec $ do
  ...
</pre>

Run again with <strong>runhaskell zipSpec.hs</strong>

<pre style='color:red'>
zipSpec.hs:3:1:
    The type signature for zip' lacks an accompanying binding
</pre>

Next, as instructed by the failing test, we create our binding for the signature.

<pre>
  import Test.Hspec

  zip' :: [a] -> [b] -> [(a,b)]
  <strong>zip' (x:xs) (y:ys) = (x,y):zip' xs ys</strong>

  main = hspec $ do
  ...
</pre>

Run again, and we get our next error message:

<pre style='color:red'>
zip'
  - creates a list of tuples containing elements of both lists occuring in the same position FAILED [1]

1) zip' creates a list of tuples containing elements of both lists occuring in the same position
uncaught exception: PatternMatchFail (zipSpec.hs:4:1-37: Non-exhaustive patterns in function zip')
</pre>

Our full implementation of the function declaration, including the <a href="http://www.haskell.org/tutorial/patterns.html" target="_blank">pattern matching</a> code looks like this below.  It can deal with two additional base cases where the inputs can be empty lists.

<pre>
import Test.Hspec

<strong>zip' :: [a] -> [b] -> [(a,b)]
zip' _ [] = []
zip' [] _ = []
zip' (x:xs) (y:ys) = (x,y):zip' xs ys</strong>

main = hspec $ do
  describe "zip'" $ do
    it "creates a list of tuples containing elements of both lists occuring in the same position" $ do
      zip' [1,2,3] [9,8,7] `shouldBe` [(1,9),(2,8),(3,7)]
</pre>

Running again, we get our first passing test.

<pre style='color:green;font-weight:bold'>
 zip'
  - creates a list of tuples containing elements of both lists occuring in the same position

Finished in 0.0002 seconds
1 example, 0 failures
</pre>

<p>If we were to do this test first style, we would drive out the edgecases of empty lists being passed in.  I am not doing this for brevity.</p>

Obviously we do not know that we are testing anything until we have seen it fail for the right reason. Lets break it and see how the test responds.
Change the assertion from <strong>[(1,9),(2,8),(3,7)] to []</strong>, resulting in an obivous assertion error and run the test again.

And back to red again
----------------------

We run it again and see that it complains about the failed assertion, which is great.

<pre style="color:red">
zip'
  - creates a list of tuples containing elements of both lists occuring in the same position FAILED [1]

1) zip' creates a list of tuples containing elements of both lists occuring in the same position
expected: []
but got: [(1,3),(2,4)]
 </pre>

Ok so this is looking promising.  We now have a test that enables us to start poking at haskell to see how it responds.

From here you can try out more functions, and make sure that you get the output that you expect.  You will need to include the different library files
depending on what functionality you are trying to test.

Hspec RSpec similarities
-------------------------

<p>Describes can be nested to give extra context.  In fact context in Hspec is just an alias for describe.</p>
There are also before blocks for setup, before the test runs.<br />
You can also create a spec helper file, just like RSpec that is imported into your specs, helping keep tests <a href="http://en.wikipedia.org/wiki/Don%27t_repeat_yourself" target="_blank">DRY</a>.

More testing frameworks for Haskell
------------------------------------
<a href="http://www.haskell.org/haskellwiki/Introduction_to_QuickCheck1" target="_blank">QuickCheck</a>
<a href="http://hackage.haskell.org/package/HTF" target="_blank">HTF</a>
<a href="http://hackage.haskell.org/package/test-framework-hunit" target="_blank">HUnit</a>
<a href="http://hackage.haskell.org/package/smallcheck" target="_blank">Smallcheck</a>
