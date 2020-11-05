---
title: Dividir cadeias de caracteres usando String. Split (guia C#)
description: O método Split retorna uma matriz de cadeias de caracteres divididas de um conjunto de delimitadores. É uma maneira fácil de extrair subsequências de uma cadeia de caracteres.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: 5361a3c60905edd19b180c5ddb14064a85f64337
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400494"
---
# <a name="how-to-separate-strings-using-stringsplit-in-c"></a><span data-ttu-id="4f4a8-104">Como separar cadeias de caracteres usando String. Split em C\#</span><span class="sxs-lookup"><span data-stu-id="4f4a8-104">How to separate strings using String.Split in C\#</span></span>

<span data-ttu-id="4f4a8-105">O método <xref:System.String.Split%2A?displayProperty=nameWithType> cria uma matriz de subcadeias, dividindo a cadeia de caracteres de entrada com base em um ou mais delimitadores.</span><span class="sxs-lookup"><span data-stu-id="4f4a8-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="4f4a8-106">Esse método é geralmente a maneira mais fácil de separar uma cadeia de caracteres em limites de palavras.</span><span class="sxs-lookup"><span data-stu-id="4f4a8-106">This method is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="4f4a8-107">Ele também é usado para dividir cadeias de caracteres em outras cadeias ou caractere específico.</span><span class="sxs-lookup"><span data-stu-id="4f4a8-107">It's also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="4f4a8-108">O código a seguir divide uma frase comum em uma matriz de cadeias de caracteres para cada palavra.</span><span class="sxs-lookup"><span data-stu-id="4f4a8-108">The following code splits a common phrase into an array of strings for each word.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet1":::

<span data-ttu-id="4f4a8-109">Cada instância de um caractere separador produz um valor na matriz retornada.</span><span class="sxs-lookup"><span data-stu-id="4f4a8-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="4f4a8-110">Caracteres separadores consecutivos produzem a cadeia de caracteres vazia como um valor na matriz retornada.</span><span class="sxs-lookup"><span data-stu-id="4f4a8-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span> <span data-ttu-id="4f4a8-111">Você pode ver como uma cadeia de caracteres vazia é criada no exemplo a seguir, que usa o caractere de espaço como um separador.</span><span class="sxs-lookup"><span data-stu-id="4f4a8-111">You can see how an empty string is created in the following example, which uses the space character as a separator.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet2":::

<span data-ttu-id="4f4a8-112">Esse comportamento torna mais fácil para formatos como arquivos de valores separados por vírgulas (CSV) que representam dados tabulares.</span><span class="sxs-lookup"><span data-stu-id="4f4a8-112">This behavior makes it easier for formats like comma-separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="4f4a8-113">Vírgulas consecutivas representam uma coluna em branco.</span><span class="sxs-lookup"><span data-stu-id="4f4a8-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="4f4a8-114">Você pode passar um parâmetro <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> opcional para excluir as cadeias de caracteres vazias da matriz retornada.</span><span class="sxs-lookup"><span data-stu-id="4f4a8-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="4f4a8-115">Para um processamento mais complicado da coleção retornada, você pode usar o [LINQ](../programming-guide/concepts/linq/index.md) para manipular a sequência de resultado.</span><span class="sxs-lookup"><span data-stu-id="4f4a8-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="4f4a8-116">O <xref:System.String.Split%2A?displayProperty=nameWithType> pode usar vários caracteres separadores.</span><span class="sxs-lookup"><span data-stu-id="4f4a8-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="4f4a8-117">O exemplo a seguir usa espaços, vírgulas, pontos, dois-pontos e tabulações como separando caracteres, que são passados para <xref:System.String.Split%2A> em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="4f4a8-117">The following example uses spaces, commas, periods, colons, and tabs as separating characters, which are passed to <xref:System.String.Split%2A> in an array .</span></span>
<span data-ttu-id="4f4a8-118">O loop, na parte inferior do código, exibe cada uma das palavras na matriz retornada.</span><span class="sxs-lookup"><span data-stu-id="4f4a8-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet3":::

<span data-ttu-id="4f4a8-119">As instâncias consecutivas de qualquer separador produzem a cadeia de caracteres vazia na matriz de saída:</span><span class="sxs-lookup"><span data-stu-id="4f4a8-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet4":::

<span data-ttu-id="4f4a8-120">O <xref:System.String.Split%2A?displayProperty=nameWithType> pode receber uma matriz de cadeias de caracteres (sequências de caracteres que atuam como separadores para analisar a cadeia de caracteres de destino, em vez de um único caractere).</span><span class="sxs-lookup"><span data-stu-id="4f4a8-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet5":::

## <a name="see-also"></a><span data-ttu-id="4f4a8-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="4f4a8-121">See also</span></span>

- [<span data-ttu-id="4f4a8-122">Extrair elementos de uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="4f4a8-122">Extract elements from a string</span></span>](../../standard/base-types/divide-up-strings.md)
- [<span data-ttu-id="4f4a8-123">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="4f4a8-123">C# programming guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="4f4a8-124">Cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="4f4a8-124">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="4f4a8-125">Expressões regulares do .NET</span><span class="sxs-lookup"><span data-stu-id="4f4a8-125">.NET regular expressions</span></span>](../../standard/base-types/regular-expressions.md)
