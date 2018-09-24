---
title: Usando operadores de conversão (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
- implicit conversion operators [C#]
- explicit conversion operators [C#]
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
ms.openlocfilehash: 17a722f7160ae9cd03caa2dff9c4436fcf0f9d9e
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46698800"
---
# <a name="using-conversion-operators-c-programming-guide"></a><span data-ttu-id="7f638-102">Usando operadores de conversão (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="7f638-102">Using Conversion Operators (C# Programming Guide)</span></span>
<span data-ttu-id="7f638-103">É possível usar operadores de conversão `implicit`, que são mais fáceis de usar ou operadores de conversão `explicit`, que indicam claramente para alguém que lê o código que você está convertendo um tipo.</span><span class="sxs-lookup"><span data-stu-id="7f638-103">You can use `implicit` conversion operators, which are easier to use, or `explicit` conversion operators, which clearly indicate to anyone reading the code that you're converting a type.</span></span> <span data-ttu-id="7f638-104">Este tópico demonstra os dois os tipos de operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="7f638-104">This topic demonstrates both types of conversion operator.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f638-105">Para obter informações sobre conversões de tipo simples, consulte [Como converter uma cadeia de caracteres em um número](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [Como converter uma matriz de bytes em um int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [Como converter entre cadeias de caracteres hexadecimais e tipos numéricos](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md) ou <xref:System.Convert>.</span><span class="sxs-lookup"><span data-stu-id="7f638-105">For information about simple type conversions, see [How to: Convert a String to a Number](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [How to: Convert a byte Array to an int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [How to: Convert Between Hexadecimal Strings and Numeric Types](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md), or <xref:System.Convert>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f638-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f638-106">Example</span></span>  
 <span data-ttu-id="7f638-107">Este é um exemplo de um operador de conversão explícita.</span><span class="sxs-lookup"><span data-stu-id="7f638-107">This is an example of an explicit conversion operator.</span></span> <span data-ttu-id="7f638-108">Este operador converte do tipo <xref:System.Byte> em um tipo de valor denominado `Digit`.</span><span class="sxs-lookup"><span data-stu-id="7f638-108">This operator converts from the type <xref:System.Byte> to a value type called `Digit`.</span></span> <span data-ttu-id="7f638-109">Como nem todos os bytes podem ser convertidos em um dígito, a conversão é explícita, o que significa que uma conversão deve ser usada, conforme mostrado no método `Main`.</span><span class="sxs-lookup"><span data-stu-id="7f638-109">Because not all bytes can be converted to a digit, the conversion is explicit, meaning that a cast must be used, as shown in the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="7f638-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f638-110">Example</span></span>  
 <span data-ttu-id="7f638-111">Este exemplo demonstra um operador de conversão implícita definindo um operador de conversão que desfaz o que o exemplo anterior fez: converte de uma classe de valor chamada `Digit` no tipo <xref:System.Byte> integral.</span><span class="sxs-lookup"><span data-stu-id="7f638-111">This example demonstrates an implicit conversion operator by defining a conversion operator that undoes what the previous example did: it converts from a value class called `Digit` to the integral <xref:System.Byte> type.</span></span> <span data-ttu-id="7f638-112">Como qualquer dígito pode ser convertido em um <xref:System.Byte>, não há necessidade de forçar os usuários a serem explícitos com relação à conversão.</span><span class="sxs-lookup"><span data-stu-id="7f638-112">Because any digit can be converted to a <xref:System.Byte>, there's no need to force users to be explicit about the conversion.</span></span>  
  
 [!code-csharp[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7f638-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f638-113">See Also</span></span>

- [<span data-ttu-id="7f638-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="7f638-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="7f638-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="7f638-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="7f638-116">Operadores de conversão</span><span class="sxs-lookup"><span data-stu-id="7f638-116">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
- [<span data-ttu-id="7f638-117">is</span><span class="sxs-lookup"><span data-stu-id="7f638-117">is</span></span>](../../../csharp/language-reference/keywords/is.md)
