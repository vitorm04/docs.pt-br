---
title: "value (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- value_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
caps.latest.revision: 14
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
ms.openlocfilehash: 012cf622091687996fec477a8b5b821b190bbc29
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="value-c-reference"></a><span data-ttu-id="d37c8-102">value (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d37c8-102">value (C# Reference)</span></span>
<span data-ttu-id="d37c8-103">A palavra-chave contextual `value` é usada no acessador definido em declarações de propriedade comuns.</span><span class="sxs-lookup"><span data-stu-id="d37c8-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="d37c8-104">Ela é semelhante a um parâmetro de entrada em um método.</span><span class="sxs-lookup"><span data-stu-id="d37c8-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="d37c8-105">A palavra `value` referencia o valor que o código cliente está tentando atribuir à propriedade.</span><span class="sxs-lookup"><span data-stu-id="d37c8-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="d37c8-106">No exemplo a seguir, `MyDerivedClass` tem uma propriedade chamada `Name` que usa o parâmetro `value` para atribuir uma nova cadeia de caracteres ao campo de suporte `name`.</span><span class="sxs-lookup"><span data-stu-id="d37c8-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="d37c8-107">Do ponto de vista do código cliente, a operação é gravada como uma atribuição simples.</span><span class="sxs-lookup"><span data-stu-id="d37c8-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>  
  
 <span data-ttu-id="d37c8-108">[!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d37c8-108">[!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]</span></span>  
  
 <span data-ttu-id="d37c8-109">Para obter mais informações sobre o uso de `value`, consulte [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="d37c8-109">For more information about the use of `value`, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d37c8-110">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d37c8-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d37c8-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d37c8-111">See Also</span></span>  
 <span data-ttu-id="d37c8-112">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="d37c8-112">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="d37c8-113">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d37c8-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="d37c8-114">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="d37c8-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)

