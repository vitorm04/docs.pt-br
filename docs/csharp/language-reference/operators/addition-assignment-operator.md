---
title: "Operador += (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- +=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
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
ms.openlocfilehash: 42567b2d8e7d9b694ce64ccb88e0fd4bfe05b020
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="3b1f7-102">Operador += (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="3b1f7-102">+= Operator (C# Reference)</span></span>
<span data-ttu-id="3b1f7-103">Operador de atribuição de adição.</span><span class="sxs-lookup"><span data-stu-id="3b1f7-103">The addition assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b1f7-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="3b1f7-104">Remarks</span></span>  
 <span data-ttu-id="3b1f7-105">Uma expressão que usa o operador de atribuição `+=`, como</span><span class="sxs-lookup"><span data-stu-id="3b1f7-105">An expression using the `+=` assignment operator, such as</span></span>  
  
```  
x += y  
```  
  
 <span data-ttu-id="3b1f7-106">equivale a</span><span class="sxs-lookup"><span data-stu-id="3b1f7-106">is equivalent to</span></span>  
  
```  
x = x + y  
```  
  
 <span data-ttu-id="3b1f7-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="3b1f7-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="3b1f7-108">O significado do [operador +](../../../csharp/language-reference/operators/addition-operator.md) dependerá dos tipos de `x` e `y` (adição para operandos numéricos, concatenação para operandos de cadeia de caracteres e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="3b1f7-108">The meaning of the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) depends on the types of `x` and `y` (addition for numeric operands, concatenation for string operands, and so forth).</span></span>  
  
 <span data-ttu-id="3b1f7-109">O operador `+=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador +](../../../csharp/language-reference/operators/addition-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="3b1f7-109">The `+=` operator cannot be overloaded directly, but user-defined types can overload the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="3b1f7-110">O operador `+=` também é usado para especificar um método que será chamado em resposta a um evento; esses métodos são chamados de manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="3b1f7-110">The `+=` operator is also used to specify a method that will be called in response to an event; such methods are called event handlers.</span></span> <span data-ttu-id="3b1f7-111">O uso do operador `+=` nesse contexto é conhecido como *inscrever-se em um evento*.</span><span class="sxs-lookup"><span data-stu-id="3b1f7-111">The use of the `+=` operator in this context is referred to as *subscribing to an event*.</span></span> <span data-ttu-id="3b1f7-112">Para obter mais informações, consulte [Como Realizar e Cancelar a Assinatura de Eventos](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="3b1f7-112">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span> <span data-ttu-id="3b1f7-113">e [Delegados](../../../csharp/programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="3b1f7-113">and [Delegates](../../../csharp/programming-guide/delegates/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b1f7-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3b1f7-114">Example</span></span>  
 <span data-ttu-id="3b1f7-115">[!code-cs[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="3b1f7-115">[!code-cs[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b1f7-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b1f7-116">See Also</span></span>  
 <span data-ttu-id="3b1f7-117">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="3b1f7-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="3b1f7-118">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="3b1f7-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="3b1f7-119">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="3b1f7-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

