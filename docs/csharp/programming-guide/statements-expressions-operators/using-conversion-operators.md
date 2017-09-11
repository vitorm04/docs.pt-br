---
title: "Usando operadores de conversão (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#], operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
- implicit conversion operators [C#]
- explicit conversion operators [C#]
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
caps.latest.revision: 20
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
ms.openlocfilehash: 2561b680da567623b8dab13e9e5294c3dd2c1012
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="using-conversion-operators-c-programming-guide"></a><span data-ttu-id="8690b-102">Usando operadores de conversão (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="8690b-102">Using Conversion Operators (C# Programming Guide)</span></span>
<span data-ttu-id="8690b-103">É possível usar operadores de conversão `implicit`, que são mais fáceis de usar ou operadores de conversão `explicit`, que indicam claramente para alguém que lê o código que você está convertendo um tipo.</span><span class="sxs-lookup"><span data-stu-id="8690b-103">You can use `implicit` conversion operators, which are easier to use, or `explicit` conversion operators, which clearly indicate to anyone reading the code that you're converting a type.</span></span> <span data-ttu-id="8690b-104">Este tópico demonstra os dois os tipos de operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="8690b-104">This topic demonstrates both types of conversion operator.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8690b-105">Para obter informações sobre conversões de tipo simples, consulte [Como converter uma cadeia de caracteres em um número](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [Como converter uma matriz de bytes em um int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [Como converter entre cadeias de caracteres hexadecimais e tipos numéricos](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md) ou <xref:System.Convert>.</span><span class="sxs-lookup"><span data-stu-id="8690b-105">For information about simple type conversions, see [How to: Convert a String to a Number](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [How to: Convert a byte Array to an int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [How to: Convert Between Hexadecimal Strings and Numeric Types](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md), or <xref:System.Convert>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8690b-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8690b-106">Example</span></span>  
 <span data-ttu-id="8690b-107">Este é um exemplo de um operador de conversão explícita.</span><span class="sxs-lookup"><span data-stu-id="8690b-107">This is an example of an explicit conversion operator.</span></span> <span data-ttu-id="8690b-108">Este operador converte do tipo <xref:System.Byte> em um tipo de valor denominado `Digit`.</span><span class="sxs-lookup"><span data-stu-id="8690b-108">This operator converts from the type <xref:System.Byte> to a value type called `Digit`.</span></span> <span data-ttu-id="8690b-109">Como nem todos os bytes podem ser convertidos em um dígito, a conversão é explícita, o que significa que uma conversão deve ser usada, conforme mostrado no método `Main`.</span><span class="sxs-lookup"><span data-stu-id="8690b-109">Because not all bytes can be converted to a digit, the conversion is explicit, meaning that a cast must be used, as shown in the `Main` method.</span></span>  
  
 <span data-ttu-id="8690b-110">[!code-cs[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="8690b-110">[!code-cs[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="8690b-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8690b-111">Example</span></span>  
 <span data-ttu-id="8690b-112">Este exemplo demonstra um operador de conversão implícita definindo um operador de conversão que desfaz o que o exemplo anterior fez: converte de uma classe de valor chamada `Digit` no tipo <xref:System.Byte> integral.</span><span class="sxs-lookup"><span data-stu-id="8690b-112">This example demonstrates an implicit conversion operator by defining a conversion operator that undoes what the previous example did: it converts from a value class called `Digit` to the integral <xref:System.Byte> type.</span></span> <span data-ttu-id="8690b-113">Como qualquer dígito pode ser convertido em um <xref:System.Byte>, não há necessidade de forçar os usuários a serem explícitos com relação à conversão.</span><span class="sxs-lookup"><span data-stu-id="8690b-113">Because any digit can be converted to a <xref:System.Byte>, there's no need to force users to be explicit about the conversion.</span></span>  
  
 <span data-ttu-id="8690b-114">[!code-cs[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="8690b-114">[!code-cs[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8690b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8690b-115">See Also</span></span>  
 <span data-ttu-id="8690b-116">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="8690b-116">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="8690b-117">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="8690b-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="8690b-118">[Operadores de conversão](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md) </span><span class="sxs-lookup"><span data-stu-id="8690b-118">[Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md) </span></span>  
 [<span data-ttu-id="8690b-119">is</span><span class="sxs-lookup"><span data-stu-id="8690b-119">is</span></span>](../../../csharp/language-reference/keywords/is.md)

