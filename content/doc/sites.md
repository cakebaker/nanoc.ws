---
title: "Sites"
is_dynamic: true
---

A site managed by Nanoc is a directory with a specific structure. It contains source data, as well as processing instructions that describe how the site should be compiled.

By default, Nanoc uses the `filesystem` data source, which means that source data is stored inside the <span class="filename">content/</span> directory. Nanoc can read from other sources too, including databases or web APIs. For details, see the <%= link_to_id('/doc/data-sources.*') %> page.

## Creating a site

To create a site, use the `create-site` command. This command takes the site name as an argument. For example:

<pre><span class="prompt">%</span> <kbd>nanoc create-site tutorial</kbd>
      <span class="log-create">create</span>  nanoc.yaml
      <span class="log-create">create</span>  Rules
      <span class="log-create">create</span>  content/index.html
      <span class="log-create">create</span>  content/stylesheet.css
      <span class="log-create">create</span>  layouts/default.html
Created a blank Nanoc site at 'tutorial'. Enjoy!</pre>

## Directory structure

A site has the following files and directories:

<span class="filename">nanoc.yaml</span>
<span class="filename">config.yaml</span> (on older sites)
: contains the site configuration

<span class="filename">Rules</span>
: contains compilation, routing and layouting rules

<span class="filename">content/</span>
: contains the uncompiled items

<span class="filename">layouts/</span>
: contains the layouts

<span class="filename">lib/</span>
: contains custom site-specific code (filters, helpers, …)

<span class="filename">output/</span>
: contains the compiled site

<span class="filename">tmp/</span>
: contains data used for speeding up compilation (can be safely emptied)

## Code

Nanoc will load all Ruby source files in the <span class="filename">lib/</span> directory before it starts compiling. All method definitions, class definitions, … will be available during the compilation process. This directory is useful for putting in custom <a href="/doc/helpers/">helpers</a>, custom <a href="/doc/filters/">filters</a>, custom <a href="/doc/data-sources/">data sources</a>, etc.

## Compiling a site

To compile a site, invoke <span class="command">nanoc</span> on the command line. For example:

<pre><span class="prompt">%</span> <kbd>nanoc</kbd>
Loading site data… done
Compiling site…
      update  [0.05s]  output/doc/sites/index.html

Site compiled in 2.42s.</pre>

It is recommended to use [Bundler](http://bundler.io/) with Nanoc sites. When using bundler, compiling a site is done by invoking <span class="command">bundle exec nanoc</span> on the command line.

To pass additional options when compiling a site, invoke the <span class="command">nanoc compile</span>, and pass the desired options.

Nanoc will not compile items that are not outdated. If you want to force Nanoc to recompile everything, delete the output directory and re-run the compile command.

You can use [guard-nanoc](https://github.com/guard/guard-nanoc) to automatically recompile the site when it changes.
