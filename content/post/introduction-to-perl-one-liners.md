---
comments: true
tags: ["perl"]
categories: ["Perl"]
title: "Perl one-liners"
date: 2016-12-29T16:01:23+08:00
---

Introduction to Perl one-liners

Perl one-liners are small and awesome Perl programs that fit in a single line of code and they do one thing really well. These things include changing line spacing, numbering lines, doing calculations, converting and substituting text, deleting and printing certain lines, parsing logs, editing files in-place, doing statistics, carrying out system administration tasks, updating a bunch of files at once, and many more. Perl one-liners will make you the shell warrior. Anything that took you minutes to solve, will now take you seconds!

Let's look at several examples to get more familiar with one-liners. Here is one:

```perl
    perl -pi -e 's/you/me/g' file
```

This one-liner replaces all occurrences of the text *you* with *me* in the file *file*. Very useful if you ask me. Imagine you are on a remote server and have this file and you need to do the replacement. You can either open it in text editor and execute find-replace or just do it through command line and, bam, be done with it.

The **-e** argument is the best argument. It allows you to specify the Perl code to be executed right on the command line. In this one-liner the code says, do the substitution (*s/find/replace/flags* command) and replace *you* with me globally (g flag). The **-p** argument makes sure the code gets executed on every line, and that the line gets printed out after that. The **-i** argument makes sure that **file** gets edited in-place, meaning Perl opens the file, executes the substitution for each line, prints the output to a temporary file, and then replaces the original file.

How about doing the same replacement in multiple files? Just specify them on the command line!

```perl
perl -pi -e 's/you/me/g' file1 file2 file3
```

Now let's do the same replacement only on lines that match we. It's as simple as this:

```perl
perl -pi -e 's/you/me/g if /we/' file
```

Here we use the conditional if /we/. This makes sure that s/you/me/g gets executed only on lines that match the regular expression /we/. The regular expression here can be anything. Let's say you want to execute the substitution only on lines that have digits in them. You can then use the /\d/ regular expression that matches numbers:

```perl
perl -pi -e 's/you/me/g if /\d/' file
```

Now how about finding all repeated lines in a file?

```perl
perl -ne 'print if $a{$_}++' file
```

This one-liner records the lines seen so far in the %a hash and keeps the counter of how many times it has seen the same line. The $a{$_}++ creates elements in the %a hash automagically. When it sees a repeated line, the value of that hash element is defined and greater than zero, so if $a{$_} is true, and it prints the line. This one-liner also uses the -n command line argument that loops over the input but unlike -p doesn't print the lines automatically, so you have to use print explicitly.

How about numbering lines? Super simple! Perl has the $. special variable that automatically maintains the current line number. You can just print it out together with the line:

```perl
perl -ne 'print "$. $_"'
```

You can also achieve the same by using -p argument and modifying the $_ variable, which contains the entire line:

```perl
perl -pe '$_ = "$. $_"'
```

Here each line gets replaced by the string "$. $_", which is the current line number followed by the line itself.

How about we combine the previous two one-liners and create one that numbers repeated lines? Here we go:

```perl
    perl -ne 'print "$. $_" if $a{$_}++'
```

Now let's do something different. Let's sum up all the numbers on each line. We'll use the sum function from the List::Util CPAN module. You can install it as easily as running perl -MCPAN -e'install List::Util'.

```perl
    perl -MList::Util=sum -alne 'print sum @F'
```

The -MList::Util command line argument imports the List::Util module, and the =sum part of it imports the sum function from it. Next -a enables automatic splitting of fields into the @F array. The -l argument makes sure that print outputs a newline at the end of each line. Finally the sum @F sums up all the elements in the @F list and print prints it out, followed by a newline (that was added by the -l argument).

How about finding the date 1299 days ago? That's also solvable by a simple one-liner:

```perl
    perl -MPOSIX -le '
      @now = localtime;
      $now[3] -= 1299;
      print scalar localtime mktime @now
    '
```
This one-liner didn't quite fit in one line, but that's just because my blog has narrow space for content. What happens here is we modify the 4th element of the structure returned by localtime, which happens to be days. So we just subtract 1299 days from the current day. Then we reassembles it into a new time through localtime mktime @now and print it in scalar context that prints human readable time.

How about generating an 8 letter password? Again, solvable elegantly with a one-liner:

```perl
    perl -le 'print map { (a..z)[rand 26] } 1..8'
```

The a..z generates a list of letters from a to z (total 26). Then we randomly choose one of the characters through generating a random number in range 0-25, and then we repeat this whole process 8 times!

Here is another one. Suppose you want to quickly find the decimal number that corresponds to an IP address. You can use the unpack function and find it really quickly:

```perl
    perl -le 'print unpack("N", 127.0.0.1)'
```

This one-liner uses a vstring, which is a version literal. The IP address 127.0.0.1 is treated as a vstring, which is basically the numbers 127, 0, 0, 1 concatenated together. Next the unpack function unpacks them to a single decimal number.

Btw, I once created a cheat sheet with all the pack/unpack format strings. Get it here: perl pack, unpack cheat sheet.

Now how about calculations? Let's find the sum of the numbers in the first column:

```perl
    perl -lane '$sum += $F[0]; END { print $sum }'
```

Here the lines automatically get split up into fields through the -a argument. The fields can be now accessed through the @F array. The first element of the array, $F[0], is the first column. So all we have to do is sum all the columns up through $sum += $F[0]. When the Perl program ends its job, it executes any code in the special END block. In this case we print out the total sum there. Really easy!

Now let's find out how many packets have gone through all the iptables rules. It's this simple:

> iptables -L -nvx | perl -lane '
>   $_ = $F[0]; $pkts += $_ if /^\d/; END { print $pkts }
> '

The iptables program outputs the packets as the first field. All we do is check if the first field is numeric (because it also outputs labels header), and if so, sum the packets up on the first column, just like in the previous one-liner.

How about getting a list of the names of all users on the system?

```perl
    perl -a -F: -lne 'print $F[4]' /etc/passwd
```

Combining -a with -F argument allows you to specify the character that lines should be split on. In this case it's the colon, which is the record separator of /etc/passwd. Next we just print the 5th field $F[4], which is the real name of the user. Really quick and easy.

As you can see, knowing Perl one-liners lets you accomplish many tasks quickly. If you wish to learn more and become really fast in the shell, I suggest you get a copy of my "Perl One-Liners Explained" e-book. The e-book contains 130 unique one-liners and many of them are presented in several different ways, so the total number of one-liners in this book is over 200.