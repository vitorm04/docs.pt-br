---
title: Como converter entre cadeias de caracteres hexadecimais e tipos numéricos – guia de programação C#
description: Saiba como converter entre cadeias de caracteres hexadecimais e tipos numéricos. Consulte exemplos de código e exiba recursos adicionais disponíveis.
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: a49c4a9ee1fc19134d434d42b1eae59376c89fa4
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381795"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="1684c-104">Como converter entre cadeias de caracteres hexadecimais e tipos numéricos (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="1684c-104">How to convert between hexadecimal strings and numeric types (C# Programming Guide)</span></span>
<span data-ttu-id="1684c-105">Estes exemplos mostram como realizar as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="1684c-105">These examples show you how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="1684c-106">Obter o valor hexadecimal de cada caractere em uma [cadeia de caracteres](../../language-reference/builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="1684c-106">Obtain the hexadecimal value of each character in a [string](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="1684c-107">Obter o [char](../../language-reference/builtin-types/char.md) que corresponde a cada valor em uma cadeia de caracteres hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="1684c-107">Obtain the [char](../../language-reference/builtin-types/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
- <span data-ttu-id="1684c-108">Converter um `string` hexadecimal em um [int](../../language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="1684c-108">Convert a hexadecimal `string` to an [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
- <span data-ttu-id="1684c-109">Converter um `string` hexadecimal em um [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="1684c-109">Convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>  
  
- <span data-ttu-id="1684c-110">Como converter uma matriz de [bytes](../../language-reference/builtin-types/integral-numeric-types.md) em um `string` hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="1684c-110">Convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1684c-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1684c-111">Example</span></span>  
 <span data-ttu-id="1684c-112">Este exemplo gera o valor hexadecimal de cada caractere em um `string`.</span><span class="sxs-lookup"><span data-stu-id="1684c-112">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="1684c-113">Primeiro, ele analisa o `string` como uma matriz de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1684c-113">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="1684c-114">Em seguida, ele chama <xref:System.Convert.ToInt32%28System.Char%29> em cada caractere para obter seu valor numérico.</span><span class="sxs-lookup"><span data-stu-id="1684c-114">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="1684c-115">Por fim, ele formata o número como sua representação hexadecimal em um `string`.</span><span class="sxs-lookup"><span data-stu-id="1684c-115">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="1684c-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1684c-116">Example</span></span>  
 <span data-ttu-id="1684c-117">Este exemplo analisa um `string` de valores hexadecimais e gera o caractere correspondente a cada valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="1684c-117">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="1684c-118">Primeiro, ele chama o método [Split (Char \[ \] )](xref:System.String.Split(System.Char[])) para obter cada valor hexadecimal como um indivíduo `string` em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="1684c-118">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="1684c-119">Em seguida, ele chama <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> para converter o valor hexadecimal em um valor decimal representado como um [int](../../language-reference/builtin-types/integral-numeric-types.md). Ele mostra duas maneiras diferentes de obter o caractere correspondente a esse código de caractere.</span><span class="sxs-lookup"><span data-stu-id="1684c-119">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="1684c-120">A primeira técnica usa <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, que retorna o caractere correspondente ao argumento de inteiro como um `string`.</span><span class="sxs-lookup"><span data-stu-id="1684c-120">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="1684c-121">A segunda técnica converte explicitamente o `int` em um [char](../../language-reference/builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="1684c-121">The second technique explicitly casts the `int` to a [char](../../language-reference/builtin-types/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="1684c-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1684c-122">Example</span></span>  
 <span data-ttu-id="1684c-123">Este exemplo mostra outra maneira de converter um hexadecimal `string` em um inteiro, chamando o método <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29>.</span><span class="sxs-lookup"><span data-stu-id="1684c-123">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="1684c-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1684c-124">Example</span></span>  
 <span data-ttu-id="1684c-125">O exemplo a seguir mostra como converter um hexadecimal `string` para um [float](../../language-reference/builtin-types/floating-point-numeric-types.md) usando a classe <xref:System.BitConverter?displayProperty=nameWithType> e o método <xref:System.UInt32.Parse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1684c-125">The following example shows how to convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="1684c-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1684c-126">Example</span></span>  
 <span data-ttu-id="1684c-127">O exemplo a seguir mostra como converter uma matriz de [bytes](../../language-reference/builtin-types/integral-numeric-types.md) em uma cadeia de caracteres hexadecimal usando a classe <xref:System.BitConverter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1684c-127">The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="1684c-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="1684c-128">See also</span></span>

- [<span data-ttu-id="1684c-129">Cadeias de Caracteres de Formato Numérico Padrão</span><span class="sxs-lookup"><span data-stu-id="1684c-129">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="1684c-130">Types</span><span class="sxs-lookup"><span data-stu-id="1684c-130">Types</span></span>](./index.md)
- [<span data-ttu-id="1684c-131">Como determinar se uma cadeia de caracteres representa um valor numérico</span><span class="sxs-lookup"><span data-stu-id="1684c-131">How to determine whether a string represents a numeric value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
