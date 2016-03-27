+++
title = "Sudoku observations and programmatic considerations"
description = "Programmatic considerations pertaining to Sudoku puzzles."
draft = false
comments = true
date = "2010-11-28T10:24:00-06:00"
modified = "2010-11-28T10:39:56-06:00"
slug = "Sudoku-observations-and-programmatic-considerations"
blogengine = "2fd8be25-ab8d-4158-adab-e2bc615787d9"
categories = ["gaming"]
tags = ["sudoku"]
+++

<p>At the lowest level, any Sudoku puzzle consists of a number of squares.</p>
<p>There are&nbsp;<em>rows</em> times <em>columns</em> squares consisting of a single value.</p>
<p>There are <em>x</em> number of larger squares consisting of&nbsp;<em>y</em>&nbsp;values, where&nbsp;<em>x</em> is the smallest of <em>rows</em>&nbsp;and <em>columns</em>, and <em>y</em> is the largest of <em>rows</em> and <em>columns</em>.</p>
<p>As already mentioned, there are a <em>x</em> number of rows, as well as a <em>y</em> number of columns.</p>
<p>Overlap is possible, but the puzzle still consists of these basic parts.</p>
<p>Given the above:</p>
<ul>
<li>Puzzle
<ul>
<li>Rows (int)</li>
<li>Columns (int)</li>
<li>Squares (collection of Square)</li>
</ul>
</li>
<li>Square
<ul>
<li>Value (string)</li>
<li>Row (int)</li>
<li>Column (int)</li>
<li>Block (int)&nbsp;may not be required</li>
</ul>
</li>
</ul>
