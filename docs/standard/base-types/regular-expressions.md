---
title: "Expressões regulares no .NET"
description: "Expressões regulares no .NET"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: d1a640cf-09ca-48f7-800c-a627a6d549c9
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: ac26821819b22aa3ea47e6945bb5c8575dcd9807
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="regular-expressions-in-net"></a><span data-ttu-id="17b02-104">Expressões regulares no .NET</span><span class="sxs-lookup"><span data-stu-id="17b02-104">Regular expressions in .NET</span></span>

<span data-ttu-id="17b02-105">Expressões regulares oferecem um método poderoso, flexível e eficiente de processamento de texto.</span><span class="sxs-lookup"><span data-stu-id="17b02-105">Regular expressions provide a powerful, flexible, and efficient method for processing text.</span></span> <span data-ttu-id="17b02-106">A extensiva notação de correspondência de padrões de expressões regulares permite que você analise rapidamente grandes quantidades de texto para encontrar padrões de caracteres específicos; para validar o texto e garantir que ele corresponda a um padrão predefinido (como um endereço de email); para extrair, editar, substituir ou excluir subcadeias de caracteres de texto; e para adicionar as cadeias de caracteres extraídas para uma coleção a fim de gerar um relatório.</span><span class="sxs-lookup"><span data-stu-id="17b02-106">The extensive pattern-matching notation of regular expressions enables you to quickly parse large amounts of text to find specific character patterns; to validate text to ensure that it matches a predefined pattern (such as an e-mail address); to extract, edit, replace, or delete text substrings; and to add the extracted strings to a collection in order to generate a report.</span></span> <span data-ttu-id="17b02-107">Para vários aplicativos que lidam com cadeias de caracteres ou que analisam grandes blocos de texto, as expressões regulares são uma ferramenta indispensável.</span><span class="sxs-lookup"><span data-stu-id="17b02-107">For many applications that deal with strings or that parse large blocks of text, regular expressions are an indispensable tool.</span></span>

## <a name="how-regular-expressions-work"></a><span data-ttu-id="17b02-108">Como funcionam as expressões regulares</span><span class="sxs-lookup"><span data-stu-id="17b02-108">How Regular Expressions Work</span></span>

<span data-ttu-id="17b02-109">A parte mais importante do processamento de texto com expressões regulares é o mecanismo de expressões regulares, que é representado pelo objeto [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) no .NET.</span><span class="sxs-lookup"><span data-stu-id="17b02-109">The centerpiece of text processing with regular expressions is the regular expression engine, which is represented by the [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) object in .NET.</span></span> <span data-ttu-id="17b02-110">No mínimo, o processamento de texto usando expressões regulares exige que o mecanismo de expressões regulares seja fornecido com os dois itens informativos a seguir:</span><span class="sxs-lookup"><span data-stu-id="17b02-110">At a minimum, processing text using regular expressions requires that the regular expression engine be provided with the following two items of information:</span></span>

* <span data-ttu-id="17b02-111">O padrão de expressão regular a ser identificado no texto.</span><span class="sxs-lookup"><span data-stu-id="17b02-111">The regular expression pattern to identify in the text.</span></span> 
  
  <span data-ttu-id="17b02-112">No .NET, padrões de expressão regular são definidos por uma sintaxe ou linguagem especial, compatível com expressões regulares Perl 5 e inclui alguns recursos adicionais, como correspondência da direita para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="17b02-112">In .NET, regular expression patterns are defined by a special syntax or language, which is compatible with Perl 5 regular expressions and adds some additional features such as right-to-left matching.</span></span> <span data-ttu-id="17b02-113">Para obter mais informações, consulte [Linguagem de expressões regulares – referência rápida](quick-ref.md).</span><span class="sxs-lookup"><span data-stu-id="17b02-113">For more information, see [Regular Expression Language - Quick Reference](quick-ref.md).</span></span>
  
* <span data-ttu-id="17b02-114">O texto a ser analisado para o padrão de expressão regular.</span><span class="sxs-lookup"><span data-stu-id="17b02-114">The text to parse for the regular expression pattern.</span></span>

<span data-ttu-id="17b02-115">Os métodos da classe [Regex](xref:System.Text.RegularExpressions.Regex) permitem que você realize as seguintes operações:</span><span class="sxs-lookup"><span data-stu-id="17b02-115">The methods of the [Regex](xref:System.Text.RegularExpressions.Regex) class let you perform the following operations:</span></span>

* <span data-ttu-id="17b02-116">Determinar se o padrão de expressão regular ocorre no texto de entrada chamando o método [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)).</span><span class="sxs-lookup"><span data-stu-id="17b02-116">Determine whether the regular expression pattern occurs in the input text by calling the [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) method.</span></span> <span data-ttu-id="17b02-117">Para obter um exemplo que usa o método [IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) para validar texto, consulte [Como verificar se cadeias de caracteres estão em um formato de email válido](verify-format.md).</span><span class="sxs-lookup"><span data-stu-id="17b02-117">For an example that uses the [IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) method for validating text, see [How to: Verify that Strings Are in Valid Email Format](verify-format.md).</span></span>

* <span data-ttu-id="17b02-118">Recuperar uma ou todas as ocorrências de texto que correspondem ao padrão de expressão regular chamando o método [Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) ou [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)).</span><span class="sxs-lookup"><span data-stu-id="17b02-118">Retrieve one or all occurrences of text that matches the regular expression pattern by calling the [Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) or [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) method.</span></span> <span data-ttu-id="17b02-119">O primeiro método retorna um objeto [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) que oferece informações sobre o texto correspondente.</span><span class="sxs-lookup"><span data-stu-id="17b02-119">The former method returns a [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) object that provides information about the matching text.</span></span> <span data-ttu-id="17b02-120">O último retorna um objeto [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) que contém um objeto [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) para cada correspondência encontrada no texto analisado.</span><span class="sxs-lookup"><span data-stu-id="17b02-120">The latter returns a [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) object that contains one [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) object for each match found in the parsed text.</span></span> 

* <span data-ttu-id="17b02-121">Substituir o texto que corresponde ao padrão da expressão regular chamando o método [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)).</span><span class="sxs-lookup"><span data-stu-id="17b02-121">Replace text that matches the regular expression pattern by calling the [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) method.</span></span> <span data-ttu-id="17b02-122">Para ver exemplos que usam o método [Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) para alterar formatos de data e remover caracteres inválidos de uma cadeia de caracteres, consulte [Como retirar caracteres inválidos de uma cadeia de caracteres](strip-characters.md) e [Exemplo de expressão regular: alterando formatos de data](changing-formats.md).</span><span class="sxs-lookup"><span data-stu-id="17b02-122">For examples that use the [Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) method to change date formats and remove invalid characters from a string, see [How to: Strip Invalid Characters from a String](strip-characters.md) and [Regular Expression Example: Changing Date Formats](changing-formats.md).</span></span>

<span data-ttu-id="17b02-123">Para obter uma visão geral do modelo de objeto de expressão regular, consulte [O modelo de objeto de expressão regular](object-model.md).</span><span class="sxs-lookup"><span data-stu-id="17b02-123">For an overview of the regular expression object model, see [The Regular Expression Object Model](object-model.md).</span></span>

<span data-ttu-id="17b02-124">Para obter mais informações sobre a linguagem de expressão regular, consulte [Linguagem de expressões regulares – referência rápida](quick-ref.md).</span><span class="sxs-lookup"><span data-stu-id="17b02-124">For more information about the regular expression language, see [Regular Expression Language - Quick Reference](quick-ref.md).</span></span>

## <a name="regular-expression-examples"></a><span data-ttu-id="17b02-125">Exemplos de expressões regulares</span><span class="sxs-lookup"><span data-stu-id="17b02-125">Regular Expression Examples</span></span>

<span data-ttu-id="17b02-126">A classe [String](xref:System.String) inclui uma série de métodos de pesquisa de cadeia de caracteres e substituição que podem ser usados quando você quer localizar cadeias de caracteres literais em uma cadeia de caracteres maior.</span><span class="sxs-lookup"><span data-stu-id="17b02-126">The [String](xref:System.String) class includes a number of string search and replacement methods that you can use when you want to locate literal strings in a larger string.</span></span> <span data-ttu-id="17b02-127">Expressões regulares são mais úteis quando você quer localizar uma dentre diversas subcadeias de caracteres em uma cadeia de caracteres maior ou quando quer identificar padrões em uma cadeia de caracteres, como mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="17b02-127">Regular expressions are most useful either when you want to locate one of several substrings in a larger string, or when you want to identify patterns in a string, as the following examples illustrate.</span></span> 

### <a name="example-1-replacing-substrings"></a><span data-ttu-id="17b02-128">Exemplo 1: substituindo subcadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="17b02-128">Example 1: Replacing Substrings</span></span>

<span data-ttu-id="17b02-129">Vamos presumir que uma lista de endereçamento contém nomes que, às vezes, incluem um pronome de tratamento (Sr., Srs., Srta. ou Sra.) junto com o nome e o sobrenome.</span><span class="sxs-lookup"><span data-stu-id="17b02-129">Assume that a mailing list contains names that sometimes include a title (Mr., Mrs., Miss, or Ms.) along with a first and last name.</span></span> <span data-ttu-id="17b02-130">Se não quiser incluir os pronomes de tratamento ao gerar etiquetas para envelopes na lista, é possível usar uma expressão regular para removê-los, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="17b02-130">If you do not want to include the titles when you generate envelope labels from the list, you can use a regular expression to remove the titles, as the following example illustrates.</span></span>

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = "(Mr\\.? |Mrs\\.? |Miss |Ms\\.? )";
      string[] names = { "Mr. Henry Hunt", "Ms. Sara Samuels", 
                         "Abraham Adams", "Ms. Nicole Norris" };
      foreach (string name in names)
         Console.WriteLine(Regex.Replace(name, pattern, String.Empty));
   }
}
// The example displays the following output:
//    Henry Hunt
//    Sara Samuels
//    Abraham Adams
//    Nicole Norris
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(Mr\.? |Mrs\.? |Miss |Ms\.? )"
      Dim names() As String = { "Mr. Henry Hunt", "Ms. Sara Samuels", _
                                "Abraham Adams", "Ms. Nicole Norris" }
      For Each name As String In names
         Console.WriteLine(Regex.Replace(name, pattern, String.Empty))
      Next                                
   End Sub
End Module
' The example displays the following output:
'    Henry Hunt
'    Sara Samuels
'    Abraham Adams
'    Nicole Norris
```

<span data-ttu-id="17b02-131">O padrão de expressão regular `(Mr\.? |Mrs\.? |Miss |Ms\.? )` corresponde a qualquer ocorrência de “Sr”, “Sr.”, “Sra”, “Sra.”, “Srta” ou “Srta.”.</span><span class="sxs-lookup"><span data-stu-id="17b02-131">The regular expression pattern `(Mr\.? |Mrs\.? |Miss |Ms\.? )` matches any occurrence of "Mr ", "Mr. ", "Mrs ", "Mrs. ", "Miss ", "Ms or "Ms. ".</span></span> <span data-ttu-id="17b02-132">A chamada para o método [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) substitui a cadeia de caracteres correspondente por [String.Empty](xref:System.String.Empty); em outras palavras, ela a remove da cadeia de caracteres original.</span><span class="sxs-lookup"><span data-stu-id="17b02-132">The call to the [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) method replaces the matched string with [String.Empty](xref:System.String.Empty); in other words, it removes it from the original string.</span></span>

### <a name="example-2-identifying-duplicated-words"></a><span data-ttu-id="17b02-133">Exemplo 2: identificando palavras duplicadas</span><span class="sxs-lookup"><span data-stu-id="17b02-133">Example 2: Identifying Duplicated Words</span></span>

<span data-ttu-id="17b02-134">Duplicar palavras acidentalmente é um erro comum que escritores cometem.</span><span class="sxs-lookup"><span data-stu-id="17b02-134">Accidentally duplicating words is a common error that writers make.</span></span> <span data-ttu-id="17b02-135">Uma expressão regular pode ser usada para identificar palavras duplicadas, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="17b02-135">A regular expression can be used to identify duplicated words, as the following example shows.</span></span>

```csharp
using System;
using System.Text.RegularExpressions;

public class Class1
{
   public static void Main()
   {
      string pattern = @"\b(\w+?)\s\1\b";
      string input = "This this is a nice day. What about this? This tastes good. I saw a a dog.";
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
         Console.WriteLine("{0} (duplicates '{1}') at position {2}", 
                           match.Value, match.Groups[1].Value, match.Index);
   }
}
// The example displays the following output:
//       This this (duplicates 'This)' at position 0
//       a a (duplicates 'a)' at position 66
```

```vb
Imports System.Text.RegularExpressions

Module modMain
   Public Sub Main()
      Dim pattern As String = "\b(\w+?)\s\1\b"
      Dim input As String = "This this is a nice day. What about this? This tastes good. I saw a a dog."
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
         Console.WriteLine("{0} (duplicates '{1}') at position {2}", _
                           match.Value, match.Groups(1).Value, match.Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       This this (duplicates 'This)' at position 0
'       a a (duplicates 'a)' at position 66
```

<span data-ttu-id="17b02-136">O padrão de expressão regular `\b(\w+?)\s\1\b` pode ser interpretado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="17b02-136">The regular expression pattern `\b(\w+?)\s\1\b` can be interpreted as follows:</span></span>

<span data-ttu-id="17b02-137">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17b02-137">Syntax</span></span> | <span data-ttu-id="17b02-138">Significado</span><span class="sxs-lookup"><span data-stu-id="17b02-138">Meaning</span></span>
------ | -------
`\b` | <span data-ttu-id="17b02-139">Iniciar em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="17b02-139">Start at a word boundary.</span></span>
`(\w+?)` | <span data-ttu-id="17b02-140">Corresponder a um ou mais caracteres de palavra, mas o menor número de caracteres possível.</span><span class="sxs-lookup"><span data-stu-id="17b02-140">Match one or more word characters, but as few characters as possible.</span></span> <span data-ttu-id="17b02-141">Juntos, formam um grupo que pode ser chamado de `\1`.</span><span class="sxs-lookup"><span data-stu-id="17b02-141">Together, they form a group that can be referred to as `\1`.</span></span>
`\s` | <span data-ttu-id="17b02-142">Corresponde a um caractere de espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="17b02-142">Match a white-space character.</span></span>
`\1` | <span data-ttu-id="17b02-143">Corresponder à subcadeia de caracteres que é igual ao grupo denominado `\1`.</span><span class="sxs-lookup"><span data-stu-id="17b02-143">Match the substring that is equal to the group named `\1`.</span></span>
`\b` | <span data-ttu-id="17b02-144">Corresponder a um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="17b02-144">Match a word boundary.</span></span>

<span data-ttu-id="17b02-145">O método [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) é chamado com opções de expressão regular definidas como [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase).</span><span class="sxs-lookup"><span data-stu-id="17b02-145">The [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) method is called with regular expression options set to [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase).</span></span> <span data-ttu-id="17b02-146">Portanto, a operação de correspondência não faz distinção entre maiúsculas e minúsculas e o exemplo identifica a subcadeia de caracteres “This this” como uma duplicação.</span><span class="sxs-lookup"><span data-stu-id="17b02-146">Therefore, the match operation is case-insensitive, and the example identifies the substring "This this" as a duplication.</span></span>

<span data-ttu-id="17b02-147">Observe que a cadeia de caracteres de entrada inclui a subcadeia de caracteres “this?</span><span class="sxs-lookup"><span data-stu-id="17b02-147">Note that the input string includes the substring "this?</span></span> <span data-ttu-id="17b02-148">This”.</span><span class="sxs-lookup"><span data-stu-id="17b02-148">This".</span></span> <span data-ttu-id="17b02-149">No entanto, devido à pontuação no meio, ela não é identificada como uma duplicação.</span><span class="sxs-lookup"><span data-stu-id="17b02-149">However, because of the intervening punctuation mark, it is not identified as a duplication.</span></span>

### <a name="example-3-dynamically-building-a-culture-sensitive-regular-expression"></a><span data-ttu-id="17b02-150">Exemplo 3: compilando dinamicamente uma expressão regular sensível à cultura</span><span class="sxs-lookup"><span data-stu-id="17b02-150">Example 3: Dynamically Building a Culture-Sensitive Regular Expression</span></span>

<span data-ttu-id="17b02-151">O exemplo a seguir mostra a força das expressões regulares combinada à flexibilidade oferecida pelos recursos de globalização do .NET.</span><span class="sxs-lookup"><span data-stu-id="17b02-151">The following example illustrates the power of regular expressions combined with the flexibility offered by .NET's globalization features.</span></span> <span data-ttu-id="17b02-152">Ele utiliza o objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) para determinar o formato de valores de moeda na cultura atual do sistema.</span><span class="sxs-lookup"><span data-stu-id="17b02-152">It uses the [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object to determine the format of currency values in the system's current culture.</span></span> <span data-ttu-id="17b02-153">Então, essa informação é usada para construir dinamicamente uma expressão regular que extrai valores de moeda do texto.</span><span class="sxs-lookup"><span data-stu-id="17b02-153">It then uses that information to dynamically construct a regular expression that extracts currency values from the text.</span></span> <span data-ttu-id="17b02-154">Para cada correspondência, ele extrai o subgrupo que contém somente a subcadeia de caracteres, converte-a para um valor [Decimal](xref:System.Decimal) e calcula uma soma acumulada.</span><span class="sxs-lookup"><span data-stu-id="17b02-154">For each match, it extracts the subgroup that contains the numeric string only, converts it to a [Decimal](xref:System.Decimal) value, and calculates a running total.</span></span> 

```csharp
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      // Define text to be parsed.
      string input = "Office expenses on 2/13/2008:\n" + 
                     "Paper (500 sheets)                      $3.95\n" + 
                     "Pencils (box of 10)                     $1.00\n" + 
                     "Pens (box of 10)                        $4.49\n" + 
                     "Erasers                                 $2.19\n" + 
                     "Ink jet printer                        $69.95\n\n" + 
                     "Total Expenses                        $ 81.58\n"; 

      // Get current culture's NumberFormatInfo object.
      NumberFormatInfo nfi = CultureInfo.CurrentCulture.NumberFormat;
      // Assign needed property values to variables.
      string currencySymbol = nfi.CurrencySymbol;
      bool symbolPrecedesIfPositive = nfi.CurrencyPositivePattern % 2 == 0;
      string groupSeparator = nfi.CurrencyGroupSeparator;
      string decimalSeparator = nfi.CurrencyDecimalSeparator;

      // Form regular expression pattern.
      string pattern = Regex.Escape( symbolPrecedesIfPositive ? currencySymbol : "") + 
                       @"\s*[-+]?" + "([0-9]{0,3}(" + groupSeparator + "[0-9]{3})*(" + 
                       Regex.Escape(decimalSeparator) + "[0-9]+)?)" + 
                       (! symbolPrecedesIfPositive ? currencySymbol : ""); 
      Console.WriteLine( "The regular expression pattern is:");
      Console.WriteLine("   " + pattern);      

      // Get text that matches regular expression pattern.
      MatchCollection matches = Regex.Matches(input, pattern, 
                                              RegexOptions.IgnorePatternWhitespace);               
      Console.WriteLine("Found {0} matches.", matches.Count); 

      // Get numeric string, convert it to a value, and add it to List object.
      List<decimal> expenses = new List<Decimal>();

      foreach (Match match in matches)
         expenses.Add(Decimal.Parse(match.Groups[1].Value));      

      // Determine whether total is present and if present, whether it is correct.
      decimal total = 0;
      foreach (decimal value in expenses)
         total += value;

      if (total / 2 == expenses[expenses.Count - 1]) 
         Console.WriteLine("The expenses total {0:C2}.", expenses[expenses.Count - 1]);
      else
         Console.WriteLine("The expenses total {0:C2}.", total);
   }  
}
// The example displays the following output:
//       The regular expression pattern is:
//          \$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)
//       Found 6 matches.
//       The expenses total $81.58.
```

```vb
Imports System.Collections.Generic
Imports System.Globalization
Imports System.Text.RegularExpressions

Public Module Example
   Public Sub Main()
      ' Define text to be parsed.
      Dim input As String = "Office expenses on 2/13/2008:" + vbCrLf + _
                            "Paper (500 sheets)                      $3.95" + vbCrLf + _
                            "Pencils (box of 10)                     $1.00" + vbCrLf + _
                            "Pens (box of 10)                        $4.49" + vbCrLf + _
                            "Erasers                                 $2.19" + vbCrLf + _
                            "Ink jet printer                        $69.95" + vbCrLf + vbCrLf + _
                            "Total Expenses                        $ 81.58" + vbCrLf
      ' Get current culture's NumberFormatInfo object.
      Dim nfi As NumberFormatInfo = CultureInfo.CurrentCulture.NumberFormat
      ' Assign needed property values to variables.
      Dim currencySymbol As String = nfi.CurrencySymbol
      Dim symbolPrecedesIfPositive As Boolean = CBool(nfi.CurrencyPositivePattern Mod 2 = 0)
      Dim groupSeparator As String = nfi.CurrencyGroupSeparator
      Dim decimalSeparator As String = nfi.CurrencyDecimalSeparator

      ' Form regular expression pattern.
      Dim pattern As String = Regex.Escape(CStr(IIf(symbolPrecedesIfPositive, currencySymbol, ""))) + _
                              "\s*[-+]?" + "([0-9]{0,3}(" + groupSeparator + "[0-9]{3})*(" + _
                              Regex.Escape(decimalSeparator) + "[0-9]+)?)" + _
                              CStr(IIf(Not symbolPrecedesIfPositive, currencySymbol, "")) 
      Console.WriteLine("The regular expression pattern is: ")
      Console.WriteLine("   " + pattern)      

      ' Get text that matches regular expression pattern.
      Dim matches As MatchCollection = Regex.Matches(input, pattern, RegexOptions.IgnorePatternWhitespace)               
      Console.WriteLine("Found {0} matches. ", matches.Count)

      ' Get numeric string, convert it to a value, and add it to List object.
      Dim expenses As New List(Of Decimal)

      For Each match As Match In matches
         expenses.Add(Decimal.Parse(match.Groups.Item(1).Value))      
      Next

      ' Determine whether total is present and if present, whether it is correct.
      Dim total As Decimal
      For Each value As Decimal In expenses
         total += value
      Next

      If total / 2 = expenses(expenses.Count - 1) Then
         Console.WriteLine("The expenses total {0:C2}.", expenses(expenses.Count - 1))
      Else
         Console.WriteLine("The expenses total {0:C2}.", total)
      End If   
   End Sub
End Module
' The example displays the following output:
'       The regular expression pattern is:
'          \$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)
'       Found 6 matches.
'       The expenses total $81.58.
```

<span data-ttu-id="17b02-155">Em um computador cuja cultura atual seja Inglês – Estados Unidos (en-US), o exemplo compila dinamicamente a expressão regular `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`.</span><span class="sxs-lookup"><span data-stu-id="17b02-155">On a computer whose current culture is English - United States (en-US), the example dynamically builds the regular expression `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`.</span></span> <span data-ttu-id="17b02-156">Esse padrão de expressão regular pode ser interpretado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="17b02-156">This regular expression pattern can be interpreted as follows:</span></span>

<span data-ttu-id="17b02-157">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17b02-157">Syntax</span></span> | <span data-ttu-id="17b02-158">Significado</span><span class="sxs-lookup"><span data-stu-id="17b02-158">Meaning</span></span>
------ | -------
`\$` | <span data-ttu-id="17b02-159">Procure uma única ocorrência do símbolo de cifrão ($) na cadeia de caracteres de entrada.</span><span class="sxs-lookup"><span data-stu-id="17b02-159">Look for a single occurrence of the dollar symbol ($) in the input string.</span></span> <span data-ttu-id="17b02-160">A cadeia de caracteres do padrão de expressão regular inclui uma barra invertida para indicar que o símbolo de cifrão deve ser interpretado literalmente ao invés de como uma âncora de expressão regular.</span><span class="sxs-lookup"><span data-stu-id="17b02-160">The regular expression pattern string includes a backslash to indicate that the dollar symbol is to be interpreted literally rather than as a regular expression anchor.</span></span> <span data-ttu-id="17b02-161">(O símbolo $ sozinho indicaria que o mecanismo de expressões regulares deveria tentar iniciar a correspondência no final de uma cadeia de caracteres.) Para assegurar que o símbolo de moeda da cultura atual não seja interpretado inadequadamente como um símbolo de expressão regular, o exemplo chama o método [Escape](xref:System.Text.RegularExpressions.Regex.Escape(System.String)) para escapar do caractere.</span><span class="sxs-lookup"><span data-stu-id="17b02-161">(The $ symbol alone would indicate that the regular expression engine should try to begin its match at the end of a string.) To ensure that the current culture's currency symbol is not misinterpreted as a regular expression symbol, the example calls the [Escape](xref:System.Text.RegularExpressions.Regex.Escape(System.String)) method to escape the character.</span></span>
`\s*` | <span data-ttu-id="17b02-162">Procure zero ou mais ocorrências de um caractere de espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="17b02-162">Look for zero or more occurrences of a white-space character.</span></span>
`[-+]?` | <span data-ttu-id="17b02-163">Procure zero ou uma ocorrência de um sinal de positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="17b02-163">Look for zero or one occurrence of either a positive sign or a negative sign.</span></span>
`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)` | <span data-ttu-id="17b02-164">Os parênteses externos ao redor da expressão a definem como um grupo de captura ou uma subexpressão.</span><span class="sxs-lookup"><span data-stu-id="17b02-164">The outer parentheses around this expression define it as a capturing group or a subexpression.</span></span> <span data-ttu-id="17b02-165">Se uma correspondência for encontrada, informações sobre essa parte da cadeia de caracteres correspondente podem ser recuperadas do segundo objeto [Group](xref:System.Text.RegularExpressions.Group) no objeto [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) retornado pela propriedade [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups).</span><span class="sxs-lookup"><span data-stu-id="17b02-165">If a match is found, information about this part of the matching string can be retrieved from the second [Group](xref:System.Text.RegularExpressions.Group) object in the [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) object returned by the [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) property.</span></span> <span data-ttu-id="17b02-166">(O primeiro elemento na coleção representa a correspondência inteira.)</span><span class="sxs-lookup"><span data-stu-id="17b02-166">(The first element in the collection represents the entire match.)</span></span>
`[0-9]{0,3}` | <span data-ttu-id="17b02-167">Procure de zero a três ocorrências dos dígitos decimais de 0 a 9.</span><span class="sxs-lookup"><span data-stu-id="17b02-167">Look for zero to three occurrences of the decimal digits 0 through 9.</span></span>
`(,[0-9]{3})*` | <span data-ttu-id="17b02-168">Procure zero ou mais ocorrências de um separador de grupo seguido por três dígitos decimais.</span><span class="sxs-lookup"><span data-stu-id="17b02-168">Look for zero or more occurrences of a group separator followed by three decimal digits.</span></span>
`\.` | <span data-ttu-id="17b02-169">Procure uma única ocorrência do separador decimal.</span><span class="sxs-lookup"><span data-stu-id="17b02-169">Look for a single occurrence of the decimal separator.</span></span>
`[0-9]+` | <span data-ttu-id="17b02-170">Procure por um ou mais dígitos decimais.</span><span class="sxs-lookup"><span data-stu-id="17b02-170">Look for one or more decimal digits.</span></span>
`(\.[0-9]+)?` | <span data-ttu-id="17b02-171">Procure zero ou uma ocorrência de um separador decimal seguido por pelo menos um dígito decimal.</span><span class="sxs-lookup"><span data-stu-id="17b02-171">Look for zero or one occurrence of the decimal separator followed by at least one decimal digit.</span></span>

## <a name="related-topics"></a><span data-ttu-id="17b02-172">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="17b02-172">Related Topics</span></span>

<span data-ttu-id="17b02-173">Título</span><span class="sxs-lookup"><span data-stu-id="17b02-173">Title</span></span> | <span data-ttu-id="17b02-174">Descrição</span><span class="sxs-lookup"><span data-stu-id="17b02-174">Description</span></span>
----- | -----------
[<span data-ttu-id="17b02-175">Linguagem de expressão regular – referência rápida</span><span class="sxs-lookup"><span data-stu-id="17b02-175">Regular expression language - quick reference</span></span>](quick-ref.md) | <span data-ttu-id="17b02-176">Oferece informações sobre o conjunto de caracteres, operadores e constructos que você pode usar para definir expressões regulares.</span><span class="sxs-lookup"><span data-stu-id="17b02-176">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>
[<span data-ttu-id="17b02-177">O modelo de objeto de expressão regular</span><span class="sxs-lookup"><span data-stu-id="17b02-177">The regular expression object model</span></span>](object-model.md) | <span data-ttu-id="17b02-178">Oferece informações e exemplos de código que ilustram como usar as classes de expressão regular.</span><span class="sxs-lookup"><span data-stu-id="17b02-178">Provides information and code examples that illustrate how to use the regular expression classes.</span></span>
[<span data-ttu-id="17b02-179">Detalhes do comportamento de expressões regulares</span><span class="sxs-lookup"><span data-stu-id="17b02-179">Details of regular expression behavior</span></span>](regex-behavior.md) | <span data-ttu-id="17b02-180">Oferece informações sobre os recursos e o comportamento das expressões regulares do .NET.</span><span class="sxs-lookup"><span data-stu-id="17b02-180">Provides information about the capabilities and behavior of .NETregular expressions.</span></span>
[<span data-ttu-id="17b02-181">Exemplos de expressões regulares</span><span class="sxs-lookup"><span data-stu-id="17b02-181">Regular expression examples</span></span>](regex-examples.md) | <span data-ttu-id="17b02-182">Oferece exemplos de código que ilustram usos típicos de expressões regulares.</span><span class="sxs-lookup"><span data-stu-id="17b02-182">Provides code examples that illustrate typical uses of regular expressions.</span></span>


## <a name="reference"></a><span data-ttu-id="17b02-183">Referência</span><span class="sxs-lookup"><span data-stu-id="17b02-183">Reference</span></span>

[<span data-ttu-id="17b02-184">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="17b02-184">System.Text.RegularExpressions</span></span>](xref:System.Text.RegularExpressions)

[<span data-ttu-id="17b02-185">System.Text.RegularExpressions.Regex</span><span class="sxs-lookup"><span data-stu-id="17b02-185">System.Text.RegularExpressions.Regex</span></span>](xref:System.Text.RegularExpressions.Regex)


