
## Testing Out the New ~~

1.  Clone the perl5 git repository:

    $ git clone git://perl5.git.perl.org/perl.git

    ...that may take a few minutes, the first time.

2.  Check out the smartmatch branch.

    $ git checkout -b smartmatch origin/smartmatch

    You should make sure you're pretty up to date.  This command, for example,
    should print 1:

    $ git log | grep -c ea0c2dbd5f5ac6845ecc7ec6696415bf8e27bd52

3.  Compile that perl.  Something like:

      * ./Configure -de -Dusedevel
      * make -j2
      * make test -j2
      * sudo make install

    Now you have perl5.11.0 in your path.

4.  Read the smartmatch spec defined in the pod.
    
    $ perldoc perlsyn

    Grep for "Smart matching in detail"

5.  Write tests exploiting behaviors defined in perlsyn

    Tests are organized into files in ./t *generally* based on the type of
    value on the right hand side of the ~~.  You should feel free to put your
    tests wherever you want.  Nobody is going to be upset because of where it
    is.  More tests is better.

6.  Run: prove -e perl5.11.0

## Simple instructions for git / github newbies:

Install git:

   $ apt-get install git-core 
   # or on a Mac
   $ sudo port -v install git-core
   # FreeBSD and OpenBSD have devel/git, pkgsrc (NetBSD) has devel/scmgit.
   # generally, the package is named either git or git-core, to prevent
   # clobbering the gnuit package's common name.

Clone perl:

   $ git clone git://perl5.git.perl.org/perl.git

### I want a github account

Go to htp://www.github.com, click 'Pricing and Signup', click 'Open Source'.

Follow registration through to get a username and password registered.

If you don't have an ssh key already, generate one with:

   $ ssh-keygen

The file will be either ~/.ssh/id_rsa.pub or ~/.ssh/id_dsa.pub, depending upon
the version of SSH you're using. The program should ask you for a passphrase
for the key, specifying the file name while doing so. Note that if you specify
a passphrase that this passphrase must be given any time the key is used. If
you're only going to use the key for github, it doesn't really need a
passphrase.

Login to github. Add your ssh key to github by clicking "account" in the upper
right corner. Then, on the left-hand side of the page, click "add another public
key" under "SSH Public Keys". Fill in the title (something descriptive) and
copypaste the key into the textbox labelled "Key". Be sure not to include any
newlines when pasting, or the key will not be valid.

Go to: http://github.com/rjbs/perl-smartmatch-tests/tree/master

Click the 'Fork' button

You'll be taken to your own copy of this repository.

Click the text next to 'Your Clone URL'. This will lightbox the git command you
need to run, e.g.

    $ git clone git@github.com:bobtfish/perl-smartmatch-tests.git 

Copy and paste this (the text in the lightbox, not the text above) into your
terminal, and run the command. You now have checked out a copy of these tests.
You can commit (git add file1 file2 & git commit), then upload your work to
github (git push), then click 'Send Pull request' in the web form, and a dialog
box will pop up asking you to write a mail. Write a brief description of your
changes and send.

rjbs will get your message and either integrate the work you've done, or send
you some feedback.

### I don't want a github account

That's fine!

    $ git clone git@github.com:rjbs/perl-smartmatch-tests.git

This will check out a readonly copy of the repository. Add tests and commit
(git add file1 file2 & git commit), possibly multiple times. When you want to
submit your work, then say 'git log'.

Note the sha1 hash below your first commit message.

    $ git format-patch <sha1sum>

Each change you made will be written out as a file similarly named to the
commit message, e.g. 0001-Smartmatch-test-Foo.diff

Mail these diffs as attachments to rjbs for application.


