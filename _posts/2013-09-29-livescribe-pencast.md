---
layout: post
title: Livescribe Pencast PDFs on Linux
---

For a course I'm taking, supplementary material is provided as Livescribe Pencast PDFs. These are PDFs recorded with a special pen, which saves audio and the pen movements. However, they only work with Adobe Reader X and above, which is not available on Linux. The following solution allows you to extract the audio as an M4A file, although not the pen movements (they are encoded in a plain-text format, though, so it should be possible to write a viewer for them).

You'll need [Sejda](http://www.sejda.org/download/), an open-source command-line utility (and Java library) for various PDF operations. Download sejda-console. After extracting the zip file and `cd`'ing into the top directory, execute the following commands:


{% highlight bash %}
cd bin
chmod a+x sejda-console
./sejda-console unpack -o DIRECTORY -f PDF_FILE
{% endhighlight %}

Now the M4A file should be in DIRECTORY.
