---
title: Como converter entre cadeias de caracteres hexadecimais e tipos numéricos – guia de C# programação
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: e5013891db827e27b3cda55135fff4ee287cfcb4
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423144"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="2d9cf-102">Como converter entre cadeias de caracteres hexadecimais e tipos numéricos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="2d9cf-102">How to: Convert Between Hexadecimal Strings and Numeric Types (C# Programming Guide)</span></span>
<span data-ttu-id="2d9cf-103">Estes exemplos mostram como realizar as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="2d9cf-103">These examples show you how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="2d9cf-104">Obter o valor hexadecimal de cada caractere em uma [cadeia de caracteres](../../language-reference/builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="2d9cf-104">Obtain the hexadecimal value of each character in a [string](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="2d9cf-105">Obter o [char](../../language-reference/keywords/char.md) que corresponde a cada valor em uma cadeia de caracteres hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="2d9cf-105">Obtain the [char](../../language-reference/keywords/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
- <span data-ttu-id="2d9cf-106">Converter um `string` hexadecimal em um [int](../../language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="2d9cf-106">Convert a hexadecimal `string` to an [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
- <span data-ttu-id="2d9cf-107">Converter um `string` hexadecimal em um [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="2d9cf-107">Convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>  
  
- <span data-ttu-id="2d9cf-108">Como converter uma matriz de [bytes](../../language-reference/builtin-types/integral-numeric-types.md) em um `string` hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="2d9cf-108">Convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d9cf-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2d9cf-109">Example</span></span>  
 <span data-ttu-id="2d9cf-110">Este exemplo gera o valor hexadecimal de cada caractere em um `string`.</span><span class="sxs-lookup"><span data-stu-id="2d9cf-110">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="2d9cf-111">Primeiro, ele analisa o `string` como uma matriz de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2d9cf-111">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="2d9cf-112">Em seguida, ele chama <xref:System.Convert.ToInt32%28System.Char%29> em cada caractere para obter seu valor numérico.</span><span class="sxs-lookup"><span data-stu-id="2d9cf-112">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="2d9cf-113">Por fim, ele formata o número como sua representação hexadecimal em um `string`.</span><span class="sxs-lookup"><span data-stu-id="2d9cf-113">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="2d9cf-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2d9cf-114">Example</span></span>  
 <span data-ttu-id="2d9cf-115">Este exemplo analisa um `string` de valores hexadecimais e gera o caractere correspondente a cada valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="2d9cf-115">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="2d9cf-116">Primeiro, ele chama o método [Split(Char\[\])](xref:System.String.Split(System.Char[])) para obter cada valor hexadecimal como um `string` individual em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="2d9cf-116">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="2d9cf-117">Em seguida, ele chama <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> para converter o valor hexadecimal em um valor decimal representado como um [int](../../language-reference/builtin-types/integral-numeric-types.md). Ele mostra duas maneiras diferentes de obter o caractere correspondente a esse código de caractere.</span><span class="sxs-lookup"><span data-stu-id="2d9cf-117">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="2d9cf-118">A primeira técnica usa <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, que retorna o caractere correspondente ao argumento de inteiro como um `string`.</span><span class="sxs-lookup"><span data-stu-id="2d9cf-118">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="2d9cf-119">A segunda técnica converte explicitamente o `int` em um [char](../../language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="2d9cf-119">The second technique explicitly casts the `int` to a [char](../../language-reference/keywords/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="2d9cf-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2d9cf-120">Example</span></span>  
 <span data-ttu-id="2d9cf-121">Este exemplo mostra outra maneira de converter um hexadecimal `string` em um inteiro, chamando o método <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29>.</span><span class="sxs-lookup"><span data-stu-id="2d9cf-121">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="2d9cf-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2d9cf-122">Example</span></span>  
 <span data-ttu-id="2d9cf-123">O exemplo a seguir mostra como converter um hexadecimal `string` para um [float](../../language-reference/builtin-types/floating-point-numeric-types.md) usando a classe <xref:System.BitConverter?displayProperty=nameWithType> e o método <xref:System.UInt32.Parse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2d9cf-123">The following example shows how to convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="2d9cf-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2d9cf-124">Example</span></span>  
 <span data-ttu-id="2d9cf-125">O exemplo a seguir mostra como converter uma matriz de [bytes](../../language-reference/builtin-types/integral-numeric-types.md) em uma cadeia de caracteres hexadecimal usando a classe <xref:System.BitConverter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2d9cf-125">The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="2d9cf-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d9cf-126">See also</span></span>

- [<span data-ttu-id="2d9cf-127">Cadeias de Caracteres de Formato Numérico Padrão</span><span class="sxs-lookup"><span data-stu-id="2d9cf-127">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="2d9cf-128">Tipos</span><span class="sxs-lookup"><span data-stu-id="2d9cf-128">Types</span></span>](./index.md)
- [<span data-ttu-id="2d9cf-129">Como determinar se uma cadeia de caracteres representa um valor numérico</span><span class="sxs-lookup"><span data-stu-id="2d9cf-129">How to: Determine Whether a String Represents a Numeric Value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
