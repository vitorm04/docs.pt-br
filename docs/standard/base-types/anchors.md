---
title: "Âncoras em expressões regulares"
description: "Âncoras em expressões regulares"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 96dff1be-3005-4ba5-af1b-323182a26085
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: ef2a63115f1efbe2418c348a3379fe7dd2face86

---

# <a name="anchors-in-regular-expressions"></a>Âncoras em expressões regulares

Âncoras ou asserções atômicas de largura zero, especificam uma posição na cadeia de caracteres em que uma correspondência deve ocorrer. Quando você usa uma âncora na sua expressão de pesquisa, o mecanismo de expressões regulares não avança pela cadeia de caracteres ou consome caracteres, ele procura uma correspondência apenas na posição especificada. Por exemplo, **^** Especifica que a correspondência deve começar no início de uma linha ou cadeia de caracteres. Portanto, a expressão regular `^http:` corresponde a "http:" apenas quando ele ocorre no início de uma linha. A tabela a seguir lista as âncoras com suporte pelas expressões regulares no .NET. 

Âncora | Descrição
------ | ----------- 
**^** | A correspondência deve ocorrer no início da cadeia de caracteres ou da linha.
**$** | A correspondência deve ocorrer no final da cadeia de caracteres ou linha ou antes de \n no final da linha ou da cadeia de caracteres.
**\A** | A correspondência deve ocorrer no início da cadeia de caracteres apenas (sem suporte a multilinha)
**\Z** | A correspondência deve ocorrer no final da cadeia de caracteres ou antes de \n no final da cadeia de caracteres.
**\z** | A correspondência deve ocorrer apenas no final da cadeia de caracteres. 
**\G** | A correspondência deve começar na posição em que a correspondência anterior foi encerrada.
**\b** | A correspondência deve ocorrer em um limite de palavra.
**\B** | A correspondência não deve ocorrer em um limite de palavra.
 
## <a name="start-of-string-or-line-"></a>Início da Cadeia de Caracteres ou Linha: ^

A âncora **^** especifica que o seguinte padrão deve começar na posição do primeiro caractere da cadeia de caracteres. Se você usar **^** com a opção [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) (consulte [Opções de expressões regulares](options.md)), a correspondência deverá ocorrer no início de cada linha.

O exemplo a seguir usa a âncora **^** em uma expressão regular que extrai informações sobre os anos durante os quais algumas equipes de profissionais de beisebol existiram. O exemplo chama duas sobrecargas do método `Regex.Matches`: 

* A chamada para a sobrecarga [Matches(String, String)](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String)) localiza apenas a primeira subcadeia de caracteres na cadeia de caracteres de entrada que corresponde ao padrão de expressão regular. 

* A chamada para a sobrecarga [Matches(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) com o parâmetro de opções definido como [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) localiza todas as cinco subcadeias de caracteres.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      int startPos = 0, endPos = 70;
      string input = "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957\n" +
                     "Chicago Cubs, National League, 1903-present\n" + 
                     "Detroit Tigers, American League, 1901-present\n" + 
                     "New York Giants, National League, 1885-1957\n" +  
                     "Washington Senators, American League, 1901-1960\n";   
      string pattern = @"^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+";
      Match match;

      if (input.Substring(startPos, endPos).Contains(",")) {
         match = Regex.Match(input, pattern);
         while (match.Success) {
            Console.Write("The {0} played in the {1} in", 
                              match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);

            Console.WriteLine(".");
            startPos = match.Index + match.Length;
            endPos = startPos + 70 <= input.Length ? 70 : input.Length - startPos;
            if (! input.Substring(startPos, endPos).Contains(",")) break;
            match = match.NextMatch();
         }
         Console.WriteLine();
      }

      if (input.Substring(startPos, endPos).Contains(",")) {
         match = Regex.Match(input, pattern, RegexOptions.Multiline);
         while (match.Success) {
            Console.Write("The {0} played in the {1} in", 
                              match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);

            Console.WriteLine(".");
            startPos = match.Index + match.Length;
            endPos = startPos + 70 <= input.Length ? 70 : input.Length - startPos;
            if (! input.Substring(startPos, endPos).Contains(",")) break;
            match = match.NextMatch();
         }
         Console.WriteLine();
      }
   }
}
// The example displays the following output:
//    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
//    
//    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
//    The Chicago Cubs played in the National League in 1903-present.
//    The Detroit Tigers played in the American League in 1901-present.
//    The New York Giants played in the National League in 1885-1957.
//    The Washington Senators played in the American League in 1901-1960.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim startPos As Integer = 0
      Dim endPos As Integer = 70
      Dim input As String = "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957" + vbCrLf + _
                            "Chicago Cubs, National League, 1903-present" + vbCrLf + _
                            "Detroit Tigers, American League, 1901-present" + vbCrLf + _
                            "New York Giants, National League, 1885-1957" + vbCrLf + _
                            "Washington Senators, American League, 1901-1960" + vbCrLf  

      Dim pattern As String = "^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+"
      Dim match As Match

      ' Provide minimal validation in the event the input is invalid.
      If input.Substring(startPos, endPos).Contains(",") Then
         match = Regex.Match(input, pattern)
         Do While match.Success
            Console.Write("The {0} played in the {1} in", _
                              match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
            startPos = match.Index + match.Length 
            endPos = CInt(IIf(startPos + 70 <= input.Length, 70, input.Length - startPos))
            If Not input.Substring(startPos, endPos).Contains(",") Then Exit Do
            match = match.NextMatch()            
         Loop
         Console.WriteLine()                               
      End If      

      startPos = 0
      endPos = 70
      If input.Substring(startPos, endPos).Contains(",") Then
         match = Regex.Match(input, pattern, RegexOptions.Multiline)
         Do While match.Success
            Console.Write("The {0} played in the {1} in", _
                              match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
            startPos = match.Index + match.Length 
            endPos = CInt(IIf(startPos + 70 <= input.Length, 70, input.Length - startPos))
            If Not input.Substring(startPos, endPos).Contains(",") Then Exit Do
            match = match.NextMatch()            
         Loop
         Console.WriteLine()                               
      End If      


'       For Each match As Match in Regex.Matches(input, pattern, RegexOptions.Multiline)
'          Console.Write("The {0} played in the {1} in", _
'                            match.Groups(1).Value, match.Groups(4).Value)
'          For Each capture As Capture In match.Groups(5).Captures
'             Console.Write(capture.Value)
'          Next
'          Console.WriteLine(".")
'       Next
   End Sub
End Module
' The example displays the following output:
'    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
'    
'    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
'    The Chicago Cubs played in the National League in 1903-present.
'    The Detroit Tigers played in the American League in 1901-present.
'    The New York Giants played in the National League in 1885-1957.
'    The Washington Senators played in the American League in 1901-1960.
```

O padrão de expressão regular `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+` é definido conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | ----------- 
`^` | Começa a correspondência no início da cadeia de caracteres de entrada (ou o início da linha se o método for chamado com a opção `RegexOptions.Multiline`).
`((\w+(\s?)){2,}` | Corresponde a um ou mais caracteres de palavra seguidos por zero ou um espaço exatamente duas vezes. Este é o primeiro grupo de captura. Essa expressão também define um segundo e um terceiro grupos de captura: o segundo consiste na palavra capturada e o terceiro consiste nos espaços capturados. 
`,\s` | Corresponde a uma vírgula seguida por um caractere de espaço em branco.
`(\w+\s\w+)` | Corresponde a um ou mais caracteres de palavra seguidos por um espaço, seguido por um ou mais caracteres de palavra. Este é o quarto grupo de captura.
`,` | Corresponde a uma vírgula.
`\s\d{4}` | Corresponde a um espaço seguido por quatro dígitos decimais.
`(-(\d{4}`&#124;`present))?` |  Corresponde a zero ou uma ocorrência de um hífen seguido por quatro dígitos decimais ou a cadeia de caracteres "present". Este é o sexto grupo de captura. Ele também inclui um sétimo grupo de captura. 
`,?` | Corresponde a zero ou uma ocorrência de uma vírgula.
`(\s\d{4}(-(\d{4}`&#124;`present))?,?)+` | Corresponde a uma ou mais ocorrências do seguinte: um espaço, quatro dígitos decimais, zero ou uma ocorrência de um hífen seguido por quatro dígitos decimais ou a cadeia de caracteres "present" e zero ou uma vírgula. Este é o quinto grupo de captura.
 
## <a name="end-of-string-or-line-"></a>Final da Cadeia de Caracteres ou da Linha: $

A âncora **$** especifica que o padrão anterior deve ocorrer no final da cadeia de caracteres de entrada ou antes de \n no final da cadeia de caracteres de entrada. 

Se você usar **$** com a opção [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline), a correspondência também pode ocorrer no final de uma linha. Observe que **$** corresponde a **\n**, mas não corresponde a **\r\n** (a combinação de caracteres de nova linha e de retorno de carro ou CR/LF). De acordo com a combinação de caracteres CR/LF, inclua **\r?$** no padrão de expressão regular.

O exemplo a seguir adiciona a âncora **$** ao padrão de expressão regular usada no exemplo na seção anterior "Início da cadeia de caracteres ou linha". Quando usado com a cadeia de caracteres de entrada original, que inclui cinco linhas de texto, o método [Regex.Matches(String, String)](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String)) não pode localizar uma correspondência, pois o final da primeira linha não corresponde ao padrão **$**. Quando a cadeia de caracteres de entrada original é dividida em uma matriz de cadeia de caracteres, o método `Regex.Matches(String, String)` obtém sucesso na correspondência de cada uma das cinco linhas. Quando o método [Regex.Matches(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) for chamado com o parâmetro *options* definido como `RegexOptions.Multiline`, nenhuma correspondência será encontrada porque o padrão de expressão regular não considera o elemento de retorno de carro (\u+000D). No entanto, quando o padrão de expressão regular é modificado substituindo **$** por **\r?$**, chamar o método `Regex.Matches(String, String, RegexOptions)` com o parâmetro *options* definido como `RegexOptions.Multiline` novamente encontra cinco correspondências.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      int startPos = 0, endPos = 70;
      string cr = Environment.NewLine;
      string input = "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957" + cr +
                     "Chicago Cubs, National League, 1903-present" + cr + 
                     "Detroit Tigers, American League, 1901-present" + cr + 
                     "New York Giants, National League, 1885-1957" + cr +  
                     "Washington Senators, American League, 1901-1960" + cr;   
      Match match;

      string basePattern = @"^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+";
      string pattern = basePattern + "$";
      Console.WriteLine("Attempting to match the entire input string:");
      if (input.Substring(startPos, endPos).Contains(",")) {
         match = Regex.Match(input, pattern);
         while (match.Success) {
            Console.Write("The {0} played in the {1} in", 
                              match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);

            Console.WriteLine(".");
            startPos = match.Index + match.Length;
            endPos = startPos + 70 <= input.Length ? 70 : input.Length - startPos;
            if (! input.Substring(startPos, endPos).Contains(",")) break;
            match = match.NextMatch();
         }
         Console.WriteLine();
      }

      string[] teams = input.Split(new String[] { cr }, StringSplitOptions.RemoveEmptyEntries);
      Console.WriteLine("Attempting to match each element in a string array:");
      foreach (string team in teams)
      {
         if (team.Length > 70) continue;

         match = Regex.Match(team, pattern);
         if (match.Success)
         {
            Console.Write("The {0} played in the {1} in", 
                          match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);
            Console.WriteLine(".");
         }
      }
      Console.WriteLine();

      startPos = 0;
      endPos = 70;
      Console.WriteLine("Attempting to match each line of an input string with '$':");
      if (input.Substring(startPos, endPos).Contains(",")) {
         match = Regex.Match(input, pattern, RegexOptions.Multiline);
         while (match.Success) {
            Console.Write("The {0} played in the {1} in", 
                              match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);

            Console.WriteLine(".");
            startPos = match.Index + match.Length;
            endPos = startPos + 70 <= input.Length ? 70 : input.Length - startPos;
            if (! input.Substring(startPos, endPos).Contains(",")) break;
            match = match.NextMatch();
         }
         Console.WriteLine();
      }

      startPos = 0;
      endPos = 70;
      pattern = basePattern + "\r?$"; 
      Console.WriteLine(@"Attempting to match each line of an input string with '\r?$':");
      if (input.Substring(startPos, endPos).Contains(",")) {
         match = Regex.Match(input, pattern, RegexOptions.Multiline);
         while (match.Success) {
            Console.Write("The {0} played in the {1} in", 
                              match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);

            Console.WriteLine(".");
            startPos = match.Index + match.Length;
            endPos = startPos + 70 <= input.Length ? 70 : input.Length - startPos;
            if (! input.Substring(startPos, endPos).Contains(",")) break;
            match = match.NextMatch();
         }
         Console.WriteLine();
      }
   }
}
// The example displays the following output:
//    Attempting to match the entire input string:
//    
//    Attempting to match each element in a string array:
//    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
//    The Chicago Cubs played in the National League in 1903-present.
//    The Detroit Tigers played in the American League in 1901-present.
//    The New York Giants played in the National League in 1885-1957.
//    The Washington Senators played in the American League in 1901-1960.
//    
//    Attempting to match each line of an input string with '$':
//    
//    Attempting to match each line of an input string with '\r+$':
//    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
//    The Chicago Cubs played in the National League in 1903-present.
//    The Detroit Tigers played in the American League in 1901-present.
//    The New York Giants played in the National League in 1885-1957.
//    The Washington Senators played in the American League in 1901-1960.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim startPos As Integer = 0
      Dim endPos As Integer = 70
      Dim input As String = "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957" + vbCrLf + _
                            "Chicago Cubs, National League, 1903-present" + vbCrLf + _
                            "Detroit Tigers, American League, 1901-present" + vbCrLf + _
                            "New York Giants, National League, 1885-1957" + vbCrLf + _
                            "Washington Senators, American League, 1901-1960" + vbCrLf  

      Dim basePattern As String = "^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+"
      Dim match As Match

      Dim pattern As String = basePattern + "$"
      Console.WriteLine("Attempting to match the entire input string:")
      ' Provide minimal validation in the event the input is invalid.
      If input.Substring(startPos, endPos).Contains(",") Then
         match = Regex.Match(input, pattern)
         Do While match.Success
            Console.Write("The {0} played in the {1} in", _
                              match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
            startPos = match.Index + match.Length 
            endPos = CInt(IIf(startPos + 70 <= input.Length, 70, input.Length - startPos))
            If Not input.Substring(startPos, endPos).Contains(",") Then Exit Do
            match = match.NextMatch()            
         Loop
         Console.WriteLine()                               
      End If      

      Dim teams() As String = input.Split(New String() { vbCrLf }, StringSplitOptions.RemoveEmptyEntries)
      Console.WriteLine("Attempting to match each element in a string array:")
      For Each team As String In teams
         If team.Length > 70 Then Continue For
         match = Regex.Match(team, pattern)
         If match.Success Then
            Console.Write("The {0} played in the {1} in", _
                           match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
         End If
      Next
      Console.WriteLine()

      startPos = 0
      endPos = 70
      Console.WriteLine("Attempting to match each line of an input string with '$':")
      ' Provide minimal validation in the event the input is invalid.
      If input.Substring(startPos, endPos).Contains(",") Then
         match = Regex.Match(input, pattern, RegexOptions.Multiline)
         Do While match.Success
            Console.Write("The {0} played in the {1} in", _
                              match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
            startPos = match.Index + match.Length 
            endPos = CInt(IIf(startPos + 70 <= input.Length, 70, input.Length - startPos))
            If Not input.Substring(startPos, endPos).Contains(",") Then Exit Do
            match = match.NextMatch()            
         Loop
         Console.WriteLine()                               
      End If      


      startPos = 0
      endPos = 70
      pattern = basePattern + "\r?$" 
      Console.WriteLine("Attempting to match each line of an input string with '\r?$':")
      ' Provide minimal validation in the event the input is invalid.
      If input.Substring(startPos, endPos).Contains(",") Then
         match = Regex.Match(input, pattern, RegexOptions.Multiline)
         Do While match.Success
            Console.Write("The {0} played in the {1} in", _
                              match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
            startPos = match.Index + match.Length 
            endPos = CInt(IIf(startPos + 70 <= input.Length, 70, input.Length - startPos))
            If Not input.Substring(startPos, endPos).Contains(",") Then Exit Do
            match = match.NextMatch()            
         Loop
         Console.WriteLine()                               
      End If      
   End Sub
End Module
' The example displays the following output:
'    Attempting to match the entire input string:
'    
'    Attempting to match each element in a string array:
'    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
'    The Chicago Cubs played in the National League in 1903-present.
'    The Detroit Tigers played in the American League in 1901-present.
'    The New York Giants played in the National League in 1885-1957.
'    The Washington Senators played in the American League in 1901-1960.
'    
'    Attempting to match each line of an input string with '$':
'    
'    Attempting to match each line of an input string with '\r+$':
'    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
'    The Chicago Cubs played in the National League in 1903-present.
'    The Detroit Tigers played in the American League in 1901-present.
'    The New York Giants played in the National League in 1885-1957.
'    The Washington Senators played in the American League in 1901-1960.
```

## <a name="start-of-string-only-a"></a>Apenas Início da Cadeia de Caracteres: \A

A âncora **\A** especifica que uma correspondência deve ocorrer no início da cadeia de caracteres de entrada. Ela é idêntica à âncora **^**, exceto que **\A** ignora a opção [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline). Portanto, ela pode corresponder apenas ao início da primeira linha em uma cadeia de caracteres de entrada multilinhas.

O exemplo a seguir é semelhante aos exemplos das âncoras **^** e **$**. Ele usa a âncora **\A** em uma expressão regular que extrai informações sobre os anos durante os quais algumas equipes de profissionais de beisebol existiram. A cadeia de caracteres de entrada inclui cinco linhas. A chamada para o método [Regex.Matches(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) localiza apenas a primeira subcadeia de caracteres na cadeia de caracteres de entrada que corresponde ao padrão de expressão regular. Como o exemplo mostra, a opção `Multiline` não tem efeito.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      int startPos = 0, endPos = 70;
      string input = "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957\n" +
                     "Chicago Cubs, National League, 1903-present\n" + 
                     "Detroit Tigers, American League, 1901-present\n" + 
                     "New York Giants, National League, 1885-1957\n" +  
                     "Washington Senators, American League, 1901-1960\n";   

      string pattern = @"\A((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+";
      Match match;

      if (input.Substring(startPos, endPos).Contains(",")) {
         match = Regex.Match(input, pattern, RegexOptions.Multiline);
         while (match.Success) {
            Console.Write("The {0} played in the {1} in", 
                              match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);

            Console.WriteLine(".");
            startPos = match.Index + match.Length;
            endPos = startPos + 70 <= input.Length ? 70 : input.Length - startPos;
            if (! input.Substring(startPos, endPos).Contains(",")) break;
            match = match.NextMatch();
         }
         Console.WriteLine();
      }
   }
}
// The example displays the following output:
//    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim startPos As Integer = 0
      Dim endPos As Integer = 70
      Dim input As String = "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957" + vbCrLf + _
                            "Chicago Cubs, National League, 1903-present" + vbCrLf + _
                            "Detroit Tigers, American League, 1901-present" + vbCrLf + _
                            "New York Giants, National League, 1885-1957" + vbCrLf + _
                            "Washington Senators, American League, 1901-1960" + vbCrLf  

      Dim pattern As String = "\A((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+"
      Dim match As Match

      ' Provide minimal validation in the event the input is invalid.
      If input.Substring(startPos, endPos).Contains(",") Then
         match = Regex.Match(input, pattern, RegexOptions.Multiline)
         Do While match.Success
            Console.Write("The {0} played in the {1} in", _
                              match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
            startPos = match.Index + match.Length 
            endPos = CInt(IIf(startPos + 70 <= input.Length, 70, input.Length - startPos))
            If Not input.Substring(startPos, endPos).Contains(",") Then Exit Do
            match = match.NextMatch()            
         Loop
         Console.WriteLine()                               
      End If      
   End Sub   
End Module
' The example displays the following output:
'    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
```

## <a name="end-of-string-or-before-ending-newline-z"></a>Final da Cadeia de Caracteres ou Antes de Terminar Nova Linha: \ Z

A âncora **\Z** especifica que a correspondência deve ocorrer no final da cadeia de caracteres de entrada ou antes de **\n** no final da cadeia de caracteres de entrada. Ela é idêntica à âncora **$**, exceto que **\Z** ignora a opção [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline). Portanto, em uma cadeia de caracteres multilinhas, ela pode corresponder apenas ao final da última linha ou à última linha antes de **\n**.

Observe que **\Z** corresponde a **\n** mas não corresponde a **\r\n** (a combinação de caracteres CR/LF). Para corresponder a CR/LF, inclua **\r?\Z** no padrão da expressão regular.

O exemplo a seguir usa a âncora **\Z** em uma expressão regular semelhante ao exemplo na seção “Início da Cadeia de Caracteres ou Linha” anterior, que extrai informações sobre os anos durante os quais algumas equipes de profissionais de beisebol existiram. A subexpressão `\r?\Z` na expressão regular `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z` corresponde ao final de uma cadeia de caracteres e também corresponde a uma cadeia de caracteres que termina com **\n** ou **\r\n**. Como resultado, cada elemento da matriz corresponde ao padrão da expressão regular.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957",  
                          "Chicago Cubs, National League, 1903-present" + Environment.NewLine, 
                          "Detroit Tigers, American League, 1901-present" + Regex.Unescape(@"\n"), 
                          "New York Giants, National League, 1885-1957", 
                          "Washington Senators, American League, 1901-1960" + Environment.NewLine}; 
      string pattern = @"^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z";

      foreach (string input in inputs)
      {
         if (input.Length > 70 || ! input.Contains(",")) continue;

         Console.WriteLine(Regex.Escape(input));
         Match match = Regex.Match(input, pattern);
         if (match.Success)
            Console.WriteLine("   Match succeeded.");
         else
            Console.WriteLine("   Match failed.");
      }   
   }
}
// The example displays the following output:
//    Brooklyn\ Dodgers,\ National\ League,\ 1911,\ 1912,\ 1932-1957
//       Match succeeded.
//    Chicago\ Cubs,\ National\ League,\ 1903-present\r\n
//       Match succeeded.
//    Detroit\ Tigers,\ American\ League,\ 1901-present\n
//       Match succeeded.
//    New\ York\ Giants,\ National\ League,\ 1885-1957
//       Match succeeded.
//    Washington\ Senators,\ American\ League,\ 1901-1960\r\n
//       Match succeeded.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957",  _
                            "Chicago Cubs, National League, 1903-present" + vbCrLf, _
                            "Detroit Tigers, American League, 1901-present" + vbLf, _
                            "New York Giants, National League, 1885-1957", _
                            "Washington Senators, American League, 1901-1960" + vbCrLf }  
      Dim pattern As String = "^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z"

      For Each input As String In inputs
         If input.Length > 70 Or Not input.Contains(",") Then Continue For

         Console.WriteLine(Regex.Escape(input))
         Dim match As Match = Regex.Match(input, pattern)
         If match.Success Then
            Console.WriteLine("   Match succeeded.")
         Else
            Console.WriteLine("   Match failed.")
         End If
      Next   
   End Sub
End Module
' The example displays the following output:
'    Brooklyn\ Dodgers,\ National\ League,\ 1911,\ 1912,\ 1932-1957
'       Match succeeded.
'    Chicago\ Cubs,\ National\ League,\ 1903-present\r\n
'       Match succeeded.
'    Detroit\ Tigers,\ American\ League,\ 1901-present\n
'       Match succeeded.
'    New\ York\ Giants,\ National\ League,\ 1885-1957
'       Match succeeded.
'    Washington\ Senators,\ American\ League,\ 1901-1960\r\n
'       Match succeeded.
```

## <a name="end-of-string-only-z"></a>Apenas Final da Cadeia de Caracteres: \ z

A âncora **\z** especifica que uma correspondência deve ocorrer no final da cadeia de caracteres de entrada. Como o elemento de linguagem **$**, **\z** ignora a opção [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline). Diferentemente do elemento de linguagem **\Z**, **\z** não corresponde ao caractere **\n** no final de uma cadeia de caracteres. Portanto, ele pode corresponder somente à última linha da cadeia de caracteres de entrada.

O exemplo a seguir usa a âncora **\z** em uma expressão regular que é de outro modo idêntica ao exemplo na seção anterior, que extrai informações sobre os anos durante os quais algumas equipes de profissionais de beisebol existiram. O exemplo tenta corresponder cada um dos cinco elementos em uma matriz de cadeia de caracteres com um padrão de expressão regular `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z`. Duas das cadeias de caracteres terminam com os caracteres de alimentação de linha e retorno de carro, uma termina com um caractere de alimentação de linha e duas terminam sem um caractere de retorno de carro nem um caractere de alimentação de linha. Como a saída mostra, apenas as cadeias de caracteres sem um caractere de retorno de carro ou de alimentação de linha correspondem ao padrão. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957", 
                          "Chicago Cubs, National League, 1903-present" + Environment.NewLine,
                          "Detroit Tigers, American League, 1901-present\\r",
                          "New York Giants, National League, 1885-1957",
                          "Washington Senators, American League, 1901-1960" + Environment.NewLine };  
      string pattern = @"^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z";

      foreach (string input in inputs)
      {
         if (input.Length > 70 || ! input.Contains(",")) continue;

         Console.WriteLine(Regex.Escape(input));
         Match match = Regex.Match(input, pattern);
         if (match.Success)
            Console.WriteLine("   Match succeeded.");
         else
            Console.WriteLine("   Match failed.");
      }   
   }
}
// The example displays the following output:
//    Brooklyn\ Dodgers,\ National\ League,\ 1911,\ 1912,\ 1932-1957
//       Match succeeded.
//    Chicago\ Cubs,\ National\ League,\ 1903-present\r\n
//       Match failed.
//    Detroit\ Tigers,\ American\ League,\ 1901-present\n
//       Match failed.
//    New\ York\ Giants,\ National\ League,\ 1885-1957
//       Match succeeded.
//    Washington\ Senators,\ American\ League,\ 1901-1960\r\n
//       Match failed.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957",  _
                            "Chicago Cubs, National League, 1903-present" + vbCrLf, _
                            "Detroit Tigers, American League, 1901-present" + vbLf, _
                            "New York Giants, National League, 1885-1957", _
                            "Washington Senators, American League, 1901-1960" + vbCrLf }  
      Dim pattern As String = "^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z"

      For Each input As String In inputs
         If input.Length > 70 Or Not input.Contains(",") Then Continue For

         Console.WriteLine(Regex.Escape(input))
         Dim match As Match = Regex.Match(input, pattern)
         If match.Success Then
            Console.WriteLine("   Match succeeded.")
         Else
            Console.WriteLine("   Match failed.")
         End If
      Next   
   End Sub
End Module
' The example displays the following output:
'    Brooklyn\ Dodgers,\ National\ League,\ 1911,\ 1912,\ 1932-1957
'       Match succeeded.
'    Chicago\ Cubs,\ National\ League,\ 1903-present\r\n
'       Match failed.
'    Detroit\ Tigers,\ American\ League,\ 1901-present\n
'       Match failed.
'    New\ York\ Giants,\ National\ League,\ 1885-1957
'       Match succeeded.
'    Washington\ Senators,\ American\ League,\ 1901-1960\r\n
'       Match failed.
```

## <a name="contiguous-matches-g"></a>Correspondências Contíguas: \ G

A âncora **\G** especifica que uma correspondência deve ocorrer no ponto em que a correspondência anterior foi encerrada. Quando você usa essa âncora com o método [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) ou [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch), ela garante que todas as correspondências são contíguas. 

O exemplo a seguir usa uma expressão regular para extrair os nomes de espécies de roedores de uma cadeia de caracteres delimitada por vírgulas. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "capybara,squirrel,chipmunk,porcupine,gopher," + 
                     "beaver,groundhog,hamster,guinea pig,gerbil," + 
                     "chinchilla,prairie dog,mouse,rat";
      string pattern = @"\G(\w+\s?\w*),?";
      Match match = Regex.Match(input, pattern);
      while (match.Success) 
      {
         Console.WriteLine(match.Groups[1].Value);
         match = match.NextMatch();
      } 
   }
}
// The example displays the following output:
//       capybara
//       squirrel
//       chipmunk
//       porcupine
//       gopher
//       beaver
//       groundhog
//       hamster
//       guinea pig
//       gerbil
//       chinchilla
//       prairie dog
//       mouse
//       rat
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "capybara,squirrel,chipmunk,porcupine,gopher," + _
                            "beaver,groundhog,hamster,guinea pig,gerbil," + _
                            "chinchilla,prairie dog,mouse,rat"
      Dim pattern As String = "\G(\w+\s?\w*),?"
      Dim match As Match = Regex.Match(input, pattern)
      Do While match.Success
         Console.WriteLine(match.Groups(1).Value)
         match = match.NextMatch()
      Loop 
   End Sub
End Module
' The example displays the following output:
'       capybara
'       squirrel
'       chipmunk
'       porcupine
'       gopher
'       beaver
'       groundhog
'       hamster
'       guinea pig
'       gerbil
'       chinchilla
'       prairie dog
'       mouse
'       rat
```

A expressão regular `\G(\w+\s?\w*),?` é interpretada conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | ----------- 
`\G` | Começa onde a última correspondência terminou.
`\w+` | Fazer a correspondência a um ou mais caracteres de palavra.
`\s?` | Corresponde a zero ou um espaço.
`\w*` | Corresponder a zero ou mais caracteres de palavra.
`(\w+\s?\w*)` | Corresponde a um ou mais caracteres de palavra seguidos por zero ou um espaço, seguido por zero ou mais caracteres de palavra. Este é o primeiro grupo de captura.
`,?` | Corresponde a zero ou uma ocorrência de um caractere de vírgula literal.
 
## <a name="word-boundary-b"></a>Limite de Palavra: \b

A âncora **\b** especifica que a correspondência deve ocorrer em um limite entre um caractere de palavra (o elemento de linguagem **\w**) e um caractere não pertencente a palavras (o elemento de linguagem **\W**). Os caracteres de palavra consistem em caracteres alfanuméricos e sublinhados. Um caractere não pertencente a palavras é qualquer caractere que não seja alfanumérico ou um sublinhado. (Para obter mais informações, confira [Classes de caracteres em expressões regulares](classes.md).) A correspondência também pode ocorrer em um limite de palavra no início ou no final da cadeia de caracteres.

A âncora **\b** frequentemente é usada para garantir que uma subexpressão corresponda a uma palavra inteira, em vez de apenas ao início ou final de uma palavra. A expressão regular `\bare\w*\b` no exemplo a seguir ilustra esse uso. Ela corresponde a qualquer palavra que comece com a subcadeia de caracteres "are". A saída do exemplo também ilustra que **\b** corresponde ao início e ao final da cadeia de caracteres de entrada. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "area bare arena mare";
      string pattern = @"\bare\w*\b";
      Console.WriteLine("Words that begin with 'are':");
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("'{0}' found at position {1}",
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       Words that begin with 'are':
//       'area' found at position 0
//       'arena' found at position 10
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "area bare arena mare"
      Dim pattern As String = "\bare\w*\b"
      Console.WriteLine("Words that begin with 'are':")
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("'{0}' found at position {1}", _
                           match.Value, match.Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       Words that begin with 'are':
'       'area' found at position 0
'       'arena' found at position 10
```

O padrão da expressão regular é interpretado conforme a tabela a seguir.

Padrão | Descrição
------- | ----------- 
`\b` | Começar a correspondência em um limite de palavra.
`are` | Corresponde à subcadeia de caracteres “are”.
`\w*` | Corresponder a zero ou mais caracteres de palavra.
`\b` | Termina a correspondência em um limite de palavra.
 
## <a name="non-word-boundary-b"></a>Limite de Não Palavra: \B

A âncora **\B** especifica que a correspondência não deve ocorrer em um limite de palavra. É o oposto da âncora **\b**.

O exemplo a seguir usa a âncora **\B** para localizar ocorrências da subcadeia de caracteres "qu" em uma palavra. O padrão de expressão regular `\Bqu\w+` corresponde a uma subcadeia de caracteres que começa com um "qu" que não inicia uma palavra e que continua até o final da palavra.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "equity queen equip acquaint quiet";
      string pattern = @"\Bqu\w+";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("'{0}' found at position {1}", 
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       'quity' found at position 1
//       'quip' found at position 14
//       'quaint' found at position 21
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "equity queen equip acquaint quiet"
      Dim pattern As String = "\Bqu\w+"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("'{0}' found at position {1}", _
                           match.Value, match.Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       'quity' found at position 1
'       'quip' found at position 14
'       'quaint' found at position 21
```

O padrão da expressão regular é interpretado conforme a tabela a seguir.

Padrão | Descrição
------- | ----------- 
`\B` | Não começa a correspondência em um limite de palavra.
`qu` | Corresponde à subcadeia de caracteres “qu”.
`\w+` | Fazer a correspondência a um ou mais caracteres de palavra.
 
## <a name="see-also"></a>Consulte também

[Linguagem de expressão regular – referência rápida](quick-ref.md)

[Opções de expressões regulares](options.md)
 



<!--HONumber=Nov16_HO5-->


