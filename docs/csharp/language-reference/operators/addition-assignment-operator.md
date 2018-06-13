---
title: Operador += (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: bcd56acad8e2b08585e5ae60f1c3cf8183b5664a
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171873"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1cccf-102">Operador += (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="1cccf-102">+= Operator (C# Reference)</span></span>
<span data-ttu-id="1cccf-103">Operador de atribuição de adição.</span><span class="sxs-lookup"><span data-stu-id="1cccf-103">The addition assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cccf-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="1cccf-104">Remarks</span></span>  
 <span data-ttu-id="1cccf-105">Uma expressão que usa o operador de atribuição `+=`, como</span><span class="sxs-lookup"><span data-stu-id="1cccf-105">An expression using the `+=` assignment operator, such as</span></span>  
  
```csharp  
x += y  
```  
  
 <span data-ttu-id="1cccf-106">equivale a</span><span class="sxs-lookup"><span data-stu-id="1cccf-106">is equivalent to</span></span>  
  
```csharp  
x = x + y  
```  
  
 <span data-ttu-id="1cccf-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="1cccf-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="1cccf-108">O significado do [operador +](../../../csharp/language-reference/operators/addition-operator.md) dependerá dos tipos de `x` e `y` (adição para operandos numéricos, concatenação para operandos de cadeia de caracteres e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="1cccf-108">The meaning of the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) depends on the types of `x` and `y` (addition for numeric operands, concatenation for string operands, and so forth).</span></span>  
  
 <span data-ttu-id="1cccf-109">O operador `+=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador +](../../../csharp/language-reference/operators/addition-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="1cccf-109">The `+=` operator cannot be overloaded directly, but user-defined types can overload the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="1cccf-110">O operador `+=` também é usado para especificar um método que será chamado em resposta a um evento; esses métodos são chamados de manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="1cccf-110">The `+=` operator is also used to specify a method that will be called in response to an event; such methods are called event handlers.</span></span> <span data-ttu-id="1cccf-111">O uso do operador `+=` nesse contexto é conhecido como *inscrever-se em um evento*.</span><span class="sxs-lookup"><span data-stu-id="1cccf-111">The use of the `+=` operator in this context is referred to as *subscribing to an event*.</span></span> <span data-ttu-id="1cccf-112">Para obter mais informações, consulte [Como assinar e cancelar a assinatura de eventos](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) e [Delegados](../../../csharp/programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="1cccf-112">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) and [Delegates](../../../csharp/programming-guide/delegates/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cccf-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1cccf-113">Example</span></span>  
 [!code-csharp[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1cccf-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cccf-114">See Also</span></span>  
 [<span data-ttu-id="1cccf-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="1cccf-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1cccf-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1cccf-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1cccf-117">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="1cccf-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
