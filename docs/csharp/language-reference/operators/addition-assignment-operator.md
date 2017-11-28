---
title: "Operador += (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 91286b3c6b9a7239bcd5d5bac0ef08bfd7fa8345
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d331f-102">Operador += (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d331f-102">+= Operator (C# Reference)</span></span>
<span data-ttu-id="d331f-103">Operador de atribuição de adição.</span><span class="sxs-lookup"><span data-stu-id="d331f-103">The addition assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d331f-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="d331f-104">Remarks</span></span>  
 <span data-ttu-id="d331f-105">Uma expressão que usa o operador de atribuição `+=`, como</span><span class="sxs-lookup"><span data-stu-id="d331f-105">An expression using the `+=` assignment operator, such as</span></span>  
  
```  
x += y  
```  
  
 <span data-ttu-id="d331f-106">equivale a</span><span class="sxs-lookup"><span data-stu-id="d331f-106">is equivalent to</span></span>  
  
```  
x = x + y  
```  
  
 <span data-ttu-id="d331f-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="d331f-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="d331f-108">O significado do [operador +](../../../csharp/language-reference/operators/addition-operator.md) dependerá dos tipos de `x` e `y` (adição para operandos numéricos, concatenação para operandos de cadeia de caracteres e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="d331f-108">The meaning of the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) depends on the types of `x` and `y` (addition for numeric operands, concatenation for string operands, and so forth).</span></span>  
  
 <span data-ttu-id="d331f-109">O operador `+=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador +](../../../csharp/language-reference/operators/addition-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="d331f-109">The `+=` operator cannot be overloaded directly, but user-defined types can overload the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="d331f-110">O operador `+=` também é usado para especificar um método que será chamado em resposta a um evento; esses métodos são chamados de manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="d331f-110">The `+=` operator is also used to specify a method that will be called in response to an event; such methods are called event handlers.</span></span> <span data-ttu-id="d331f-111">O uso do operador `+=` nesse contexto é conhecido como *inscrever-se em um evento*.</span><span class="sxs-lookup"><span data-stu-id="d331f-111">The use of the `+=` operator in this context is referred to as *subscribing to an event*.</span></span> <span data-ttu-id="d331f-112">Para obter mais informações, consulte [Como Realizar e Cancelar a Assinatura de Eventos](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="d331f-112">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span> <span data-ttu-id="d331f-113">e [Delegados](../../../csharp/programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="d331f-113">and [Delegates](../../../csharp/programming-guide/delegates/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d331f-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d331f-114">Example</span></span>  
 [!code-csharp[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d331f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d331f-115">See Also</span></span>  
 [<span data-ttu-id="d331f-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d331f-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d331f-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d331f-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d331f-118">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="d331f-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
