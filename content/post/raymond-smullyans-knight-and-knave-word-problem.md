+++
title = "Raymond Smullyan's Knight and Knave Word Problem"
description = "A look at Raymond Smullyan's knight and knave word problem, as introduced to me by David Gries."
draft = false
comments = true
date = "2005-04-24T00:01:00-05:00"
slug = "Raymond-Smullyans-Knight-and-Knave-Word-Problem"
blogengine = "aa95af8f-ebf0-4434-9829-01a90daa6d9a"
categories = ["article", "philosophy"]
tags = []
+++

<p>
According to David Gries (via his site), logician Raymond Smullyan stated the following word problem in one of his many books, which regards lying knaves and truthful knights.
</p>
<!--more-->
<p>
A group of three people, each of which is a knight (tells the truth all the time) or a knave (lies all the time) are talking. B says that C and D are the same type (both knaves or both knights). Someone then asks D, &ldquo;Are B and C the same type?&rdquo; What does D answer?<!--adsense-->
</p>
<p>
While Dr. Gries states that case analysis is confusing, I beg to differ. According to this, we look at what would happen if a number of cases were true. In logic books, this is most often done by way of a truth table.
</p>
<p>
First, we must determine our variables. We have, as given in the problem itself, B, C, and D, each of which can be either a knight or a knave.
</p>
<p>
Second, we must determine our equations. We have two different equations. For the first, does C = D according to B. For the second, does B = C according to D. Of course, if B or D is lying, then they will give us the opposite answer.
</p>
<table border="1" cellspacing="0" cellpadding="0">
	<tbody>
		<tr>
			<td width="115" valign="top">
			<p>
			<strong>B</strong>
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			<strong>C</strong>
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			<strong>D</strong>
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			<strong>B, C = D?</strong>
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			<strong>D, B = C?</strong>
			</p>
			</td>
		</tr>
		<tr>
			<td width="115" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			True
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
		<tr>
			<td width="115" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			False
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			False
			</p>
			</td>
		</tr>
		<tr>
			<td width="115" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			False
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			False
			</p>
			</td>
		</tr>
		<tr>
			<td width="115" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			True
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
		<tr>
			<td width="115" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			False
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			False
			</p>
			</td>
		</tr>
		<tr>
			<td width="115" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			True
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
		<tr>
			<td width="115" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			True
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
		<tr>
			<td width="115" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			False
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			False
			</p>
			</td>
		</tr>
	</tbody>
</table>
<p>
Now, we are given that B says that C and D are the same. We can therefore look at just those that have &lsquo;True&rsquo; in our &lsquo;B, C = D?&rsquo; column.
</p>
<table border="1" cellspacing="0" cellpadding="0">
	<tbody>
		<tr>
			<td width="115" valign="top">
			<p>
			<strong>B</strong>
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			<strong>C</strong>
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			<strong>D</strong>
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			<strong>B, C = D?</strong>
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			<strong>D, B = C?</strong>
			</p>
			</td>
		</tr>
		<tr>
			<td width="115" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			True
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
		<tr>
			<td width="115" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			True
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
		<tr>
			<td width="115" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			True
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
		<tr>
			<td width="115" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			True
			</p>
			</td>
			<td width="115" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
	</tbody>
</table>
<p>
We see now that D would say that B and C are the same as well. We also see that either one of them is a knight and the other two are knaves, or they are all knights.
</p>
<p>
Of course, the question is not what the type of each is, but rather is a question of what D answers. So, if one is able to find at least one of these cases, they can answer the question &ndash; the answer does not require all possibilities to be found, assuming that the question does not bring about contradictory answers.
</p>
<p>
Let us, for our own benefit, now ask what C would say to the question of whether B is the same type as D.
</p>
<table border="1" cellspacing="0" cellpadding="0">
	<tbody>
		<tr>
			<td width="99" valign="top">
			<p>
			<strong>B</strong>
			</p>
			</td>
			<td width="99" valign="top">
			<p>
			<strong>C</strong>
			</p>
			</td>
			<td width="99" valign="top">
			<p>
			<strong>D</strong>
			</p>
			</td>
			<td width="96" valign="top">
			<p>
			<strong>B, C = D?</strong>
			</p>
			</td>
			<td width="96" valign="top">
			<p>
			<strong>D, B = C?</strong>
			</p>
			</td>
			<td width="87" valign="top">
			<p>
			<strong>C, B = D?</strong>
			</p>
			</td>
		</tr>
		<tr>
			<td width="99" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="99" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="99" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="96" valign="top">
			<p>
			True
			</p>
			</td>
			<td width="96" valign="top">
			<p>
			True
			</p>
			</td>
			<td width="87" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
		<tr>
			<td width="99" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="99" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="99" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="96" valign="top">
			<p>
			False
			</p>
			</td>
			<td width="96" valign="top">
			<p>
			False
			</p>
			</td>
			<td width="87" valign="top">
			<p>
			False
			</p>
			</td>
		</tr>
		<tr>
			<td width="99" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="99" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="99" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="96" valign="top">
			<p>
			False
			</p>
			</td>
			<td width="96" valign="top">
			<p>
			False
			</p>
			</td>
			<td width="87" valign="top">
			<p>
			False
			</p>
			</td>
		</tr>
		<tr>
			<td width="99" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="99" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="99" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="96" valign="top">
			<p>
			True
			</p>
			</td>
			<td width="96" valign="top">
			<p>
			True
			</p>
			</td>
			<td width="87" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
		<tr>
			<td width="99" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="99" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="99" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="96" valign="top">
			<p>
			False
			</p>
			</td>
			<td width="96" valign="top">
			<p>
			False
			</p>
			</td>
			<td width="87" valign="top">
			<p>
			False
			</p>
			</td>
		</tr>
		<tr>
			<td width="99" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="99" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="99" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="96" valign="top">
			<p>
			True
			</p>
			</td>
			<td width="96" valign="top">
			<p>
			True
			</p>
			</td>
			<td width="87" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
		<tr>
			<td width="99" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="99" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="99" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="96" valign="top">
			<p>
			True
			</p>
			</td>
			<td width="96" valign="top">
			<p>
			True
			</p>
			</td>
			<td width="87" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
		<tr>
			<td width="99" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="99" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="99" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="96" valign="top">
			<p>
			False
			</p>
			</td>
			<td width="96" valign="top">
			<p>
			False
			</p>
			</td>
			<td width="87" valign="top">
			<p>
			False
			</p>
			</td>
		</tr>
	</tbody>
</table>
<p>
We see that C would give the same reasons as the others when asked the question. This is really quite interesting, if not only because it at first appears we&rsquo;re asking the question of whether C = D and B = C, and therefore if B = D. We presume that if someone tells us that C = D, and that another tells us that B = C, then B = D. However, if we bring lying, or more broadly, doubt into the equation, we find that that is not necessarily the case.
</p>
<p>
We can expand upon this same example. For example, let us take some individual E, which we know is either a knight or a knave. Let us ask this individual if they are a knight.
</p>
<table border="1" cellspacing="0" cellpadding="0">
	<tbody>
		<tr>
			<td width="287" valign="top">
			<p>
			<strong>E</strong>
			</p>
			</td>
			<td width="288" valign="top">
			<p>
			<strong>E, E = Knight?</strong>
			</p>
			</td>
		</tr>
		<tr>
			<td width="287" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="288" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
		<tr>
			<td width="287" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="288" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
	</tbody>
</table>
<p>
Now let us look at what would have been the case if we had asked them if they were a knave, instead.
</p>
<table border="1" cellspacing="0" cellpadding="0">
	<tbody>
		<tr>
			<td width="287" valign="top">
			<p>
			<strong>E</strong>
			</p>
			</td>
			<td width="288" valign="top">
			<p>
			<strong>E, E = Knave?</strong>
			</p>
			</td>
		</tr>
		<tr>
			<td width="287" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="288" valign="top">
			<p>
			False
			</p>
			</td>
		</tr>
		<tr>
			<td width="287" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="288" valign="top">
			<p>
			False
			</p>
			</td>
		</tr>
	</tbody>
</table>
<p>
We can, therefore, get nowhere if simply ask an individual whether or not they always lie or always tell the truth, just as we cannot ask an individual if they ever lie, for they may lie or may tell the truth when they answer the question.
</p>
<p>
But, does having two people help our quest for the truth? Let us take F and G, which are each either a knight or a knave. Now let us ask one if they are of the same type, similar to what was asked in the original question, and he answers that they are.
</p>
<table border="1" cellspacing="0" cellpadding="0">
	<tbody>
		<tr>
			<td width="192" valign="top">
			<p>
			<strong>F</strong>
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			<strong>G</strong>
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			<strong>F, F = G?</strong>
			</p>
			</td>
		</tr>
		<tr>
			<td width="192" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
		<tr>
			<td width="192" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			False
			</p>
			</td>
		</tr>
		<tr>
			<td width="192" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
		<tr>
			<td width="192" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			False
			</p>
			</td>
		</tr>
	</tbody>
</table>
<p>
At the very least we know that G is a Knight. We can then ask G if they are the same.
</p>
<table border="1" cellspacing="0" cellpadding="0">
	<tbody>
		<tr>
			<td width="192" valign="top">
			<p>
			<strong>F</strong>
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			<strong>G</strong>
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			<strong>G, F = G?</strong>
			</p>
			</td>
		</tr>
		<tr>
			<td width="192" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
		<tr>
			<td width="192" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
		<tr>
			<td width="192" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			False
			</p>
			</td>
		</tr>
		<tr>
			<td width="192" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			False
			</p>
			</td>
		</tr>
	</tbody>
</table>
<p>
However, this requires two questions. Can we do it in one? If we were to ask F is G is a knight, and they say yes, we see that they are at least the same class (and if they say no, that they are of a different class).
</p>
<table border="1" cellspacing="0" cellpadding="0">
	<tbody>
		<tr>
			<td width="192" valign="top">
			<p>
			<strong>F</strong>
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			<strong>G</strong>
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			<strong>F, G = Knight?</strong>
			</p>
			</td>
		</tr>
		<tr>
			<td width="192" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
		<tr>
			<td width="192" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			False
			</p>
			</td>
		</tr>
		<tr>
			<td width="192" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			False
			</p>
			</td>
		</tr>
		<tr>
			<td width="192" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
	</tbody>
</table>
<p>
We could ask a more difficult question of F; if you were G, would you say that F is a knight? If he said yes, we would at least know that G is a knight. Here, the third column contains the answer, and the fourth/last is for assistance while reading the table.
</p>
<table border="1" cellspacing="0" cellpadding="0">
	<tbody>
		<tr>
			<td width="146" valign="top">
			<p>
			<strong>F</strong>
			</p>
			</td>
			<td width="147" valign="top">
			<p>
			<strong>G</strong>
			</p>
			</td>
			<td width="150" valign="top">
			<p>
			<strong>F, if G, F = Knight?</strong>
			</p>
			</td>
			<td width="132" valign="top">
			<p>
			<strong>(G, F = Knight?)</strong>
			</p>
			</td>
		</tr>
		<tr>
			<td width="146" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="147" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="150" valign="top">
			<p>
			True
			</p>
			</td>
			<td width="132" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
		<tr>
			<td width="146" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="147" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="150" valign="top">
			<p>
			False
			</p>
			</td>
			<td width="132" valign="top">
			<p>
			False
			</p>
			</td>
		</tr>
		<tr>
			<td width="146" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="147" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="150" valign="top">
			<p>
			True
			</p>
			</td>
			<td width="132" valign="top">
			<p>
			False
			</p>
			</td>
		</tr>
		<tr>
			<td width="146" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="147" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="150" valign="top">
			<p>
			False
			</p>
			</td>
			<td width="132" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
	</tbody>
</table>
<p>
This gives us the idea of asking the following question of F to find out F&rsquo;s status. If you were F, and you were asked if F would say that F was a knight, what would you say?
</p>
<table border="1" cellspacing="0" cellpadding="0">
	<tbody>
		<tr>
			<td width="192" valign="top">
			<p>
			<strong>F</strong>
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			<strong>F, F = Knight?</strong>
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			<strong>F, if F, F = Knight?</strong>
			</p>
			</td>
		</tr>
		<tr>
			<td width="192" valign="top">
			<p>
			Knight
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			True
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			True
			</p>
			</td>
		</tr>
		<tr>
			<td width="192" valign="top">
			<p>
			Knave
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			True
			</p>
			</td>
			<td width="192" valign="top">
			<p>
			False
			</p>
			</td>
		</tr>
	</tbody>
</table>
<p>
Therefore, if we look at the question that originally got us going on this thread, the better question would be to ask B first whether or not if they were B, whether they would tell us if they were a knight. If they say that if they were B they would tell us that they would tell us that they were a knight, then we know that they are a knight. On the other hand, if they were to tell us that they would not tell us that B was a knight, if they were B, then we know that they are a knave. For if B were a liar they would lie and say that they were a knight if they were asked if they were a knight, but, because B is asked whether B would lie if they were B and asked, they would have to say that B would not say that.
</p>
<h4>Note</h4>
<p>
While the problem and solution are found at <a href="http://www.cs.cornell.edu/Info/People/gries/Logic/Neatsolution.html" onclick="window.open(this.href);return false;">http://www.cs.cornell.edu/Info/People/gries/Logic/Neatsolution.html</a>, I have gone about solving the problem my own particular way, by expanding out the possible cases in a table.
</p>

