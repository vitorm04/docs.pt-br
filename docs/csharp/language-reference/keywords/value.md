---
title: value (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: c8f808540385552f6222566f23251f6cbd6e86df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33265266"
---
# <a name="value-c-reference"></a><span data-ttu-id="a0270-102">value (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a0270-102">value (C# Reference)</span></span>
<span data-ttu-id="a0270-103">A palavra-chave contextual `value` é usada no acessador definido em declarações de propriedade comuns.</span><span class="sxs-lookup"><span data-stu-id="a0270-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="a0270-104">Ela é semelhante a um parâmetro de entrada em um método.</span><span class="sxs-lookup"><span data-stu-id="a0270-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="a0270-105">A palavra `value` referencia o valor que o código cliente está tentando atribuir à propriedade.</span><span class="sxs-lookup"><span data-stu-id="a0270-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="a0270-106">No exemplo a seguir, `MyDerivedClass` tem uma propriedade chamada `Name` que usa o parâmetro `value` para atribuir uma nova cadeia de caracteres ao campo de suporte `name`.</span><span class="sxs-lookup"><span data-stu-id="a0270-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="a0270-107">Do ponto de vista do código cliente, a operação é gravada como uma atribuição simples.</span><span class="sxs-lookup"><span data-stu-id="a0270-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]  
  
 <span data-ttu-id="a0270-108">Para obter mais informações sobre o uso de `value`, consulte [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="a0270-108">For more information about the use of `value`, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="a0270-109">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="a0270-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a0270-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0270-110">See Also</span></span>  
 [<span data-ttu-id="a0270-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a0270-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a0270-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a0270-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a0270-113">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="a0270-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
