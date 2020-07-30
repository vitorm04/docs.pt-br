---
title: Como determinar se uma cadeia de caracteres representa um valor numérico – guia de programação C#
description: Saiba como determinar se uma cadeia de caracteres é uma representação válida de um tipo numérico especificado. Consulte exemplos de código e exiba recursos adicionais.
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: c248c6c54de493ab06a833fc525252fa812d60da
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381743"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="a8de2-104">Como determinar se uma cadeia de caracteres representa um valor numérico (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="a8de2-104">How to determine whether a string represents a numeric value (C# Programming Guide)</span></span>
<span data-ttu-id="a8de2-105">Para determinar se uma cadeia de caracteres é uma representação válida de um tipo numérico especificado, use o método estático `TryParse` implementado por todos os tipos numéricos primitivos e também por tipos como <xref:System.DateTime> e <xref:System.Net.IPAddress>.</span><span class="sxs-lookup"><span data-stu-id="a8de2-105">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="a8de2-106">O exemplo a seguir mostra como determinar se "108" é um [int](../../language-reference/builtin-types/integral-numeric-types.md) válido.</span><span class="sxs-lookup"><span data-stu-id="a8de2-106">The following example shows how to determine whether "108" is a valid [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
```csharp  
int i = 0;
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="a8de2-107">Se a cadeia de caracteres contiver caracteres não numéricos ou o valor numérico for muito grande ou muito pequeno para o tipo especificado, `TryParse` retornará false e definirá o parâmetro de saída como zero.</span><span class="sxs-lookup"><span data-stu-id="a8de2-107">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="a8de2-108">Caso contrário, ele retornará true e definirá o parâmetro de saída como o valor numérico da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a8de2-108">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8de2-109">Uma cadeia de caracteres pode conter apenas caracteres numéricos e ainda não ser válida para o método `TryParse` do tipo usado.</span><span class="sxs-lookup"><span data-stu-id="a8de2-109">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="a8de2-110">Por exemplo, "256" não é um valor válido para `byte`, mas é válido para `int`.</span><span class="sxs-lookup"><span data-stu-id="a8de2-110">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="a8de2-111">“98,6” não é um valor válido para `int`, mas é válido para `decimal`.</span><span class="sxs-lookup"><span data-stu-id="a8de2-111">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8de2-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8de2-112">Example</span></span>  
 <span data-ttu-id="a8de2-113">Os exemplos a seguir mostram como usar `TryParse` com representações de cadeia de caracteres dos valores `long`, `byte` e `decimal`.</span><span class="sxs-lookup"><span data-stu-id="a8de2-113">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a><span data-ttu-id="a8de2-114">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="a8de2-114">Robust Programming</span></span>  
 <span data-ttu-id="a8de2-115">Os tipos numéricos primitivos também implementam o método estático `Parse`, que lançará uma exceção se a cadeia de caracteres não for um número válido.</span><span class="sxs-lookup"><span data-stu-id="a8de2-115">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="a8de2-116">Geralmente, `TryParse` é mais eficiente, pois retornará false apenas se o número não for válido.</span><span class="sxs-lookup"><span data-stu-id="a8de2-116">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="a8de2-117">Segurança do .NET</span><span class="sxs-lookup"><span data-stu-id="a8de2-117">.NET Security</span></span>  
 <span data-ttu-id="a8de2-118">Sempre use os métodos `TryParse` ou `Parse` para validar entradas de usuário em controles como caixas de texto e caixas de combinação.</span><span class="sxs-lookup"><span data-stu-id="a8de2-118">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8de2-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="a8de2-119">See also</span></span>

- [<span data-ttu-id="a8de2-120">Como converter uma matriz de bytes em um int</span><span class="sxs-lookup"><span data-stu-id="a8de2-120">How to convert a byte array to an int</span></span>](../types/how-to-convert-a-byte-array-to-an-int.md)
- [<span data-ttu-id="a8de2-121">Como converter uma cadeia de caracteres em um número</span><span class="sxs-lookup"><span data-stu-id="a8de2-121">How to convert a string to a number</span></span>](../types/how-to-convert-a-string-to-a-number.md)
- [<span data-ttu-id="a8de2-122">Como converter entre cadeias de caracteres hexadecimais e tipos numéricos</span><span class="sxs-lookup"><span data-stu-id="a8de2-122">How to convert between hexadecimal strings and numeric types</span></span>](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [<span data-ttu-id="a8de2-123">Analisar cadeias de caracteres numéricas</span><span class="sxs-lookup"><span data-stu-id="a8de2-123">Parsing Numeric Strings</span></span>](../../../standard/base-types/parsing-numeric.md)
- [<span data-ttu-id="a8de2-124">Formatar tipos</span><span class="sxs-lookup"><span data-stu-id="a8de2-124">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
