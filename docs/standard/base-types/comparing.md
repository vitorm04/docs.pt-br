---
title: Comparando cadeias de caracteres
description: Comparando cadeias de caracteres
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 920ee5e8-3d61-4941-b5af-fc50eaee427c
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 47ee37886fa2662a89730e9d52ee04987e37da2f
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="comparing-strings"></a><span data-ttu-id="c01d4-104">Comparando cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="c01d4-104">Comparing strings</span></span>

<span data-ttu-id="c01d4-105">O .NET fornece vários métodos para comparar os valores de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c01d4-105">.NET provides several methods to compare the values of strings.</span></span> <span data-ttu-id="c01d4-106">A tabela a seguir lista e descreve os métodos de comparação de valores.</span><span class="sxs-lookup"><span data-stu-id="c01d4-106">The following table lists and describes the value-comparison methods.</span></span>

<span data-ttu-id="c01d4-107">Nome do método</span><span class="sxs-lookup"><span data-stu-id="c01d4-107">Method name</span></span> | <span data-ttu-id="c01d4-108">Use</span><span class="sxs-lookup"><span data-stu-id="c01d4-108">Use</span></span>
----------- | ---
<span data-ttu-id="c01d4-109">[String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c01d4-109">[String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32))</span></span> | <span data-ttu-id="c01d4-110">Compara os valores das duas cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c01d4-110">Compares the values of two strings.</span></span> <span data-ttu-id="c01d4-111">Retorna um valor inteiro.</span><span class="sxs-lookup"><span data-stu-id="c01d4-111">Returns an integer value.</span></span>
<span data-ttu-id="c01d4-112">[String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c01d4-112">[String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32))</span></span> | <span data-ttu-id="c01d4-113">Compara duas cadeias de caracteres sem considerar a cultura local.</span><span class="sxs-lookup"><span data-stu-id="c01d4-113">Compares two strings without regard to local culture.</span></span> <span data-ttu-id="c01d4-114">Retorna um valor inteiro.</span><span class="sxs-lookup"><span data-stu-id="c01d4-114">Returns an integer value.</span></span>
<span data-ttu-id="c01d4-115">[String.CompareTo](xref:System.String.CompareTo(System.String))</span><span class="sxs-lookup"><span data-stu-id="c01d4-115">[String.CompareTo](xref:System.String.CompareTo(System.String))</span></span> | <span data-ttu-id="c01d4-116">Compara o objeto atual de cadeia de caracteres a outra cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c01d4-116">Compares the current string object to another string.</span></span> <span data-ttu-id="c01d4-117">Retorna um valor inteiro.</span><span class="sxs-lookup"><span data-stu-id="c01d4-117">Returns an integer value.</span></span>
<span data-ttu-id="c01d4-118">[String.StartsWith](xref:System.String.StartsWith(System.String))</span><span class="sxs-lookup"><span data-stu-id="c01d4-118">[String.StartsWith](xref:System.String.StartsWith(System.String))</span></span> | <span data-ttu-id="c01d4-119">Determina se uma cadeia de caracteres começa com a cadeia de caracteres passada.</span><span class="sxs-lookup"><span data-stu-id="c01d4-119">Determines whether a string begins with the string passed.</span></span> <span data-ttu-id="c01d4-120">Representa um valor Booliano.</span><span class="sxs-lookup"><span data-stu-id="c01d4-120">Returns a Boolean value.</span></span>
<span data-ttu-id="c01d4-121">[String.EndsWith](xref:System.String.CompareTo(System.String))</span><span class="sxs-lookup"><span data-stu-id="c01d4-121">[String.EndsWith](xref:System.String.CompareTo(System.String))</span></span> | <span data-ttu-id="c01d4-122">Determina se uma cadeia de caracteres termina com a cadeia de caracteres passada.</span><span class="sxs-lookup"><span data-stu-id="c01d4-122">Determines whether a string ends with the string passed.</span></span> <span data-ttu-id="c01d4-123">Representa um valor Booliano.</span><span class="sxs-lookup"><span data-stu-id="c01d4-123">Returns a Boolean value.</span></span>
<span data-ttu-id="c01d4-124">[String.Equals](xref:System.String.CompareTo(System.String))</span><span class="sxs-lookup"><span data-stu-id="c01d4-124">[String.Equals](xref:System.String.CompareTo(System.String))</span></span> | <span data-ttu-id="c01d4-125">Determina se duas cadeias de caracteres são iguais.</span><span class="sxs-lookup"><span data-stu-id="c01d4-125">Determines whether two strings are the same.</span></span> <span data-ttu-id="c01d4-126">Representa um valor Booliano.</span><span class="sxs-lookup"><span data-stu-id="c01d4-126">Returns a Boolean value.</span></span>
<span data-ttu-id="c01d4-127">[String.IndexOf](xref:System.String.IndexOf(System.Char))</span><span class="sxs-lookup"><span data-stu-id="c01d4-127">[String.IndexOf](xref:System.String.IndexOf(System.Char))</span></span> | <span data-ttu-id="c01d4-128">Retorna a posição do índice de um caractere ou uma cadeia de caracteres, começando do início da cadeia de caracteres que você está examinando.</span><span class="sxs-lookup"><span data-stu-id="c01d4-128">Returns the index position of a character or string, starting from the beginning of the string you are examining.</span></span> <span data-ttu-id="c01d4-129">Retorna um valor inteiro.</span><span class="sxs-lookup"><span data-stu-id="c01d4-129">Returns an integer value.</span></span>
<span data-ttu-id="c01d4-130">[String.LastIndexOf](xref:System.String.LastIndexOf(System.Char))</span><span class="sxs-lookup"><span data-stu-id="c01d4-130">[String.LastIndexOf](xref:System.String.LastIndexOf(System.Char))</span></span> | <span data-ttu-id="c01d4-131">Retorna a posição do índice de um caractere ou uma cadeia de caracteres, começando do fim da cadeia de caracteres que você está examinando.</span><span class="sxs-lookup"><span data-stu-id="c01d4-131">Returns the index position of a character or string, starting from the end of the string you are examining.</span></span> <span data-ttu-id="c01d4-132">Retorna um valor inteiro.</span><span class="sxs-lookup"><span data-stu-id="c01d4-132">Returns an integer value.</span></span>

## <a name="compare"></a><span data-ttu-id="c01d4-133">Comparar</span><span class="sxs-lookup"><span data-stu-id="c01d4-133">Compare</span></span>

<span data-ttu-id="c01d4-134">O método estático [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) fornece uma maneira completa de comparar duas cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c01d4-134">The static [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) method provides a thorough way of comparing two strings.</span></span> <span data-ttu-id="c01d4-135">Esse método é cultural.</span><span class="sxs-lookup"><span data-stu-id="c01d4-135">This method is culturally aware.</span></span> <span data-ttu-id="c01d4-136">Você pode usar essa função para comparar duas cadeias de caracteres ou subcadeias de duas cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c01d4-136">You can use this function to compare two strings or substrings of two strings.</span></span> <span data-ttu-id="c01d4-137">Além disso, sobrecargas são fornecidas para considerar ou ignorar a variação cultural ou de caso.</span><span class="sxs-lookup"><span data-stu-id="c01d4-137">Additionally, overloads are provided that regard or disregard case and cultural variance.</span></span> <span data-ttu-id="c01d4-138">A tabela a seguir mostra os três valores inteiros que esse método pode retornar.</span><span class="sxs-lookup"><span data-stu-id="c01d4-138">The following table shows the three integer values that this method might return.</span></span> 

<span data-ttu-id="c01d4-139">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c01d4-139">Return value</span></span> | <span data-ttu-id="c01d4-140">Condição</span><span class="sxs-lookup"><span data-stu-id="c01d4-140">Condition</span></span>
------------ | ---------
<span data-ttu-id="c01d4-141">Um inteiro negativo</span><span class="sxs-lookup"><span data-stu-id="c01d4-141">A negative integer</span></span> | <span data-ttu-id="c01d4-142">A primeira cadeia de caracteres precede a segunda cadeia de caracteres na ordem de classificação ou a primeira cadeia de caracteres é `null`.</span><span class="sxs-lookup"><span data-stu-id="c01d4-142">The first string precedes the second string in the sort order, or the first string is `null`.</span></span>
<span data-ttu-id="c01d4-143">0</span><span class="sxs-lookup"><span data-stu-id="c01d4-143">0</span></span> | <span data-ttu-id="c01d4-144">A primeira cadeia de caracteres e a segunda cadeia de caracteres são iguais ou ambas são `null`.</span><span class="sxs-lookup"><span data-stu-id="c01d4-144">The first string and the second string are equal, or both strings are `null`.</span></span>
<span data-ttu-id="c01d4-145">Um número inteiro positivo ou 1</span><span class="sxs-lookup"><span data-stu-id="c01d4-145">A positive integer, or 1</span></span> | <span data-ttu-id="c01d4-146">A primeira cadeia de caracteres precede a segunda cadeia de caracteres na ordem de classificação ou a segunda cadeia de caracteres é nula.</span><span class="sxs-lookup"><span data-stu-id="c01d4-146">The first string follows the second string in the sort order, or the second string is null.</span></span>
 
> [!IMPORTANT]
> <span data-ttu-id="c01d4-147">O método [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) destina-se principalmente para uso em ordenação ou classificação de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c01d4-147">The [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="c01d4-148">Você não deve usar o método [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) para testar a igualdade (ou seja, para procurar explicitamente um valor retornado de 0 sem considerar se uma cadeia de caracteres é menor que ou maior que a outra).</span><span class="sxs-lookup"><span data-stu-id="c01d4-148">You should not use the [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="c01d4-149">Em vez disso, para determinar se duas cadeias de caracteres são iguais, use o método [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)).</span><span class="sxs-lookup"><span data-stu-id="c01d4-149">Instead, to determine whether two strings are equal, use the [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) method.</span></span>

<span data-ttu-id="c01d4-150">O exemplo a seguir usa o método [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) para determinar os valores relativos das duas cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c01d4-150">The following example uses the [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) method to determine the relative values of two strings.</span></span>

```csharp
string string1 = "Hello World!";
Console.WriteLine(String.Compare(string1, "Hello World?"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(String.Compare(string1, "Hello World?"))
```

<span data-ttu-id="c01d4-151">Este exemplo exibe `-1` no console.</span><span class="sxs-lookup"><span data-stu-id="c01d4-151">This example displays `-1` to the console.</span></span>

## <a name="compareordinal"></a><span data-ttu-id="c01d4-152">CompareOrdinal</span><span class="sxs-lookup"><span data-stu-id="c01d4-152">CompareOrdinal</span></span>

<span data-ttu-id="c01d4-153">O método [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) compara dois objetos de cadeia de caracteres sem considerar a cultura local.</span><span class="sxs-lookup"><span data-stu-id="c01d4-153">The [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) method compares two string objects without considering the local culture.</span></span> <span data-ttu-id="c01d4-154">Os valores de retorno desse método são idênticos aos valores retornados pelo método `Compare` na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="c01d4-154">The return values of this method are identical to the values returned by the `Compare` method in the previous table.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c01d4-155">O método [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) destina-se principalmente para uso em ordenação ou classificação de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c01d4-155">The [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="c01d4-156">Você não deve usar o método [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) para testar a igualdade (ou seja, para procurar explicitamente um valor retornado de 0 sem considerar se uma cadeia de caracteres é menor ou maior que a outra).</span><span class="sxs-lookup"><span data-stu-id="c01d4-156">You should not use the [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="c01d4-157">Em vez disso, para determinar se duas cadeias de caracteres são iguais, use o método [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)).</span><span class="sxs-lookup"><span data-stu-id="c01d4-157">Instead, to determine whether two strings are equal, use the [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) method.</span></span>

<span data-ttu-id="c01d4-158">O exemplo a seguir usa o método `CompareOrdinal` para comparar os valores de duas cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c01d4-158">The following example uses the `CompareOrdinal` method to compare the values of two strings.</span></span>

```csharp
string string1 = "Hello World!";
Console.WriteLine(String.CompareOrdinal(string1, "hello world!"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(String.CompareOrdinal(string1, "hello world!"))
```

<span data-ttu-id="c01d4-159">Este exemplo exibe `-32` no console.</span><span class="sxs-lookup"><span data-stu-id="c01d4-159">This example displays `-32` to the console.</span></span>

## <a name="compareto"></a><span data-ttu-id="c01d4-160">CompareTo</span><span class="sxs-lookup"><span data-stu-id="c01d4-160">CompareTo</span></span>

<span data-ttu-id="c01d4-161">O método [String.CompareTo](xref:System.String.CompareTo(System.String)) compara a cadeia de caracteres que o objeto atual de cadeia de caracteres encapsula com outro objeto ou cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c01d4-161">The [String.CompareTo](xref:System.String.CompareTo(System.String)) method compares the string that the current string object encapsulates to another string or object.</span></span> <span data-ttu-id="c01d4-162">Os valores de retorno desse método são idênticos aos valores retornados pelo método `String.Compare` na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="c01d4-162">The return values of this method are identical to the values returned by the `String.Compare` method in the previous table.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c01d4-163">O método [String.CompareTo](xref:System.String.CompareTo(System.String)) destina-se principalmente para uso em ordenação ou classificação de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c01d4-163">The [String.CompareTo](xref:System.String.CompareTo(System.String)) method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="c01d4-164">Você não deve usar o método [String.CompareTo](xref:System.String.CompareTo(System.String)) para testar a igualdade (ou seja, para procurar explicitamente um valor retornado de 0 sem considerar se uma cadeia de caracteres é menor ou maior que a outra).</span><span class="sxs-lookup"><span data-stu-id="c01d4-164">You should not use the [String.CompareTo](xref:System.String.CompareTo(System.String)) method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="c01d4-165">Em vez disso, para determinar se duas cadeias de caracteres são iguais, use o método [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)).</span><span class="sxs-lookup"><span data-stu-id="c01d4-165">Instead, to determine whether two strings are equal, use the [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) method.</span></span>

<span data-ttu-id="c01d4-166">O exemplo a seguir usa o método `String.CompareTo` para comparar o objeto `string1` ao objeto `string2`.</span><span class="sxs-lookup"><span data-stu-id="c01d4-166">The following example uses the `String.CompareTo` method to compare the `string1` object to the `string2` object.</span></span>

```csharp
string string1 = "Hello World";
string string2 = "Hello World!";
int MyInt = string1.CompareTo(string2);
Console.WriteLine( MyInt );
```

```vb
Dim string1 As String = "Hello World"
Dim string2 As String = "Hello World!"
Dim MyInt As Integer = string1.CompareTo(string2)
Console.WriteLine(MyInt)
```

<span data-ttu-id="c01d4-167">Este exemplo exibe `-1` no console.</span><span class="sxs-lookup"><span data-stu-id="c01d4-167">This example displays `-1` to the console.</span></span>

## <a name="equals"></a><span data-ttu-id="c01d4-168">Igual a</span><span class="sxs-lookup"><span data-stu-id="c01d4-168">Equals</span></span>

<span data-ttu-id="c01d4-169">O método [String.Equals](xref:System.String.CompareTo(System.String)) pode facilmente determinar se duas cadeias de caracteres são as mesmas.</span><span class="sxs-lookup"><span data-stu-id="c01d4-169">The [String.Equals](xref:System.String.CompareTo(System.String)) method can easily determine if two strings are the same.</span></span> <span data-ttu-id="c01d4-170">Esse método que diferencia maiúsculas de minúsculas retorna um valor Booliano `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="c01d4-170">This case-sensitive method returns a `true` or `false` Boolean value.</span></span> <span data-ttu-id="c01d4-171">Ele pode ser usado de uma classe existente, conforme ilustrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c01d4-171">It can be used from an existing class, as illustrated in the next example.</span></span> <span data-ttu-id="c01d4-172">O exemplo a seguir usa o método `Equals` para determinar se um objeto de cadeia de caracteres contém a frase "Hello World".</span><span class="sxs-lookup"><span data-stu-id="c01d4-172">The following example uses the `Equals` method to determine whether a string object contains the phrase "Hello World".</span></span>

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.Equals("Hello World"));
```

```vb
Dim string1 As String = "Hello World"
Console.WriteLine(string1.Equals("Hello World"))
```

<span data-ttu-id="c01d4-173">Este exemplo exibe `true` no console.</span><span class="sxs-lookup"><span data-stu-id="c01d4-173">This example displays `true` to the console.</span></span>

<span data-ttu-id="c01d4-174">Esse método também pode ser usado como um método estático.</span><span class="sxs-lookup"><span data-stu-id="c01d4-174">This method can also be used as a static method.</span></span> <span data-ttu-id="c01d4-175">O exemplo a seguir compara dois objetos de cadeia de caracteres usando um método estático.</span><span class="sxs-lookup"><span data-stu-id="c01d4-175">The following example compares two string objects using a static method.</span></span>

```csharp
string string1 = "Hello World";
string string2 = "Hello World";
Console.WriteLine(String.Equals(string1, string2));
```

```vb
Dim string1 As String = "Hello World"
Dim string2 As String = "Hello World"
Console.WriteLine(String.Equals(string1, string2))
```

<span data-ttu-id="c01d4-176">Este exemplo exibe `true` no console.</span><span class="sxs-lookup"><span data-stu-id="c01d4-176">This example displays `true` to the console.</span></span>

## <a name="startswith-and-endswith"></a><span data-ttu-id="c01d4-177">StartsWith e EndsWith</span><span class="sxs-lookup"><span data-stu-id="c01d4-177">StartsWith and EndsWith</span></span>

<span data-ttu-id="c01d4-178">Você pode usar o método [String.StartsWith](xref:System.String.StartsWith(System.String)) para determinar se um objeto de cadeia de caracteres começa com os mesmos caracteres que englobam outra cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c01d4-178">You can use the [String.StartsWith](xref:System.String.StartsWith(System.String)) method to determine whether a string object begins with the same characters that encompass another string.</span></span> <span data-ttu-id="c01d4-179">Esse método que diferencia maiúsculas de minúsculas retorna `true` se o objeto atual de cadeia de caracteres começa com a cadeia de caracteres passada e `false` se não existir.</span><span class="sxs-lookup"><span data-stu-id="c01d4-179">This case-sensitive method returns `true` if the current string object begins with the passed string and `false` if it does not.</span></span> <span data-ttu-id="c01d4-180">O exemplo a seguir usa esse método para determinar se um objeto de cadeia de caracteres começa com "Hello".</span><span class="sxs-lookup"><span data-stu-id="c01d4-180">The following example uses this method to determine if a string object begins with "Hello".</span></span>

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.StartsWith("Hello"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.StartsWith("Hello"))
```

<span data-ttu-id="c01d4-181">Este exemplo exibe `true` no console.</span><span class="sxs-lookup"><span data-stu-id="c01d4-181">This example displays `true` to the console.</span></span>

<span data-ttu-id="c01d4-182">O método [String.EndsWith](xref:System.String.CompareTo(System.String)) compara uma cadeia de caracteres passada com os caracteres que existem no final do objeto de cadeia de caracteres atual.</span><span class="sxs-lookup"><span data-stu-id="c01d4-182">The [String.EndsWith](xref:System.String.CompareTo(System.String)) method compares a passed string to the characters that exist at the end of the current string object.</span></span> <span data-ttu-id="c01d4-183">Ele também retorna um valor Booliano.</span><span class="sxs-lookup"><span data-stu-id="c01d4-183">It also returns a Boolean value.</span></span> <span data-ttu-id="c01d4-184">O exemplo a seguir verifica o fim de uma cadeia de caracteres usando o método `EndsWith`.</span><span class="sxs-lookup"><span data-stu-id="c01d4-184">The following example checks the end of a string using the `EndsWith` method.</span></span>

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.EndsWith("Hello"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.EndsWith("Hello"))
```

<span data-ttu-id="c01d4-185">Este exemplo exibe `false` no console.</span><span class="sxs-lookup"><span data-stu-id="c01d4-185">This example displays `false` to the console.</span></span>

## <a name="indexof-and-lastindexof"></a><span data-ttu-id="c01d4-186">IndexOf e LastIndexOf</span><span class="sxs-lookup"><span data-stu-id="c01d4-186">IndexOf and LastIndexOf</span></span>

<span data-ttu-id="c01d4-187">Você pode usar o método [String.IndexOf](xref:System.String.IndexOf(System.Char)) para determinar a posição da primeira ocorrência de um determinado caractere dentro de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c01d4-187">You can use the [String.IndexOf](xref:System.String.IndexOf(System.Char)) method to determine the position of the first occurrence of a particular character within a string.</span></span> <span data-ttu-id="c01d4-188">Esse método que diferencia maiúsculas de minúsculas inicia a contagem do início de uma cadeia de caracteres e retorna a posição de um caractere passado usando um índice baseado em zero.</span><span class="sxs-lookup"><span data-stu-id="c01d4-188">This case-sensitive method starts counting from the beginning of a string and returns the position of a passed character using a zero-based index.</span></span> <span data-ttu-id="c01d4-189">Se o caractere não for encontrado, um valor de -1 será retornado.</span><span class="sxs-lookup"><span data-stu-id="c01d4-189">If the character cannot be found, a value of –1 is returned.</span></span>

<span data-ttu-id="c01d4-190">O exemplo a seguir usa o método `IndexOf` para pesquisar a primeira ocorrência do caractere '`l`' em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c01d4-190">The following example uses the `IndexOf` method to search for the first occurrence of the '`l`' character in a string.</span></span>

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.IndexOf('l'));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.IndexOf("l"))
```

<span data-ttu-id="c01d4-191">Este exemplo exibe `2` no console.</span><span class="sxs-lookup"><span data-stu-id="c01d4-191">This example displays `2` to the console.</span></span>

<span data-ttu-id="c01d4-192">O método [String.LastIndexOf](xref:System.String.LastIndexOf(System.Char)) é semelhante ao método `String.IndexOf`, exceto que ele retorna a posição da última ocorrência de um determinado caractere dentro de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c01d4-192">The [String.LastIndexOf](xref:System.String.LastIndexOf(System.Char)) method is similar to the `String.IndexOf` method except that it returns the position of the last occurrence of a particular character within a string.</span></span> <span data-ttu-id="c01d4-193">Ele diferencia maiúsculas de minúsculas e usa um índice baseado em zero.</span><span class="sxs-lookup"><span data-stu-id="c01d4-193">It is case-sensitive and uses a zero-based index.</span></span> 

<span data-ttu-id="c01d4-194">O exemplo a seguir usa o método `LastIndexOf` para pesquisar a última ocorrência do caractere '`l`' em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c01d4-194">The following example uses the `LastIndexOf` method to search for the last occurrence of the '`l`' character in a string.</span></span>

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.LastIndexOf('l'));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.LastIndexOf("l"))
```

<span data-ttu-id="c01d4-195">Este exemplo exibe `9` no console.</span><span class="sxs-lookup"><span data-stu-id="c01d4-195">This example displays `9` to the console.</span></span>

<span data-ttu-id="c01d4-196">Os dois métodos são úteis quando usados em conjunto com o método [String.Remove](xref:System.String.Remove(System.Int32)).</span><span class="sxs-lookup"><span data-stu-id="c01d4-196">Both methods are useful when used in conjunction with the [String.Remove](xref:System.String.Remove(System.Int32)) method.</span></span> <span data-ttu-id="c01d4-197">Você pode usar tanto o método `IndexOf` quanto o `LastIndexOf` para recuperar a posição de um caractere e, em seguida, fornecer essa posição para o `Remove method` para remover um caractere ou uma palavra que começa com esse caractere.</span><span class="sxs-lookup"><span data-stu-id="c01d4-197">You can use either the `IndexOf` or `LastIndexOf` methods to retrieve the position of a character, and then supply that position to the `Remove method` in order to remove a character or a word that begins with that character.</span></span>

## <a name="see-also"></a><span data-ttu-id="c01d4-198">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c01d4-198">See Also</span></span>

[<span data-ttu-id="c01d4-199">Operações básicas de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="c01d4-199">Basic string operations</span></span>](basic-string-operations.md)













