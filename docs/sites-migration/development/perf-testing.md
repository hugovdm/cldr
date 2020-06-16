# Perf Testing

*This from an email exchange about the best perf tool to use for performance
testing.*

The tool is called JVM Monitor. Their website is jvmmonitor.org.

The installation instructions can be found at
http://www.jvmmonitor.org/download/index.html ( I took option 1 : Help ->
Eclipse Marketplace ), and just followed the prompts.

Once you have it installed and restart eclipse, you will see an additional
"perspective" in the upper right corner of your eclipse window. You probably
have "java" and "debug" perspectives, and perhaps a few others. Selecting the
"Java Monitor" perspective gets you into the tools. Switching over to this
perspective while running any program will allow you to monitor memory usage, do
CPU profiling, etc. If you're running a local ST, you start by finding its
thread in the upper left corner, and then right-click and select "Start
Monitoring..."

I've just started using this and am not an expert on it by any means, but at
least I can use it to help us find the "big" problems. I've been focusing mostly
on CPU and run times so far, but the tool has a lot of features that can help us
with memory as well, if we can figure out how to use them.

What was quirky is that it appears to be built for servers. You're also faced
with a bunch of blank screens when you run.

I had to (a) set up all files for the CPU testing, (b) start the program
(VettingViewer.java), then (c) as soon as I saw the process show up in the
monitor window, right-click and tell it to monitor (probably missing some
stuff). Then (d) quickly move to the CPU window and hit the | > icon. And once
the program finishes, then if you move out of that window, you lose the data.

To get the Hot Spots, go to the JVM Explorer Properties. On the left side, pick
CPU. Then at the bottom, pick the Hot Spots tab. However, then you have to hit
the Resume arrow at the top left!
