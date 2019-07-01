---
title: 'Como: determinar se uma cadeia de caracteres representa um valor numérico – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 626fce590ba08bbdabf27ac33287a0b46b592f9c
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423609"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="fe978-102">Como: determinar se uma cadeia de caracteres representa um valor numérico (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="fe978-102">How to: Determine Whether a String Represents a Numeric Value (C# Programming Guide)</span></span>
<span data-ttu-id="fe978-103">Para determinar se uma cadeia de caracteres é uma representação válida de um tipo numérico especificado, use o método estático `TryParse` implementado por todos os tipos numéricos primitivos e também por tipos como <xref:System.DateTime> e <xref:System.Net.IPAddress>.</span><span class="sxs-lookup"><span data-stu-id="fe978-103">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="fe978-104">O exemplo a seguir mostra como determinar se "108" é um [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) válido.</span><span class="sxs-lookup"><span data-stu-id="fe978-104">The following example shows how to determine whether "108" is a valid [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="fe978-105">Se a cadeia de caracteres contiver caracteres não numéricos ou o valor numérico for muito grande ou muito pequeno para o tipo especificado, `TryParse` retornará false e definirá o parâmetro de saída como zero.</span><span class="sxs-lookup"><span data-stu-id="fe978-105">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="fe978-106">Caso contrário, ele retornará true e definirá o parâmetro de saída como o valor numérico da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="fe978-106">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe978-107">Uma cadeia de caracteres pode conter apenas caracteres numéricos e ainda não ser válida para o método `TryParse` do tipo usado.</span><span class="sxs-lookup"><span data-stu-id="fe978-107">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="fe978-108">Por exemplo, "256" não é um valor válido para `byte`, mas é válido para `int`.</span><span class="sxs-lookup"><span data-stu-id="fe978-108">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="fe978-109">“98,6” não é um valor válido para `int`, mas é válido para `decimal`.</span><span class="sxs-lookup"><span data-stu-id="fe978-109">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe978-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fe978-110">Example</span></span>  
 <span data-ttu-id="fe978-111">Os exemplos a seguir mostram como usar `TryParse` com representações de cadeia de caracteres dos valores `long`, `byte` e `decimal`.</span><span class="sxs-lookup"><span data-stu-id="fe978-111">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a><span data-ttu-id="fe978-112">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="fe978-112">Robust Programming</span></span>  
 <span data-ttu-id="fe978-113">Os tipos numéricos primitivos também implementam o método estático `Parse`, que lançará uma exceção se a cadeia de caracteres não for um número válido.</span><span class="sxs-lookup"><span data-stu-id="fe978-113">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="fe978-114">Geralmente, `TryParse` é mais eficiente, pois retornará false apenas se o número não for válido.</span><span class="sxs-lookup"><span data-stu-id="fe978-114">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="fe978-115">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fe978-115">.NET Framework Security</span></span>  
 <span data-ttu-id="fe978-116">Sempre use os métodos `TryParse` ou `Parse` para validar entradas de usuário em controles como caixas de texto e caixas de combinação.</span><span class="sxs-lookup"><span data-stu-id="fe978-116">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe978-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe978-117">See also</span></span>

- [<span data-ttu-id="fe978-118">Como: converter uma matriz de bytes em um int</span><span class="sxs-lookup"><span data-stu-id="fe978-118">How to: Convert a byte Array to an int</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)
- [<span data-ttu-id="fe978-119">Como: converter uma cadeia de caracteres em um número</span><span class="sxs-lookup"><span data-stu-id="fe978-119">How to: Convert a String to a Number</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
- [<span data-ttu-id="fe978-120">Como: converter entre cadeias de caracteres hexadecimais e tipos numéricos</span><span class="sxs-lookup"><span data-stu-id="fe978-120">How to: Convert Between Hexadecimal Strings and Numeric Types</span></span>](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [<span data-ttu-id="fe978-121">Analisando cadeias de caracteres numéricas</span><span class="sxs-lookup"><span data-stu-id="fe978-121">Parsing Numeric Strings</span></span>](../../../standard/base-types/parsing-numeric.md)
- [<span data-ttu-id="fe978-122">Formatando Tipos</span><span class="sxs-lookup"><span data-stu-id="fe978-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
