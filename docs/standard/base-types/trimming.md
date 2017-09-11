---
title: Cortando e removendo caracteres das cadeias de caracteres
description: Cortando e removendo caracteres das cadeias de caracteres
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 95d818bc-2661-43f6-adb8-13b53abf9682
ms.translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 6105861882c3bfd525a2d902fd2600f5da10417d
ms.contentlocale: pt-br
ms.lasthandoff: 11/16/2016

---

# <a name="trimming-and-removing-characters-from-strings"></a><span data-ttu-id="dd4d2-104">Cortando e removendo caracteres das cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="dd4d2-104">Trimming and removing characters from strings</span></span>

<span data-ttu-id="dd4d2-105">Se estiver analisando as palavras individuais de uma sentença, você poderá encontrar palavras com espaços em branco em ambas as extremidades da palavra.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-105">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="dd4d2-106">Nessa situação, você pode usar um dos métodos de corte na classe [System.String](https://docs.microsoft.com/dotnet/core/api/System.String) para remover qualquer número de espaços ou de outros caracteres de uma posição especificada na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-106">In this situation, you can use one of the trim methods in the [System.String](https://docs.microsoft.com/dotnet/core/api/System.String) class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="dd4d2-107">A tabela a seguir descreve os métodos de corte disponíveis.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-107">The following table describes the available trim methods.</span></span>

<span data-ttu-id="dd4d2-108">Nome do método</span><span class="sxs-lookup"><span data-stu-id="dd4d2-108">Method name</span></span> | <span data-ttu-id="dd4d2-109">Use</span><span class="sxs-lookup"><span data-stu-id="dd4d2-109">Use</span></span>
----------- | ---
[<span data-ttu-id="dd4d2-110">String.Trim</span><span class="sxs-lookup"><span data-stu-id="dd4d2-110">String.Trim</span></span>](https://docs.microsoft.com/dotnet/core/api/System.String.Trim) | <span data-ttu-id="dd4d2-111">Remove os espaços em branco ou caracteres especificados em uma matriz de caracteres do início e do final de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-111">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>
<span data-ttu-id="dd4d2-112">[String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[]))</span><span class="sxs-lookup"><span data-stu-id="dd4d2-112">[String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[]))</span></span> | <span data-ttu-id="dd4d2-113">Remove os caracteres especificados em uma matriz de caracteres do final de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-113">Removes characters specified in an array of characters from the end of a string.</span></span>
<span data-ttu-id="dd4d2-114">[String.TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[]))</span><span class="sxs-lookup"><span data-stu-id="dd4d2-114">[String.TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[]))</span></span> | <span data-ttu-id="dd4d2-115">Remove os caracteres especificados em uma matriz de caracteres do início de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-115">Removes characters specified in an array of characters from the beginning of a string.</span></span>
<span data-ttu-id="dd4d2-116">[String.Remove](https://docs.microsoft.com/dotnet/core/api/System.String.Remove(System.Int32))</span><span class="sxs-lookup"><span data-stu-id="dd4d2-116">[String.Remove](https://docs.microsoft.com/dotnet/core/api/System.String.Remove(System.Int32))</span></span> | <span data-ttu-id="dd4d2-117">Remove um número especificado de caracteres de uma posição de índice especificada em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-117">Removes a specified number of characters from a specified index position in a string.</span></span>


## <a name="trim"></a><span data-ttu-id="dd4d2-118">Trim</span><span class="sxs-lookup"><span data-stu-id="dd4d2-118">Trim</span></span>

<span data-ttu-id="dd4d2-119">Você pode remover espaços em branco com facilidade de ambas as extremidades de uma cadeia de caracteres usando o método [String.Trim](https://docs.microsoft.com/dotnet/core/api/System.String.Trim), conforme é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-119">You can easily remove white spaces from both ends of a string by using the [String.Trim](https://docs.microsoft.com/dotnet/core/api/System.String.Trim) method, as shown in the following example.</span></span>

```csharp
string MyString = " Big   ";
Console.WriteLine("Hello{0}World!", MyString);
string TrimString = MyString.Trim();
Console.WriteLine("Hello{0}World!", TrimString);
//       The example displays the following output:
//             Hello Big   World!
//             HelloBigWorld!
```

```vb
Dim MyString As String = " Big   "
Console.WriteLine("Hello{0}World!", MyString)
Dim TrimString As String = MyString.Trim()
Console.WriteLine("Hello{0}World!", TrimString)
' The example displays the following output:
'       Hello Big   World!
'       HelloBigWorld!
```

<span data-ttu-id="dd4d2-120">Você também poderá remover os caracteres que especificar em uma matriz de caracteres do início e do final de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-120">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="dd4d2-121">O exemplo a seguir remove caracteres de espaço em branco, pontos e asteriscos.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-121">The following example removes white-space characters, periods, and asterisks.</span></span>

```csharp
using System;

public class Example
{
   public static void Main()
   {
      String header = "* A Short String. *";
      Console.WriteLine(header);
      Console.WriteLine(header.Trim( new Char[] { ' ', '*', '.' } ));
   }
}
// The example displays the following output:
//       * A Short String. *
//       A Short String
```

```vb
Module Example
   Public Sub Main()
      Dim header As String = "* A Short String. *"
      Console.WriteLine(header)
      Console.WriteLine(header.Trim( { " "c, "*"c, "."c } ))
   End Sub
End Module
' The example displays the following output:
'       * A Short String. *
'       A Short String
```

## <a name="trimend"></a><span data-ttu-id="dd4d2-122">TrimEnd</span><span class="sxs-lookup"><span data-stu-id="dd4d2-122">TrimEnd</span></span>

<span data-ttu-id="dd4d2-123">O método [String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) remove os caracteres do final de uma cadeia de caracteres, criando um novo objeto de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-123">The [String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="dd4d2-124">Uma matriz de caracteres é passada para este método para especificar os caracteres a seres removidos.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-124">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="dd4d2-125">A ordem dos elementos na matriz de caracteres não afeta a operação de corte.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-125">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="dd4d2-126">O corte é interrompido quando um caractere não especificado na matriz é encontrado.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-126">The trim stops when a character not specified in the array is found.</span></span>

<span data-ttu-id="dd4d2-127">O exemplo a seguir remove as últimas letras de uma cadeia de caracteres usando o método TrimEnd.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-127">The following example removes the last letters of a string using the TrimEnd method.</span></span> <span data-ttu-id="dd4d2-128">Neste exemplo, as posições do caractere `'r'` e do caractere `'W'` estão invertidas para ilustrar que a ordem dos caracteres na matriz não importa.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-128">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="dd4d2-129">Observe que este código remove a última palavra de `MyString` mais uma parte da primeira.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-129">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>

```csharp
string MyString = "Hello World!";
char[] MyChar = {'r','o','W','l','d','!',' '};
string NewString = MyString.TrimEnd(MyChar);
Console.WriteLine(NewString);
```

```vb
Dim MyString As String = "Hello World!"
Dim MyChar() As Char = {"r","o","W","l","d","!"," "}
Dim NewString As String = MyString.TrimEnd(MyChar)
Console.WriteLine(NewString)
```

<span data-ttu-id="dd4d2-130">Esse código exibe `He` no console.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-130">This code displays `He` to the console.</span></span>

<span data-ttu-id="dd4d2-131">O exemplo a seguir remove as últimas palavras de uma cadeia de caracteres usando o método [TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])).</span><span class="sxs-lookup"><span data-stu-id="dd4d2-131">The following example removes the last word of a string using the [TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) method.</span></span> <span data-ttu-id="dd4d2-132">Nesse código, há uma vírgula após a palavra `Hello` e, como a vírgula não está especificada na matriz de caracteres para cortar, o corte termina na vírgula.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-132">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>

```csharp
string MyString = "Hello, World!";
char[] MyChar = {'r','o','W','l','d','!',' '};
string NewString = MyString.TrimEnd(MyChar);
Console.WriteLine(NewString);
```

```vb
Dim MyString As String = "Hello, World!"
Dim MyChar() As Char = {"r","o","W","l","d","!"," "}
Dim NewString As String = MyString.TrimEnd(MyChar)
Console.WriteLine(NewString)
```

<span data-ttu-id="dd4d2-133">Esse código exibe `Hello,` no console.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-133">This code displays `Hello,` to the console.</span></span>

## <a name="trimstart"></a><span data-ttu-id="dd4d2-134">TrimStart</span><span class="sxs-lookup"><span data-stu-id="dd4d2-134">TrimStart</span></span>

<span data-ttu-id="dd4d2-135">O método [String.TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) é semelhante ao método [String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])), exceto que ele cria uma nova cadeia de caracteres removendo caracteres do início de um objeto de cadeia de caracteres existente.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-135">The [String.TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) method is similar to the [String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="dd4d2-136">Uma matriz de caracteres é passada para o método [TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) para especificar os caracteres a serem removidos.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-136">An array of characters is passed to the [TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) method to specify the characters to be removed.</span></span> <span data-ttu-id="dd4d2-137">Assim como acontece com o método [TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])), a ordem dos elementos na matriz de caracteres não afeta a operação de corte.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-137">As with the [TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="dd4d2-138">O corte é interrompido quando um caractere não especificado na matriz é encontrado.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-138">The trim stops when a character not specified in the array is found.</span></span>

<span data-ttu-id="dd4d2-139">O exemplo a seguir remove a primeira palavra de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-139">The following example removes the first word of a string.</span></span> <span data-ttu-id="dd4d2-140">Neste exemplo, as posições do caractere `'l'` e do caractere `'H'` estão invertidas para ilustrar que a ordem dos caracteres na matriz não importa.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-140">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>

```csharp
string MyString = "Hello World!";
char[] MyChar = {'e', 'H','l','o',' ' };
string NewString = MyString.TrimStart(MyChar);
Console.WriteLine(NewString);
```

```vb
Dim MyString As String = "Hello World!"
Dim MyChar() As Char = {"e","H","l","o"," " }
Dim NewString As String = MyString.TrimStart(MyChar)
Console.WriteLine(NewString)
```

<span data-ttu-id="dd4d2-141">Esse código exibe `World!` no console.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-141">This code displays `World!` to the console.</span></span>

## <a name="remove"></a><span data-ttu-id="dd4d2-142">Remover</span><span class="sxs-lookup"><span data-stu-id="dd4d2-142">Remove</span></span>

<span data-ttu-id="dd4d2-143">O método [String.Remove](https://docs.microsoft.com/dotnet/core/api/System.String.Remove(System.Int32)) remove um número especificado de caracteres que começam em uma posição especificada em uma cadeia de caracteres existente.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-143">The [String.Remove](https://docs.microsoft.com/dotnet/core/api/System.String.Remove(System.Int32)) method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="dd4d2-144">Este método assume um índice baseado em zero.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-144">This method assumes a zero-based index.</span></span>

<span data-ttu-id="dd4d2-145">O exemplo a seguir remove dez caracteres de uma cadeia de caracteres começando na posição cinco de um índice baseado em zero da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-145">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>

```csharp
string MyString = "Hello Beautiful World!";
Console.WriteLine(MyString.Remove(5,10));
// The example displays the following output:
//         Hello World!  
```

```vb
Dim MyString As String = "Hello Beautiful World!"
Console.WriteLine(MyString.Remove(5,10))
' The example displays the following output:
'         Hello World!
```

<span data-ttu-id="dd4d2-146">Você também pode remover um caractere ou uma subcadeia de caracteres especificada de uma cadeia de caracteres chamando o método [String.Replace(String, String)](https://docs.microsoft.com/dotnet/core/api/System.String.Replace(System.String,System.String)) e especificando uma cadeia de caracteres vazia ([String.Empty](https://docs.microsoft.com/dotnet/core/api/System.String.Empty)) como a substituição.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-146">You can also remove a specified character or substring from a string by calling the [String.Replace(String, String)](https://docs.microsoft.com/dotnet/core/api/System.String.Replace(System.String,System.String)) method and specifying an empty string ([String.Empty](https://docs.microsoft.com/dotnet/core/api/System.String.Empty)) as the replacement.</span></span> <span data-ttu-id="dd4d2-147">O exemplo a seguir remove todas as vírgulas de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dd4d2-147">The following example removes all commas from a string.</span></span>

```csharp
using System;

public class Example
{
   public static void Main()
   {
      String phrase = "a cold, dark night";
      Console.WriteLine("Before: {0}", phrase);
      phrase = phrase.Replace(",", "");
      Console.WriteLine("After: {0}", phrase);
   }
}
// The example displays the following output:
//       Before: a cold, dark night
//       After: a cold dark night
```

```vb
Module Example
   Public Sub Main()
      Dim phrase As String = "a cold, dark night"
      Console.WriteLine("Before: {0}", phrase)
      phrase = phrase.Replace(",", "")
      Console.WriteLine("After: {0}", phrase)
   End Sub
End Module
' The example displays the following output:
'       Before: a cold, dark night
'       After: a cold dark night
```

## <a name="see-also"></a><span data-ttu-id="dd4d2-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd4d2-148">See Also</span></span>

[<span data-ttu-id="dd4d2-149">Operações básicas de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="dd4d2-149">Basic string operations</span></span>](basic-string-operations.md)


