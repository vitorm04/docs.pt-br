---
title: "Operador new (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
caps.latest.revision: 22
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
ms.openlocfilehash: 59e1cc2006548df9a7a10283a34044040e5c2fef
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="new-operator-c-reference"></a><span data-ttu-id="024ed-102">Operador new (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="024ed-102">new Operator (C# Reference)</span></span>
<span data-ttu-id="024ed-103">Usado para criar objetos e invocar construtores.</span><span class="sxs-lookup"><span data-stu-id="024ed-103">Used to create objects and invoke constructors.</span></span> <span data-ttu-id="024ed-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="024ed-104">For example:</span></span>  
  
```  
Class1 obj  = new Class1();  
```  
  
 <span data-ttu-id="024ed-105">Ele também é usado para criar instâncias de tipos anônimos:</span><span class="sxs-lookup"><span data-stu-id="024ed-105">It is also used to create instances of anonymous types:</span></span>  
  
```  
var query = from cust in customers  
            select new {Name = cust.Name, Address = cust.PrimaryAddress};  
```  
  
 <span data-ttu-id="024ed-106">O operador `new` também é usado para invocar o construtor padrão para tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="024ed-106">The `new` operator is also used to invoke the default constructor for value types.</span></span> <span data-ttu-id="024ed-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="024ed-107">For example:</span></span>  
  
```  
int i = new int();  
```  
  
 <span data-ttu-id="024ed-108">Na instrução anterior, `i` é inicializado como `0`, que é o valor padrão do tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="024ed-108">In the preceding statement, `i` is initialized to `0`, which is the default value for the type `int`.</span></span> <span data-ttu-id="024ed-109">A instrução tem o mesmo efeito que o seguinte:</span><span class="sxs-lookup"><span data-stu-id="024ed-109">The statement has the same effect as the following:</span></span>  
  
```  
int i = 0;  
```  
  
 <span data-ttu-id="024ed-110">Para ver uma lista completa dos valores padrão, consulte [Tabela de valores padrão](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="024ed-110">For a complete list of default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="024ed-111">Lembre-se de que é um erro declarar um construtor padrão para um [struct](../../../csharp/language-reference/keywords/struct.md), porque cada tipo de valor tem implicitamente um construtor padrão público.</span><span class="sxs-lookup"><span data-stu-id="024ed-111">Remember that it is an error to declare a default constructor for a [struct](../../../csharp/language-reference/keywords/struct.md) because every value type implicitly has a public default constructor.</span></span> <span data-ttu-id="024ed-112">É possível declarar construtores parametrizados em um tipo de struct para definir seus valores iniciais, mas isso só é necessário se valores diferentes do padrão forem necessários.</span><span class="sxs-lookup"><span data-stu-id="024ed-112">It is possible to declare parameterized constructors on a struct type to set its initial values, but this is only necessary if values other than the default are required.</span></span>  
  
 <span data-ttu-id="024ed-113">Objetos de tipo de valor, como structs, são criados na pilha, enquanto objetos de tipo de referência, como classes, são criadas no heap.</span><span class="sxs-lookup"><span data-stu-id="024ed-113">Value-type objects such as structs are created on the stack, while reference-type objects such as classes are created on the heap.</span></span> <span data-ttu-id="024ed-114">Os dois tipos de objeto são destruídos automaticamente, mas objetos baseados em tipos de valor são destruídos quando saem do escopo, enquanto objetos baseados em tipos de referência são destruídos em um momento não especificado após a última referência a eles ser removida.</span><span class="sxs-lookup"><span data-stu-id="024ed-114">Both types of objects are destroyed automatically, but objects based on value types are destroyed when they go out of scope, whereas objects based on reference types are destroyed at an unspecified time after the last reference to them is removed.</span></span> <span data-ttu-id="024ed-115">Para tipos de referência que consomem recursos fixos, como grandes quantidades de memória, identificadores de arquivos ou conexões de rede, às vezes é desejável empregar a finalização determinística para garantir que o objeto seja destruído assim que possível.</span><span class="sxs-lookup"><span data-stu-id="024ed-115">For reference types that consume fixed resources such as large amounts of memory, file handles, or network connections, it is sometimes desirable to employ deterministic finalization to ensure that the object is destroyed as soon as possible.</span></span> <span data-ttu-id="024ed-116">Para obter mais informações, consulte [Instrução using](../../../csharp/language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="024ed-116">For more information, see [using Statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span>  
  
 <span data-ttu-id="024ed-117">O operador `new` não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="024ed-117">The `new` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="024ed-118">Se o operador `new` não conseguir alocar memória, ele gerará a exceção <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="024ed-118">If the `new` operator fails to allocate memory, it throws the exception, <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="024ed-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="024ed-119">Example</span></span>  
 <span data-ttu-id="024ed-120">No exemplo a seguir, um objeto `struct` e um objeto de classe são criados e inicializados usando o operador `new` e, em seguida, valores atribuídos.</span><span class="sxs-lookup"><span data-stu-id="024ed-120">In the following example, a `struct` object and a class object are created and initialized by using the `new` operator and then assigned values.</span></span> <span data-ttu-id="024ed-121">Os valores padrão e atribuídos são exibidos.</span><span class="sxs-lookup"><span data-stu-id="024ed-121">The default and the assigned values are displayed.</span></span>  
  
 <span data-ttu-id="024ed-122">[!code-cs[csrefKeywordsOperator#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="024ed-122">[!code-cs[csrefKeywordsOperator#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-operator_1.cs)]</span></span>  
  
 <span data-ttu-id="024ed-123">Observe, no exemplo, que o valor padrão de uma cadeia de caracteres é `null`.</span><span class="sxs-lookup"><span data-stu-id="024ed-123">Notice in the example that the default value of a string is `null`.</span></span> <span data-ttu-id="024ed-124">Portanto, ele não é exibido.</span><span class="sxs-lookup"><span data-stu-id="024ed-124">Therefore, it is not displayed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="024ed-125">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="024ed-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="024ed-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="024ed-126">See Also</span></span>  
 <span data-ttu-id="024ed-127">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="024ed-127">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="024ed-128">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="024ed-128">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="024ed-129">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="024ed-129">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="024ed-130">[Palavras-chave do operador](../../../csharp/language-reference/keywords/operator-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="024ed-130">[Operator Keywords](../../../csharp/language-reference/keywords/operator-keywords.md) </span></span>  
 <span data-ttu-id="024ed-131">[new](../../../csharp/language-reference/keywords/new.md) </span><span class="sxs-lookup"><span data-stu-id="024ed-131">[new](../../../csharp/language-reference/keywords/new.md) </span></span>  
 [<span data-ttu-id="024ed-132">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="024ed-132">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)

