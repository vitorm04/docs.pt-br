---
title: "Como converter uma cadeia de caracteres em um número (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
caps.latest.revision: 34
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 08d13e40a385ce8e9011b508b04361b2e050f904
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a><span data-ttu-id="bbf7e-102">Como converter uma cadeia de caracteres em um número (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="bbf7e-102">How to: Convert a String to a Number (C# Programming Guide)</span></span>
<span data-ttu-id="bbf7e-103">É possível converter uma [string](../../../csharp/language-reference/keywords/string.md) em um número usando os métodos na classe <xref:System.Convert> ou usando o método `TryParse` encontrado nos diversos tipos numéricos (int, long, float, etc.).</span><span class="sxs-lookup"><span data-stu-id="bbf7e-103">You can convert a [string](../../../csharp/language-reference/keywords/string.md) to a number by using methods in the <xref:System.Convert> class or by using the `TryParse` method found on the various numeric types (int, long, float, etc.).</span></span>  
  
 <span data-ttu-id="bbf7e-104">Caso haja uma cadeia de caracteres, é um pouco mais eficiente e simples chamar um método `TryParse` (por exemplo, `int.TryParse("11")`).</span><span class="sxs-lookup"><span data-stu-id="bbf7e-104">If you have a string, it is slightly more efficient and straightforward to call a `TryParse` method (for example, `int.TryParse("11")`).</span></span>  <span data-ttu-id="bbf7e-105">Usar um método `Convert` é mais útil para objetos gerais que implementam <xref:System.IConvertible>.</span><span class="sxs-lookup"><span data-stu-id="bbf7e-105">Using a `Convert` method is more useful for general objects that implement <xref:System.IConvertible>.</span></span>  
  
 <span data-ttu-id="bbf7e-106">É possível usar métodos `Parse` ou `TryParse` no tipo numérico que se espera que a cadeia de caracteres contenha, como o tipo <xref:System.Int32?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="bbf7e-106">You can use `Parse` or `TryParse` methods on the numeric type you expect the string contains, such as the <xref:System.Int32?displayProperty=fullName> type.</span></span>  <span data-ttu-id="bbf7e-107">O método <xref:System.Convert.ToUInt32%2A?displayProperty=fullName> usa <xref:System.Int32.Parse%2A> internamente.</span><span class="sxs-lookup"><span data-stu-id="bbf7e-107">The <xref:System.Convert.ToUInt32%2A?displayProperty=fullName> method uses <xref:System.Int32.Parse%2A> internally.</span></span>  <span data-ttu-id="bbf7e-108">Se a cadeia de caracteres não estiver em um formato válido, `Parse` lançará uma exceção, ao passo que `TryParse` retornará [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="bbf7e-108">If the string is not in a valid format, `Parse` throws an exception whereas `TryParse` returns [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbf7e-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bbf7e-109">Example</span></span>  
 <span data-ttu-id="bbf7e-110">Os métodos `Parse` e `TryParse` ignoram o espaço em branco no início e no final da cadeia de caracteres, porém, todos os outros caracteres devem formar o tipo numérico correto (int, long, ulong, float, decimal etc.).</span><span class="sxs-lookup"><span data-stu-id="bbf7e-110">The `Parse` and `TryParse` methods ignore whitespace at the beginning and at the end of the string, but all other characters must be characters that form the appropriate numeric type (int, long, ulong, float, decimal, etc.).</span></span>  <span data-ttu-id="bbf7e-111">Os espaços em branco dentro dos caracteres que formam o número causam um erro.</span><span class="sxs-lookup"><span data-stu-id="bbf7e-111">Any whitespace within the characters that form the number cause an error.</span></span>  <span data-ttu-id="bbf7e-112">Por exemplo, é possível usar `decimal.TryParse` para analisar "10", "10.3", "  10  ", mas não é possível usar esse método para analisar 10 de "10X", "1 0" (observe o espaço), "10 .3" (observe o espaço), "10e1" (`float.TryParse` funcionará neste caso) e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="bbf7e-112">For example, you can use `decimal.TryParse` to parse "10", "10.3", "  10  ", but you cannot use this method to parse 10 from "10X", "1 0" (note space), "10 .3" (note space), "10e1" (`float.TryParse` works here), and so on.</span></span>  
  
 <span data-ttu-id="bbf7e-113">Os exemplos abaixo demonstram chamadas com e sem êxito a `Parse` e `TryParse`.</span><span class="sxs-lookup"><span data-stu-id="bbf7e-113">The examples below demonstrate both successful and unsuccessful calls to `Parse` and `TryParse`.</span></span>  
  
 <span data-ttu-id="bbf7e-114">[!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="bbf7e-114">[!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]</span></span>  
<span data-ttu-id="bbf7e-115">[!code-cs[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="bbf7e-115">[!code-cs[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]</span></span>  
<span data-ttu-id="bbf7e-116">[!code-cs[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="bbf7e-116">[!code-cs[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]</span></span>  
<span data-ttu-id="bbf7e-117">[!code-cs[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="bbf7e-117">[!code-cs[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]</span></span>  
<span data-ttu-id="bbf7e-118">[!code-cs[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="bbf7e-118">[!code-cs[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]</span></span>  
<span data-ttu-id="bbf7e-119">[!code-cs[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="bbf7e-119">[!code-cs[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbf7e-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bbf7e-120">Example</span></span>  
 <span data-ttu-id="bbf7e-121">A tabela a seguir lista alguns dos métodos da classe <xref:System.Convert> que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="bbf7e-121">The following table lists some of the methods from the <xref:System.Convert> class that you can use.</span></span>  
  
|<span data-ttu-id="bbf7e-122">Tipo numérico</span><span class="sxs-lookup"><span data-stu-id="bbf7e-122">Numeric Type</span></span>|<span data-ttu-id="bbf7e-123">Método</span><span class="sxs-lookup"><span data-stu-id="bbf7e-123">Method</span></span>|  
|------------------|------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 <span data-ttu-id="bbf7e-124">Este exemplo chama o método <xref:System.Convert.ToInt32%28System.String%29?displayProperty=fullName> para converter uma entrada [string](../../../csharp/language-reference/keywords/string.md) em [int](../../../csharp/language-reference/keywords/int.md).</span><span class="sxs-lookup"><span data-stu-id="bbf7e-124">This example calls the <xref:System.Convert.ToInt32%28System.String%29?displayProperty=fullName> method to convert an input [string](../../../csharp/language-reference/keywords/string.md) to an [int](../../../csharp/language-reference/keywords/int.md) .</span></span> <span data-ttu-id="bbf7e-125">O código captura as duas exceções mais comuns que podem ser geradas por esse método, <xref:System.FormatException> e <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="bbf7e-125">The code catches the two most common exceptions that can be thrown by this method, <xref:System.FormatException> and <xref:System.OverflowException>.</span></span> <span data-ttu-id="bbf7e-126">Se o número pode ser incrementado sem estourar o local de armazenamento de inteiros, o programa adiciona 1 ao resultado e imprime a saída.</span><span class="sxs-lookup"><span data-stu-id="bbf7e-126">If the number can be incremented without overflowing the integer storage location, the program adds 1 to the result and prints the output.</span></span>  
  
 <span data-ttu-id="bbf7e-127">[!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="bbf7e-127">[!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]</span></span>  
<span data-ttu-id="bbf7e-128">[!code-cs[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="bbf7e-128">[!code-cs[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbf7e-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbf7e-129">See Also</span></span>  
 <span data-ttu-id="bbf7e-130">[Tipos](../../../csharp/programming-guide/types/index.md) </span><span class="sxs-lookup"><span data-stu-id="bbf7e-130">[Types](../../../csharp/programming-guide/types/index.md) </span></span>  
 <span data-ttu-id="bbf7e-131">[Como Determinar se uma Cadeia de Caracteres Representa um Valor Numérico](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md) </span><span class="sxs-lookup"><span data-stu-id="bbf7e-131">[How to: Determine Whether a String Represents a Numeric Value](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md) </span></span>  
 [<span data-ttu-id="bbf7e-132">.NET Framework 4 Formatting Utility</span><span class="sxs-lookup"><span data-stu-id="bbf7e-132">.NET Framework 4 Formatting Utility</span></span>](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)

