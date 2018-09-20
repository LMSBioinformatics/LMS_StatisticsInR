<!DOCTYPE html>
<html lang="en-us">
  <head>
    <meta charset="UTF-8">
    <title>Chipseq short by mrccsc</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" type="text/css" href="stylesheets/normalize.css" media="screen">
    <link href='https://fonts.googleapis.com/css?family=Open+Sans:400,700' rel='stylesheet' type='text/css'>
    <link rel="stylesheet" type="text/css" href="stylesheets/stylesheet.css" media="screen">
    <link rel="stylesheet" type="text/css" href="stylesheets/github-light.css" media="screen">
  </head>
  <body>
    <section class="page-header">
      <h1 class="project-name">Chipseq short</h1>
      <h2 class="project-tagline"></h2>
      <a href="https://github.com/mrccsc/ChIPseq_short" class="btn">View on GitHub</a>
      <a href="https://github.com/mrccsc/ChIPseq_short/zipball/master" class="btn">Download .zip</a>
      <a href="https://github.com/mrccsc/ChIPseq_short/tarball/master" class="btn">Download .tar.gz</a>
    </section>

    <section class="main-content">
      <h1>
<a id="chip-seq-short-course" class="anchor" href="#chip-seq-short-course" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>ChIP-seq (short course)</h1>


<p><a href="https://gitter.im/mrccsc/ChIPseq_short?utm_source=badge&amp;utm_medium=badge&amp;utm_campaign=pr-badge&amp;utm_content=badge"><img src="https://badges.gitter.im/Join%20Chat.svg" alt="Join the chat at https://gitter.im/mrccsc/ChIPseq_short"></a></p>

<h2>
<a id="the-course" class="anchor" href="#the-course" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>The Course</h2>

<p>This course introduces some of the fundamental concepts and tools of ChIP-seq analysis in R/Bioconductor. This course is a shortened version of our full course and covers downstream analysis of ChIP-seq following peak calling and aquisition of QC results.</p>

<p>The course consists of 7 sections.</p>

<ul>
<li>Evaluation of ChIP-seq specific QC metrics</li>
<li>Working with peaks.</li>
<li>Functional annotation of peaks.</li>
<li>Motif identification.</li>
<li>External/Public datasets.</li>
<li>Exporting data.</li>
<li>Complex overlaps.</li>
<li>Simple differential ChIP-seq.</li>
</ul>

<p>Each section is presented as both HTMl and Rpres markdown ( to allow for intergration of the presentation in the RStudio enviroment itself).  Exercises and answer sheets are included after all subsections to practice techniques and provide future reference examples. </p>

<p>Course material and exercises are available to view as rendered HTML slides or single page HTML at <a href="http://mrccsc.github.io/ChIPseq_short">http://mrccsc.github.io/ChIPseq_short/</a>.<br>
All material is available to download under GPL Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License.
 license.</p>

<p>For  information on other courses run by our team see our <a href="http://mrccsc.github.io/training/">github IO page</a>.</p>

<h2>
<a id="the-team" class="anchor" href="#the-team" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>The Team</h2>

<p>This course was created and conducted by the MRC Clinical Sciences Centre Bioinformatics Team at Imperial College London, Hammersmith Hospital.<br>
For more information on the team see our <a href="http://mrccsc.github.io/">github IO page</a>.</p>

<p>This course is free for MRC CSC and Imperial staff and students. If you would like to attend a future course contact <a href="mailto:thomas.carroll@imperial.ac.uk">thomas.carroll@imperial.ac.uk</a>.</p>

<h2>
<a id="setting-up" class="anchor" href="#setting-up" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>Setting up.</h2>

<h4>
<a id="install-r" class="anchor" href="#install-r" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>Install R.</h4>

<p>R can be installed from the R-project website.<br>
R 3.1.0 or higher is required for this course.</p>

<p><a href="http://www.r-project.org/">http://www.r-project.org/</a></p>

<h4>
<a id="install-rstudio" class="anchor" href="#install-rstudio" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>Install RStudio.</h4>

<p>RStudio can be installed from the R-project website. </p>

<p><a href="http://www.rstudio.com/">http://www.rstudio.com/</a></p>

<h4>
<a id="install-required-packages" class="anchor" href="#install-required-packages" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>Install required packages.</h4>

<p>Having downloaded R and RStudio, some additional packages are required (rmarkdown and ggplot2).<br>
To install these,</p>

<ul>
<li>First launch RStudio</li>
<li>Install the packages in the R console
<pre>
source("<a href="https://bioconductor.org/biocLite.R">https://bioconductor.org/biocLite.R</a>")
biocLite("GenomicRanges")
biocLite("ChIPQC")
biocLite("BSgenome.Mmusculus.UCSC.mm9")
biocLite("ChIPseeker")
biocLite("goseq")
biocLite("rGREAT")
biocLite("AnnotationHub")
</pre>
</li>
</ul>

<h4>
<a id="download-the-material" class="anchor" href="#download-the-material" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>Download the material</h4>

<p>The material can either be downloaded as a <a href="https://github.com/mrccsc/ChIPseq_short/archive/master.zip">zip</a></p>

<pre>
wget https://github.com/mrccsc/ChIPseq_short/archive/master.zip ./
</pre>

<p>or checked out from our Github repository
<a href="https://github.com/mrccsc/ChIPseq_short/">https://github.com/mrccsc/ChIPseq_short/</a></p>

<h2>
<a id="ChIP-seq-Short-course" class="anchor" href="#ChIP-seq-Short-course" aria-hidden="true"><span class="octicon octicon-link"></span></a>ChIP-seq short course</h2>

<h4>
<a id="ChIPseq" class="anchor" href="#ChIPseq" aria-hidden="true"><span class="octicon octicon-link"></span></a>ChIP-seq short</h4>

<p>In this ChiP-seq course we introduce some of the fundamental concepts and tools of ChIP-seq analysis in R/Bioconductor. This course is a shortened version of our full course and covers downstream analysis of ChIP-seq following peak calling and aquisition of QC results.</p>
<ul>
<li>Evaluation of ChIP-seq specific QC metrics</li>
<li>Working with peaks.</li>
<li>Functional annotation of peaks.</li>
<li>Motif identification.</li>
<li>External/Public datasets.</li>
<li>Exporting data.</li>
<li>Complex overlaps.</li>
<li>Simple differential ChIP-seq.</li>
</ul>
Link to HTML presentation - <a href="http://mrccsc.github.io/ChIPseq_short/course/presentations/slides/ChIPseq_Slides.html">ChIP-seq slides</a><br>
Link to printable PDF - <br>
Link to single page, printable HTML - <a href="http://mrccsc.github.io/ChIPseq_short/course/presentations/singlepage/ChIPseq_singlepage.html">ChIP-seq single page</a><br>
 
</p>
<iframe src="http://mrccsc.github.io/ChIPseq_short/course/presentations/slides/ChIPseq_Slides.html" width="100%" height="400"></iframe>

      <footer class="site-footer">
        <span class="site-footer-owner"><a href="https://github.com/mrccsc/ChIPseq_short">Chipseq short</a> is maintained by <a href="https://github.com/mrccsc">mrccsc</a>.</span>

        <span class="site-footer-credits">This page was generated by <a href="https://pages.github.com">GitHub Pages</a> using the <a href="https://github.com/jasonlong/cayman-theme">Cayman theme</a> by <a href="https://twitter.com/jasonlong">Jason Long</a>.</span>
      </footer>

    </section>

  
  </body>
</html>
