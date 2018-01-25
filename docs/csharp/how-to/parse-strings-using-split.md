---
title: Como analisar cadeias de caracteres usando String.Split (Guia do C#)
description: "O String.Split retorna uma matriz de divisão de cadeias de caracteres com base em um conjunto de delimitadores. Esta á uma maneira fácil de analisar cadeias de caracteres."
ms.date: 01/03/2018
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
author: BillWagner
ms.author: wiwagn
ms.custom: mvc
ms.openlocfilehash: fc1032f2cdf6706ec933323643dbf6ecff3e9f6f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a><span data-ttu-id="b4120-104">Como analisar cadeias de caracteres usando String.Split (Guia do C#)</span><span class="sxs-lookup"><span data-stu-id="b4120-104">How to: Parse Strings Using String.Split (C# Guide)</span></span>

<span data-ttu-id="b4120-105">O método <xref:System.String.Split%2A?displayProperty=nameWithType> cria uma matriz de subcadeias, dividindo a cadeia de caracteres de entrada com base em um ou mais delimitadores.</span><span class="sxs-lookup"><span data-stu-id="b4120-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="b4120-106">Geralmente essa é a maneira mais fácil de separar uma cadeia de caracteres em limites de palavra.</span><span class="sxs-lookup"><span data-stu-id="b4120-106">It is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="b4120-107">Ele também é usado para dividir cadeias de caracteres em outros caracteres específicos ou cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b4120-107">It is also used to split strings on other specific characters or strings.</span></span>

<span data-ttu-id="b4120-108">O código a seguir divide uma frase comum em uma matriz de cadeias de caracteres para cada palavra.</span><span class="sxs-lookup"><span data-stu-id="b4120-108">The following code splits a common phrase into an array of strings for each word.</span></span>
<span data-ttu-id="b4120-109">Experimente você mesmo, pressionando o botão *Executar*.</span><span class="sxs-lookup"><span data-stu-id="b4120-109">Try it yourself by pressing the *Run* button.</span></span>

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

<span data-ttu-id="b4120-110">Cada instância de um caractere separador produz um valor na matriz retornada.</span><span class="sxs-lookup"><span data-stu-id="b4120-110">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="b4120-111">Caracteres separadores consecutivos produzem a cadeia de caracteres vazia como um valor na matriz retornada.</span><span class="sxs-lookup"><span data-stu-id="b4120-111">Consecutive separator characters produce the empty string as a value in the returned array.</span></span>  <span data-ttu-id="b4120-112">Você pode ver isso no exemplo a seguir, que usa espaço como um separador:</span><span class="sxs-lookup"><span data-stu-id="b4120-112">You can see this in the following example, which uses space as a separator:</span></span>

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

<span data-ttu-id="b4120-113">Esse comportamento facilita para formatos como arquivos CSV (valores separados por vírgula) que representam dados de tabela.</span><span class="sxs-lookup"><span data-stu-id="b4120-113">This behavior makes it easier for formats like comma separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="b4120-114">Vírgulas consecutivas representam uma coluna em branco.</span><span class="sxs-lookup"><span data-stu-id="b4120-114">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="b4120-115">Você pode passar um parâmetro <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=fullName> opcional para excluir as cadeias de caracteres vazias da matriz retornada.</span><span class="sxs-lookup"><span data-stu-id="b4120-115">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=fullName> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="b4120-116">Para um processamento mais complicado da coleção retornada, você pode usar o [LINQ](../programming-guide/concepts/linq/index.md) para manipular a sequência de resultado.</span><span class="sxs-lookup"><span data-stu-id="b4120-116">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>    

<span data-ttu-id="b4120-117">O <xref:System.String.Split%2A?displayProperty=nameWithType> pode usar vários caracteres separadores.</span><span class="sxs-lookup"><span data-stu-id="b4120-117"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span> <span data-ttu-id="b4120-118">O exemplo a seguir utiliza espaços, vírgulas, pontos, dois-pontos e tabulações, todos passados em uma matriz que contém esses caracteres de separação para <xref:System.String.Split%2A>.</span><span class="sxs-lookup"><span data-stu-id="b4120-118">The following example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters, to <xref:System.String.Split%2A>.</span></span>  <span data-ttu-id="b4120-119">O loop, na parte inferior do código, exibe cada uma das palavras na matriz retornada.</span><span class="sxs-lookup"><span data-stu-id="b4120-119">The loop at the bottom of the code displays each of the words in the returned array.</span></span>  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

<span data-ttu-id="b4120-120">As instâncias consecutivas de qualquer separador produzem a cadeia de caracteres vazia na matriz de saída:</span><span class="sxs-lookup"><span data-stu-id="b4120-120">Consecutive instances of any separator produce the empty string in the output array:</span></span>

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<span data-ttu-id="b4120-121">O <xref:System.String.Split%2A?displayProperty=nameWithType> pode receber uma matriz de cadeias de caracteres (sequências de caracteres que atuam como separadores para analisar a cadeia de caracteres de destino, em vez de um único caractere).</span><span class="sxs-lookup"><span data-stu-id="b4120-121"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

<span data-ttu-id="b4120-122">Você pode experimentar estes exemplos examinando o código em nosso [repositório GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings)</span><span class="sxs-lookup"><span data-stu-id="b4120-122">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings)</span></span>

## <a name="see-also"></a><span data-ttu-id="b4120-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4120-123">See Also</span></span>  
 [<span data-ttu-id="b4120-124">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b4120-124">C# Programming Guide</span></span>](../programming-guide/index.md)  
 [<span data-ttu-id="b4120-125">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="b4120-125">Strings</span></span>](../programming-guide/strings/index.md)  
 [<span data-ttu-id="b4120-126">Expressões regulares do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b4120-126">.NET Framework Regular Expressions</span></span>](https://msdn.microsoft.com/library/hs600312)
