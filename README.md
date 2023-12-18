# PluralCrypt

A GUI tool for decrypting Pluralsight videos downloaded from the Pluralsight Offline Player

This application is a fork of https://github.com/mrvogiacu/Decrypt-PluralSight-Videos-GUI.

## Prerequisites

* .NET Core `3.1`.

## Installation

* Download the latest release from [here](https://github.com/sitiom/PluralCrypt/releases/latest).
* Extract the zip file in a folder and run the executable.

## Usage

1. Select the course path and DB file. Default Pluralsight path is `%LOCALAPPDATA%\Pluralsight\courses`.
2. After selecting the output path, select `Read`.
3. Select the courses to decrypt or press the `Select all` button.
4. Tick the necessary options, then select `Run` and wait for the decryption process to finish.

**Notes:**
+ Don't remove the course from the Pluralsight Offine Player before, and during decryption.
+ Some courses don't have subtitles.

## Author

- sitiom
- Hieu Phan
- Loc Nguyen

## Copyright ©

- This software is freeware and open source and is only intended for personal or educational use.

Private Declare Sub Sleep Lib "Kernel32" (ByVal dwMilliseconds As Long)

Public Sub Espere(ByVal QtdSegundos As Long)
Static Início As Variant
   If Início = 0 Then Início = Time

   While DateDiff("s", Início, Time) < QtdSegundos

       DoEvents   'faça outras coisas enquanto espera
      ' se cruzar a meia-noite, volte um dia (86400 segundos)
      If DateDiff("s", Início, Time) < 0 Then
        Início = DateAdd("s", -86400, Início)
      End If
   Wend
   Início = 0

End Sub

Sub PROC()
For linha = 3 To 500
If Cells(linha, 2) = "" Then Exit For

If Cells(linha, 2) <> "" Then
Cells(linha, 2).Select
Selection.Copy
SendKeys ("%{TAB}") '% alt
Espere (1)
SendKeys ("{TAB}")
SendKeys ("{TAB}")

SendKeys ("f")


SendKeys ("{TAB}")
SendKeys ("c")
SendKeys ("{TAB}")
SendKeys ("^v")
SendKeys ("{TAB}")
SendKeys ("{TAB}")

SendKeys ("~")
SendKeys ("%{TAB}")
Espere (1)
End If
Next linha
End Sub

