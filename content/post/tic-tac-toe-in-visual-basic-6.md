+++
title = "Tic-Tac-Toe in Visual Basic 6"
summary = "Visual Basic 6 code for a multi-player Tic-Tac-Toe application."
draft = false
comments = true
date = "2010-07-24T12:00:00-05:00"
modified = "2010-07-24T12:06:21-05:00"
slug = "Tic-Tac-Toe-in-Visual-Basic-6"
blogengine = "c5ccd299-86b6-4712-b1e8-e28dee3b7dc9"
categories = ["software"]
tags = ["visual basic"]
+++

<p>Back in December of 2003 I created a Tic-Tac-Toe application in Visual Basic 6.</p>
<p>Below is the code from MainWin.frm, which should be sufficient to create the application.</p>
<p>This code is covered by a <a rel="external" href="http://creativecommons.org/licenses/by-nc/3.0/">Creative Commons Attribution-NonCommercial 3.0 license</a>.</p>
<pre class="code"><code class="vb">VERSION 5.00
Begin VB.Form Form1 
   Caption         =   "Tic-Tac-Toe"
   ClientHeight    =   3255
   ClientLeft      =   4410
   ClientTop       =   3255
   ClientWidth     =   4080
   LinkTopic       =   "Form1"
   ScaleHeight     =   3255
   ScaleWidth      =   4080
   Begin VB.CommandButton AboutThis 
      Caption         =   "&amp;About"
      Height          =   495
      Left            =   2760
      TabIndex        =   12
      Top             =   2760
      Width           =   1215
   End
   Begin VB.CommandButton Command10 
      Caption         =   "&amp;Clear/Restart"
      Height          =   495
      Left            =   1440
      TabIndex        =   9
      Top             =   2760
      Width           =   1215
   End
   Begin VB.CommandButton Command9 
      Caption         =   "Empty"
      Height          =   495
      Left            =   2760
      TabIndex        =   8
      Top             =   2040
      Width           =   1215
   End
   Begin VB.CommandButton Command8 
      Caption         =   "Empty"
      Height          =   495
      Left            =   1440
      TabIndex        =   7
      Top             =   2040
      Width           =   1215
   End
   Begin VB.CommandButton Command7 
      Caption         =   "Empty"
      Height          =   495
      Left            =   120
      TabIndex        =   6
      Top             =   2040
      Width           =   1215
   End
   Begin VB.CommandButton Command6 
      Caption         =   "Empty"
      Height          =   495
      Left            =   2760
      TabIndex        =   5
      Top             =   1440
      Width           =   1215
   End
   Begin VB.CommandButton Command5 
      Caption         =   "Empty"
      Height          =   495
      Left            =   1440
      TabIndex        =   4
      Top             =   1440
      Width           =   1215
   End
   Begin VB.CommandButton Command4 
      Caption         =   "Empty"
      Height          =   495
      Left            =   120
      TabIndex        =   3
      Top             =   1440
      Width           =   1215
   End
   Begin VB.CommandButton Command3 
      Caption         =   "Empty"
      Height          =   495
      Left            =   2760
      TabIndex        =   2
      Top             =   840
      Width           =   1215
   End
   Begin VB.CommandButton Command2 
      Caption         =   "Empty"
      Height          =   495
      Left            =   1440
      TabIndex        =   1
      Top             =   840
      Width           =   1215
   End
   Begin VB.CommandButton Command1 
      Caption         =   "Empty"
      Height          =   495
      Left            =   120
      TabIndex        =   0
      Top             =   840
      Width           =   1215
   End
   Begin VB.Label Label2 
      Caption         =   "2) Press 'Clear/Restart' to clear the board."
      Height          =   255
      Left            =   120
      TabIndex        =   11
      Top             =   360
      Width           =   3855
   End
   Begin VB.Label Label1 
      Caption         =   "1) Click once for an 'X', twice for an 'O'."
      Height          =   255
      Left            =   120
      TabIndex        =   10
      Top             =   120
      Width           =   3855
   End
End
Attribute VB_Name = "Form1"
Attribute VB_GlobalNameSpace = False
Attribute VB_Creatable = False
Attribute VB_PredeclaredId = True
Attribute VB_Exposed = False
Private Sub AboutThis_Click()
 MsgBox "Copyright 2003 James Skemp - http://jamesrskemp.net/", vbOKOnly, About
End Sub

Private Sub Command1_Click()
 If Command1.Caption = "Empty" Then
  Command1.Caption = "X"
 ElseIf Command1.Caption = "X" Then
  Command1.Caption = "O"
 Else: Command1.Caption = "Empty"
 End If
End Sub


Private Sub Command10_Click()
 Command1.Caption = "Empty"
 Command2.Caption = "Empty"
 Command3.Caption = "Empty"
 Command4.Caption = "Empty"
 Command5.Caption = "Empty"
 Command6.Caption = "Empty"
 Command7.Caption = "Empty"
 Command8.Caption = "Empty"
 Command9.Caption = "Empty"
End Sub

Private Sub Command11_Click()

End Sub

Private Sub Command2_Click()
 If Command2.Caption = "Empty" Then
  Command2.Caption = "X"
 ElseIf Command2.Caption = "X" Then
  Command2.Caption = "O"
 Else: Command2.Caption = "Empty"
 End If

End Sub

Private Sub Command3_Click()
 If Command3.Caption = "Empty" Then
  Command3.Caption = "X"
 ElseIf Command3.Caption = "X" Then
  Command3.Caption = "O"
 Else: Command3.Caption = "Empty"
 End If

End Sub

Private Sub Command4_Click()
 If Command4.Caption = "Empty" Then
  Command4.Caption = "X"
 ElseIf Command4.Caption = "X" Then
  Command4.Caption = "O"
 Else: Command4.Caption = "Empty"
 End If

End Sub

Private Sub Command5_Click()
 If Command5.Caption = "Empty" Then
  Command5.Caption = "X"
 ElseIf Command5.Caption = "X" Then
  Command5.Caption = "O"
 Else: Command5.Caption = "Empty"
 End If

End Sub

Private Sub Command6_Click()
 If Command6.Caption = "Empty" Then
  Command6.Caption = "X"
 ElseIf Command6.Caption = "X" Then
  Command6.Caption = "O"
 Else: Command6.Caption = "Empty"
 End If

End Sub

Private Sub Command7_Click()
 If Command7.Caption = "Empty" Then
  Command7.Caption = "X"
 ElseIf Command7.Caption = "X" Then
  Command7.Caption = "O"
 Else: Command7.Caption = "Empty"
 End If

End Sub

Private Sub Command8_Click()
 If Command8.Caption = "Empty" Then
  Command8.Caption = "X"
 ElseIf Command8.Caption = "X" Then
  Command8.Caption = "O"
 Else: Command8.Caption = "Empty"
 End If

End Sub

Private Sub Command9_Click()
 If Command9.Caption = "Empty" Then
  Command9.Caption = "X"
 ElseIf Command9.Caption = "X" Then
  Command9.Caption = "O"
 Else: Command9.Caption = "Empty"
 End If

End Sub

</code></pre>
<p>Honestly, I like <a href="http://strivinglife.com/words/post/Pascal-Programming-JRSs-Tic-Tac-Toe.aspx">the one I did in Pascal</a> much better, since the computer is fairly good.</p>
