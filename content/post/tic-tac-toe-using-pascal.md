+++
title = "Tic-Tac-Toe using Pascal"
description = "The main code for a Tic Tac Toe application written in Pascal."
draft = false
comments = true
date = "2010-07-24T11:48:00-05:00"
modified = "2010-07-24T12:00:14-05:00"
slug = "Tic-Tac-Toe-using-Pascal"
blogengine = "d2ce8dcd-3b3e-42e9-a5d0-b3c93650e0e4"
categories = ["article", "software"]
tags = ["pascal"]
+++

<p>The following is a really old program (November 2003) written in Pacal using Bloodshed Dev-Pascal (which seems to no longer be updated).</p>
<p>This is the code in main.pas, which it seems is the only file really necessary.</p>
<p>This code is covered by a <a rel="external" href="http://creativecommons.org/licenses/by-nc/3.0/">Creative Commons&nbsp;Attribution-NonCommercial 3.0 license</a>.</p>
<pre class="code"><code class="pascal">program TicTacToe (input, output);
label
     begingame, picknumber, checkmove, checkforwin, compmove, winner, nobodywon, playagain, illegalmove, compcrash, endgame;
var
   playmove, turn, points : integer;
   place1, place2, place3, place4, place5, place6, place7, place8, place9 : char;
   currentplayer, ynagain, lastwinner : char;
begin
     writeln;
     writeln('JRSs Tic-Tac-Toe v1.1');
     writeln('Created by James Skemp - http://jamesrskemp.net/'); {2003.11.09}
     writeln('Version 1.0: 2003.11.09');
     writeln('Version 1.1: 2003.11.09');
     writeln;
     points := 0;
     lastwinner := 'J';
     begingame:
     turn := 0;
     place1 := '1';
     place2 := '2';
     place3 := '3';
     place4 := '4';
     place5 := '5';
     place6 := '6';
     place7 := '7';
     place8 := '8';
     place9 := '9';
     if (lastwinner = 'J') then goto picknumber;
     if (lastwinner = 'X') then goto compmove;
     if ((lastwinner = 'O') and (points &lt;10)) then goto picknumber;
     if ((lastwinner = 'O') and (points &gt;11)) then goto compmove;
     picknumber:
     currentplayer := 'X';
     writeln;
     writeln;
     writeln('     |   |   ');
     writeln('   ',place1,' | ',place2,' | ',place3,' ');
     writeln('     |   |   ');
     writeln('  ---+---+---');
     writeln('     |   |   ');
     writeln('   ',place4,' | ',place5,' | ',place6,' ');
     writeln('     |   |   ');
     writeln('  ---+---+---');
     writeln('     |   |   ');
     writeln('   ',place7,' | ',place8,' | ',place9,' ');
     writeln('     |   |   ');
     writeln;
     writeln('Pick a number that you would like to take (you are ''X''). ');
     readln(playmove);
     checkmove:
     if ((playmove &gt; 9) and (playmove &lt;&gt; 33)) or (playmove &lt; 1) then
      begin
       writeln('Whoops.  That''s an illegal move, try again.');
       writeln;
       goto picknumber;
      end;
     if (playmove = 1) and (place1 = '1') then
      begin
       place1 := 'X';
       goto checkforwin;
      end;
     if (playmove = 2) and (place2 = '2') then
      begin
       place2 := 'X';
       goto checkforwin;
      end;
     if (playmove = 3) and (place3 = '3') then
      begin
       place3 := 'X';
       goto checkforwin;
      end;
     if (playmove = 4) and (place4 = '4') then
      begin
       place4 := 'X';
       goto checkforwin;
      end;
     if (playmove = 5) and (place5 = '5') then
      begin
       place5 := 'X';
       goto checkforwin;
      end;
     if (playmove = 6) and (place6 = '6') then
      begin
       place6 := 'X';
       goto checkforwin;
      end;
     if (playmove = 7) and (place7 = '7') then
      begin
       place7 := 'X';
       goto checkforwin;
      end;
     if (playmove = 8) and (place8 = '8') then
      begin
       place8 := 'X';
       goto checkforwin;
      end;
     if (playmove = 9) and (place9 = '9') then
      begin
       place9 := 'X';
       goto checkforwin;
      end;
     if (playmove = 33) then
      begin
       writeln('Hi James');
       goto playagain;
      end
     else
      goto illegalmove;
     compmove:
     currentplayer := 'O';
     writeln;
     writeln('Computer''s move ');
     {Check for Horizontal win}
     if ((place1 = '1') and (place2 = 'O') and (place3 = 'O')) then begin place1 := 'O'; goto checkforwin; end;
     if ((place1 = 'O') and (place2 = '2') and (place3 = 'O')) then begin place2 := 'O'; goto checkforwin; end;
     if ((place1 = 'O') and (place2 = 'O') and (place3 = '3')) then begin place3 := 'O'; goto checkforwin; end;
     if ((place4 = '4') and (place5 = 'O') and (place6 = 'O')) then begin place4 := 'O'; goto checkforwin; end;
     if ((place4 = 'O') and (place5 = '5') and (place6 = 'O')) then begin place5 := 'O'; goto checkforwin; end;
     if ((place4 = 'O') and (place5 = 'O') and (place6 = '6')) then begin place6 := 'O'; goto checkforwin; end;
     if ((place7 = '7') and (place8 = 'O') and (place9 = 'O')) then begin place7 := 'O'; goto checkforwin; end;
     if ((place7 = 'O') and (place8 = '8') and (place9 = 'O')) then begin place8 := 'O'; goto checkforwin; end;
     if ((place7 = 'O') and (place8 = 'O') and (place9 = '9')) then begin place9 := 'O'; goto checkforwin; end;
     {Check for Vertical win}
     if ((place1 = '1') and (place4 = 'O') and (place7 = 'O')) then begin place1 := 'O'; goto checkforwin; end;
     if ((place1 = 'O') and (place4 = '4') and (place7 = 'O')) then begin place4 := 'O'; goto checkforwin; end;
     if ((place1 = 'O') and (place4 = 'O') and (place7 = '7')) then begin place7 := 'O'; goto checkforwin; end;
     if ((place2 = '2') and (place5 = 'O') and (place8 = 'O')) then begin place2 := 'O'; goto checkforwin; end;
     if ((place2 = 'O') and (place5 = '5') and (place8 = 'O')) then begin place5 := 'O'; goto checkforwin; end;
     if ((place2 = 'O') and (place5 = 'O') and (place8 = '8')) then begin place8 := 'O'; goto checkforwin; end;
     if ((place3 = '3') and (place6 = 'O') and (place9 = 'O')) then begin place3 := 'O'; goto checkforwin; end;
     if ((place3 = 'O') and (place6 = '6') and (place9 = 'O')) then begin place6 := 'O'; goto checkforwin; end;
     if ((place3 = 'O') and (place6 = 'O') and (place9 = '9')) then begin place9 := 'O'; goto checkforwin; end;
     {Check for diagonal win}
     if ((place1 = '1') and (place5 = 'O') and (place9 = 'O')) then begin place1 := 'O'; goto checkforwin; end;
     if ((place1 = 'O') and (place5 = '5') and (place9 = 'O')) then begin place5 := 'O'; goto checkforwin; end;
     if ((place1 = 'O') and (place5 = 'O') and (place9 = '9')) then begin place9 := 'O'; goto checkforwin; end;
     if ((place3 = '3') and (place5 = 'O') and (place7 = 'O')) then begin place3 := 'O'; goto checkforwin; end;
     if ((place3 = 'O') and (place5 = '5') and (place7 = 'O')) then begin place5 := 'O'; goto checkforwin; end;
     if ((place3 = 'O') and (place5 = 'O') and (place7 = '7')) then begin place7 := 'O'; goto checkforwin; end;
     {Check for Horizontal block}
     if ((place1 = '1') and (place2 = 'X') and (place3 = 'X')) then begin place1 := 'O'; goto checkforwin; end;
     if ((place1 = 'X') and (place2 = '2') and (place3 = 'X')) then begin place2 := 'O'; goto checkforwin; end;
     if ((place1 = 'X') and (place2 = 'X') and (place3 = '3')) then begin place3 := 'O'; goto checkforwin; end;
     if ((place4 = '4') and (place5 = 'X') and (place6 = 'X')) then begin place4 := 'O'; goto checkforwin; end;
     if ((place4 = 'X') and (place5 = '5') and (place6 = 'X')) then begin place5 := 'O'; goto checkforwin; end;
     if ((place4 = 'X') and (place5 = 'X') and (place6 = '6')) then begin place6 := 'O'; goto checkforwin; end;
     if ((place7 = '7') and (place8 = 'X') and (place9 = 'X')) then begin place7 := 'O'; goto checkforwin; end;
     if ((place7 = 'X') and (place8 = '8') and (place9 = 'X')) then begin place8 := 'O'; goto checkforwin; end;
     if ((place7 = 'X') and (place8 = 'X') and (place9 = '9')) then begin place9 := 'O'; goto checkforwin; end;
     {Check for Vertical block}
     if ((place1 = '1') and (place4 = 'X') and (place7 = 'X')) then begin place1 := 'O'; goto checkforwin; end;
     if ((place1 = 'X') and (place4 = '4') and (place7 = 'X')) then begin place4 := 'O'; goto checkforwin; end;
     if ((place1 = 'X') and (place4 = 'X') and (place7 = '7')) then begin place7 := 'O'; goto checkforwin; end;
     if ((place2 = '2') and (place5 = 'X') and (place8 = 'X')) then begin place2 := 'O'; goto checkforwin; end;
     if ((place2 = 'X') and (place5 = '5') and (place8 = 'X')) then begin place5 := 'O'; goto checkforwin; end;
     if ((place2 = 'X') and (place5 = 'X') and (place8 = '8')) then begin place8 := 'O'; goto checkforwin; end;
     if ((place3 = '3') and (place6 = 'X') and (place9 = 'X')) then begin place3 := 'O'; goto checkforwin; end;
     if ((place3 = 'X') and (place6 = '6') and (place9 = 'X')) then begin place6 := 'O'; goto checkforwin; end;
     if ((place3 = 'X') and (place6 = 'X') and (place9 = '9')) then begin place9 := 'O'; goto checkforwin; end;
     {Check for diagonal block}
     if ((place1 = '1') and (place5 = 'X') and (place9 = 'X')) then begin place1 := 'O'; goto checkforwin; end;
     if ((place1 = 'X') and (place5 = '5') and (place9 = 'X')) then begin place5 := 'O'; goto checkforwin; end;
     if ((place1 = 'X') and (place5 = 'X') and (place9 = '9')) then begin place9 := 'O'; goto checkforwin; end;
     if ((place3 = '3') and (place5 = 'X') and (place7 = 'X')) then begin place3 := 'O'; goto checkforwin; end;
     if ((place3 = 'X') and (place5 = '5') and (place7 = 'X')) then begin place5 := 'O'; goto checkforwin; end;
     if ((place3 = 'X') and (place5 = 'X') and (place7 = '7')) then begin place7 := 'O'; goto checkforwin; end;
     if (turn = 0) then begin place3 := 'O'; goto checkforwin; end;
     {Check for favorite turn 2 places}
     if ((turn = 2) and (place1 = 'X')) then begin place9 := 'O'; goto checkforwin; end;
     if ((turn = 2) and (place7 = 'X')) then begin place1 := 'O'; goto checkforwin; end;
     if ((turn = 2) and (place9 = 'X')) then begin place7 := 'O'; goto checkforwin; end;
     {Go for place 5 if open}
     if (place5 = '5') then begin place5 := 'O'; goto checkforwin; end;
     {Check for stupid moves}
     {...}

     if (place3 = '3') then begin place3 := 'O'; goto checkforwin; end;
     if (place9 = '9') then begin place9 := 'O'; goto checkforwin; end;
     if (place1 = '1') then begin place1 := 'O'; goto checkforwin; end;
     if (place7 = '7') then begin place7 := 'O'; goto checkforwin; end;
     if (place4 = '4') then begin place4 := 'O'; goto checkforwin; end;
     if (place2 = '2') then begin place2 := 'O'; goto checkforwin; end;
     if (place6 = '6') then begin place6 := 'O'; goto checkforwin; end;
     if (place8 = '8') then begin place8 := 'O'; goto checkforwin; end;

     goto compcrash;

     checkforwin:
      turn := turn + 1;
      if ((place1 = place2) and (place1 = place3)) then goto winner;
      if ((place1 = place4) and (place1 = place7)) then goto winner;
      if ((place1 = place5) and (place1 = place9)) then goto winner;
      if ((place2 = place5) and (place2 = place8)) then goto winner;
      if ((place3 = place5) and (place3 = place7)) then goto winner;
      if ((place3 = place6) and (place3 = place9)) then goto winner;
      if ((place4 = place5) and (place4 = place6)) then goto winner;
      if ((place7 = place8) and (place7 = place9)) then goto winner;

      if turn = 9 then goto nobodywon;
     if currentplayer = 'X' then
      begin
       currentplayer := 'O';
       goto compmove;
      end
     else
      begin
       currentplayer :='X';
       goto picknumber;
      end;

     winner:
      writeln;
      writeln('     |   |   ');
      writeln('   ',place1,' | ',place2,' | ',place3,' ');
      writeln('     |   |   ');
      writeln('  ---+---+---');
      writeln('     |   |   ');
      writeln('   ',place4,' | ',place5,' | ',place6,' ');
      writeln('     |   |   ');
      writeln('  ---+---+---');
      writeln('     |   |   ');
      writeln('   ',place7,' | ',place8,' | ',place9,' ');
      writeln('     |   |   ');
      writeln;
      if currentplayer = 'X' then
       begin
        writeln;
        writeln('You''ve won!  Congrats :)');
        points := points + 1;
        lastwinner := 'X';
        goto playagain;
       end
      else
       begin
        writeln;
        writeln('Sorry :( but you have lost...');
        points := points - 1;
        lastwinner := 'O';
        goto playagain;
       end;

     nobodywon:
      writeln;
      writeln('     |   |   ');
      writeln('   ',place1,' | ',place2,' | ',place3,' ');
      writeln('     |   |   ');
      writeln('  ---+---+---');
      writeln('     |   |   ');
      writeln('   ',place4,' | ',place5,' | ',place6,' ');
      writeln('     |   |   ');
      writeln('  ---+---+---');
      writeln('     |   |   ');
      writeln('   ',place7,' | ',place8,' | ',place9,' ');
      writeln('     |   |   ');
      writeln;
     writeln('Sorry, nobody won this game.');
     points := points + 0;
     lastwinner := lastwinner;
     goto playagain;

     playagain:
     writeln;
     writeln('Would you like to play again? Y or 1 for Yes, N or 0 (zero) for No.');
     read(ynagain);
     if ((ynagain = 'Y') or (ynagain = 'y') or (ynagain = '1')) then goto begingame else goto endgame;

     illegalmove:
     writeln('Sorry, that''s an illegal move.');
     goto picknumber;

     compcrash:
     writeln('Ekk! The computer went crazy and started shooting! You died...');
     points := points - 1;
     goto playagain;

     endgame:
     writeln('Your ending points were: ',points);
     writeln('Press Enter or Return to quit');
     readln;
end.
</code></pre>
