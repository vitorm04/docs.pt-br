---
title: "Como executar conversão cast com segurança usando operadores as e is (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 733b67408997feb0e518db327e3eedd42f286a99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a><span data-ttu-id="d6630-102">Como executar conversão cast com segurança usando operadores as e is (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="d6630-102">How to: Safely Cast by Using as and is Operators (C# Programming Guide)</span></span>
<span data-ttu-id="d6630-103">Como os objetos são polimórficos, é possível que uma variável de tipo de classe base mantenha um tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="d6630-103">Because objects are polymorphic, it is possible for a variable of a base class type to hold a derived type.</span></span> <span data-ttu-id="d6630-104">Para acessar o método de tipo derivado, é necessário converter o valor de volta no tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="d6630-104">To access the derived type's method, it is necessary to cast the value back to the derived type.</span></span> <span data-ttu-id="d6630-105">No entanto, tentar uma conversão simples nesses casos, cria o risco de lançar uma <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="d6630-105">However, to attempt a simple cast in these cases creates the risk of throwing an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="d6630-106">Isso ocorre porque o C# fornece os operadores [is](../../../csharp/language-reference/keywords/is.md) e [as](../../../csharp/language-reference/keywords/as.md).</span><span class="sxs-lookup"><span data-stu-id="d6630-106">That is why C# provides the [is](../../../csharp/language-reference/keywords/is.md) and [as](../../../csharp/language-reference/keywords/as.md) operators.</span></span> <span data-ttu-id="d6630-107">É possível usar esses operadores para testar se uma conversão será bem-sucedida sem fazer com que uma exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="d6630-107">You can use these operators to test whether a cast will succeed without causing an exception to be thrown.</span></span> <span data-ttu-id="d6630-108">Em geral, o operador `as` é mais eficiente, porque ele realmente retornará o valor de conversão se a conversão puder ser realizada com êxito.</span><span class="sxs-lookup"><span data-stu-id="d6630-108">In general, the `as` operator is more efficient because it actually returns the cast value if the cast can be made successfully.</span></span> <span data-ttu-id="d6630-109">O operador `is` retorna apenas um valor booliano.</span><span class="sxs-lookup"><span data-stu-id="d6630-109">The `is` operator returns only a Boolean value.</span></span> <span data-ttu-id="d6630-110">Portanto, ele poderá ser usado quando você desejar determinar o tipo de um objeto, mas não será necessário convertê-lo realmente.</span><span class="sxs-lookup"><span data-stu-id="d6630-110">It can therefore be used when you just want to determine an object's type but do not have to actually cast it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6630-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6630-111">Example</span></span>  
 <span data-ttu-id="d6630-112">Os exemplos a seguir mostram como usar os operadores `is` e `as` para converter de um tipo de referência em outro sem o risco de lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="d6630-112">The following examples show how to use the `is` and `as` operators to cast from one reference type to another without the risk of throwing an exception.</span></span> <span data-ttu-id="d6630-113">O exemplo também mostra como usar o operador `as` com tipos de valores anuláveis.</span><span class="sxs-lookup"><span data-stu-id="d6630-113">The example also shows how to use the `as` operator with nullable value types.</span></span>  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d6630-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6630-114">See Also</span></span>  
 [<span data-ttu-id="d6630-115">Tipos</span><span class="sxs-lookup"><span data-stu-id="d6630-115">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="d6630-116">Transmissões e conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="d6630-116">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="d6630-117">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="d6630-117">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)
