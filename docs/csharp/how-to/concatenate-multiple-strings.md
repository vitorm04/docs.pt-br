---
title: "Como concatenar várias cadeias de caracteres (Guia de C#)"
description: "Há várias maneiras para concatenar cadeias de caracteres em C#. Conheça as opções e os motivos subjacentes por trás de diferentes escolhas."
ms.date: 01/11/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a4bc5e04edba48065746b96841b628ec5843c5e9
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="c4787-104">Como concatenar várias cadeias de caracteres (Guia de C#)</span><span class="sxs-lookup"><span data-stu-id="c4787-104">How to: Concatenate Multiple Strings (C# Guide)</span></span>

<span data-ttu-id="c4787-105">*Concatenação* é o processo de acrescentar uma cadeia de caracteres ao final de outra cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c4787-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="c4787-106">Concatenar cadeias de caracteres usando o operador +.</span><span class="sxs-lookup"><span data-stu-id="c4787-106">You concatenate strings by using the + operator.</span></span> <span data-ttu-id="c4787-107">Para literais de cadeia de caracteres e constantes de cadeia de caracteres, a concatenação ocorre em tempo de compilação; não ocorre nenhuma concatenação de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c4787-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="c4787-108">Para variáveis de cadeia de caracteres, a concatenação ocorre somente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c4787-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="c4787-109">O exemplo a seguir usa a concatenação para dividir um literal de cadeia de caracteres longo em cadeias de caracteres menores, a fim de melhorar a legibilidade no código-fonte.</span><span class="sxs-lookup"><span data-stu-id="c4787-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="c4787-110">Essas partes serão concatenadas em uma única cadeia de caracteres em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="c4787-110">These parts will be concatenated into a single string at compile time.</span></span> <span data-ttu-id="c4787-111">Não há custos de desempenho em tempo de execução, independentemente da quantidade de cadeias de caracteres envolvidas.</span><span class="sxs-lookup"><span data-stu-id="c4787-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  
  

<span data-ttu-id="c4787-112">Para concatenar variáveis de cadeia de caracteres, você pode usar os operadores `+` ou `+=`, a [interpolação de cadeia de caracteres](../tutorials/string-interpolation.md) ou os métodos <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> ou <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c4787-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../tutorials/string-interpolation.md) or the <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="c4787-113">O operador `+` é fácil de usar e torna o código intuitivo.</span><span class="sxs-lookup"><span data-stu-id="c4787-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="c4787-114">Mesmo ao usar vários operadores + em uma instrução, o conteúdo da cadeia de caracteres será copiada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="c4787-114">Even if you use several + operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="c4787-115">O código a seguir mostra dois exemplos de como usar o operador `+` para concatenar cadeias de caracteres:</span><span class="sxs-lookup"><span data-stu-id="c4787-115">The following code shows two examples of using the `+` operator to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="c4787-116">Em algumas expressões, é mais fácil concatenar cadeias de caracteres usando a interpolação de cadeia de caracteres, conforme mostra o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="c4787-116">In some expressions, it is easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
>  <span data-ttu-id="c4787-117">Em operações de concatenação de cadeia de caracteres, o compilador C# trata uma cadeia de caracteres nula da mesma maneira que uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="c4787-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="c4787-118">Outros métodos para concatenar cadeias de caracteres são <xref:System.String.Concat%2A?displayProperty=nameWithType> e <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c4787-118">Other methods to concatenate strings are <xref:System.String.Concat%2A?displayProperty=nameWithType> and <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c4787-119">Esses métodos funcionam bem quando você está criando uma cadeia de caracteres de um pequeno número de cadeias de caracteres de componente.</span><span class="sxs-lookup"><span data-stu-id="c4787-119">These methods work well when you are building a string from a small number of component strings.</span></span> <span data-ttu-id="c4787-120">Esses métodos também são uma ótima opção quando você sabe o número de cadeias de caracteres que compõem sua cadeia de caracteres concatenada.</span><span class="sxs-lookup"><span data-stu-id="c4787-120">These methdos are also a great choice when you know the number of strings that make up your concatenated string.</span></span>

<span data-ttu-id="c4787-121">Em outros casos, você pode combinar cadeias de caracteres em um loop em que você não sabe quantas cadeias de caracteres de origem você está combinando, sendo que o número real de cadeias de caracteres de origem pode ser grande demais.</span><span class="sxs-lookup"><span data-stu-id="c4787-121">In other cases you may be combining strings in a loop, where you don't know how many source strings you are combining, and the actual number of source strings may be quite large.</span></span> <span data-ttu-id="c4787-122">A classe <xref:System.Text.StringBuilder> foi projetada para esses cenários.</span><span class="sxs-lookup"><span data-stu-id="c4787-122">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="c4787-123">O código a seguir usa o método <xref:System.Text.StringBuilder.Append%2A> da classe <xref:System.Text.StringBuilder> para concatenar cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c4787-123">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="c4787-124">Você pode ler mais sobre os [motivos para escolher a concatenação de cadeia de caracteres ou a classe `StringBuilder`](xref:System.Text.StringBuilder#StringAndSB)</span><span class="sxs-lookup"><span data-stu-id="c4787-124">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB)</span></span>

<span data-ttu-id="c4787-125">Outra opção para unir cadeias de caracteres de uma coleção é usar o [LINQ](../programming-guide/concepts/linq/index.md) e o método <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c4787-125">Another option to join strings from a collection is to use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c4787-126">Esse método combina as cadeias de caracteres de origem usando uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="c4787-126">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="c4787-127">A expressão lambda faz o trabalho de adicionar cada cadeia de caracteres ao acúmulo existente.</span><span class="sxs-lookup"><span data-stu-id="c4787-127">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="c4787-128">O exemplo a seguir combina uma matriz de palavras, adicionando um espaço entre cada palavra na matriz:</span><span class="sxs-lookup"><span data-stu-id="c4787-128">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]  


## <a name="see-also"></a><span data-ttu-id="c4787-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4787-129">See Also</span></span>  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="c4787-130">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="c4787-130">C# Programming Guide</span></span>](../programming-guide/index.md)  
 [<span data-ttu-id="c4787-131">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c4787-131">Strings</span></span>](../programming-guide/strings/index.md)
