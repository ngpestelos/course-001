**Q1:** What steps are involved in making a Ruby scripts runnable as a  command line utility?
(i.e. directly runnable like `rake` or `gem` rather than having to type `ruby my_script.rb`)

**Answer:** Add a shebang line at the top of the script (e.g. `#! /usr/bin/env ruby`).

**Q2:** What is `ARGF` stream used for in Ruby?

**Answer:** `ARGF` contains file names passed as arguments. Ruby will then open and read each file.

**Q3:** What is `$?` used for in Bash/Ruby?

**Answer:** `$?` contains the child process' status code (see `Process::Status`)

**Q4:** What does an exit status of zero indicate when a command line script terminates? How about a non-zero exit status?

By convention, a `0` code refers to a normal exit (i.e., no errors) while any other status code denotes an abnormal exit.

**Q5:** What is the difference between the `STDOUT` and `STDERR` output streams?

**Answer:** `STDOUT` (standard output stream) is where the process' outputs are sent. `STDERR` (standard error stream) is where error messages are sent. Streams are objects similar to files, where process can read and write against.

**Q6:** When executing shell commands from within a Ruby script, how can you capture
what gets written to `STDOUT`? How do you go about capturing both `STDOUT` and `STDERR` streams?

**Answer:** Use the `Open3` module. `Open3` provides a method called `capture3` that creates a sub-process and returns its standard output, standard error, and exit code.

**Q7:** How can you efficiently write the contents of an input file to `STDOUT` with empty lines omitted? Being efficient in this context means avoiding storing the full contents of the input file in memory and processing the stream in a single pass.

**Answer:** Read the input file line-by-line and if a line only is empty after removing the newline, then read the next line.

**Q8:** How would you go about parsing command line arguments that contain a mixture of flags and file arguments? (i.e. something like `ls -a -l foo/*.txt`)

**Answer:**  Use `OptionParser` and pass `ARGV` to its `parse` method.

**Q9:** What features are provided by Ruby's `String` class to help with fixed width text layouts? (i.e. right aligning a column of numbers, or left aligning a column of text with some whitespace after it to keep the total  column width uniform)

**Answer:** `String#ljust` and `String#rjust`. Both methods take an argument (number of characters to pad).

**Q10:** Suppose your script encounters an error and has to terminate itself. What is the idiomatic Unix-style way of reporting that the command did not run successfully?

**Answer:** Return a non-zero exit code.
