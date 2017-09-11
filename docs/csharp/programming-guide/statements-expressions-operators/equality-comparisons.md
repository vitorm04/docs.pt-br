---
title: "Comparações de igualdade (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- object equality [C#]
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 948bbc1b5b8535cc31ea362497fa69a816b43edc
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="equality-comparisons-c-programming-guide"></a><span data-ttu-id="ba76a-102">Comparações de igualdade (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="ba76a-102">Equality Comparisons (C# Programming Guide)</span></span>
<span data-ttu-id="ba76a-103">Às vezes, é necessário comparar dois valores em relação à igualdade.</span><span class="sxs-lookup"><span data-stu-id="ba76a-103">It is sometimes necessary to compare two values for equality.</span></span> <span data-ttu-id="ba76a-104">Em alguns casos, testa-se a *igualdade de valor*, também conhecida como *equivalência*, o que significa que os valores contidos pelas duas variáveis são iguais.</span><span class="sxs-lookup"><span data-stu-id="ba76a-104">In some cases, you are testing for *value equality*, also known as *equivalence*, which means that the values that are contained by the two variables are equal.</span></span> <span data-ttu-id="ba76a-105">Em outros casos, é necessário determinar se duas variáveis se referem ao mesmo objeto subjacente na memória.</span><span class="sxs-lookup"><span data-stu-id="ba76a-105">In other cases, you have to determine whether two variables refer to the same underlying object in memory.</span></span> <span data-ttu-id="ba76a-106">Esse tipo de igualdade é chamado *igualdade de referência* ou *identidade*.</span><span class="sxs-lookup"><span data-stu-id="ba76a-106">This type of equality is called *reference equality*, or *identity*.</span></span> <span data-ttu-id="ba76a-107">Este tópico descreve esses dois tipos de igualdade e fornece links para outros tópicos que fornecem mais informações.</span><span class="sxs-lookup"><span data-stu-id="ba76a-107">This topic describes these two kinds of equality and provides links to other topics for more information.</span></span>  
  
## <a name="reference-equality"></a><span data-ttu-id="ba76a-108">Igualdade de Referência</span><span class="sxs-lookup"><span data-stu-id="ba76a-108">Reference Equality</span></span>  
 <span data-ttu-id="ba76a-109">Igualdade de referência significa que as duas referências de objeto se referem ao mesmo objeto subjacente.</span><span class="sxs-lookup"><span data-stu-id="ba76a-109">Reference equality means that two object references refer to the same underlying object.</span></span> <span data-ttu-id="ba76a-110">Isso pode ocorrer por meio de uma atribuição simples, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ba76a-110">This can occur through simple assignment, as shown in the following example.</span></span>  
  
 <span data-ttu-id="ba76a-111">[!code-cs[csProgGuideStatements#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/equality-comparisons_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ba76a-111">[!code-cs[csProgGuideStatements#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/equality-comparisons_1.cs)]</span></span>  
  
 <span data-ttu-id="ba76a-112">Nesse código, dois objetos são criados, mas após a instrução de atribuição, ambas as referências se referem ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="ba76a-112">In this code, two objects are created, but after the assignment statement, both references refer to the same object.</span></span> <span data-ttu-id="ba76a-113">Portanto, eles têm igualdade de referência.</span><span class="sxs-lookup"><span data-stu-id="ba76a-113">Therefore they have reference equality.</span></span> <span data-ttu-id="ba76a-114">Use o método <xref:System.Object.ReferenceEquals%2A> para determinar se duas referências referenciam o mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="ba76a-114">Use the <xref:System.Object.ReferenceEquals%2A> method to determine whether two references refer to the same object.</span></span>  
  
 <span data-ttu-id="ba76a-115">O conceito de igualdade de referência se aplica apenas a tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="ba76a-115">The concept of reference equality applies only to reference types.</span></span> <span data-ttu-id="ba76a-116">Objetos de tipo de valor não podem ter igualdade de referência, pois quando uma instância de um tipo de valor é atribuída a uma variável, uma cópia do valor é gerada.</span><span class="sxs-lookup"><span data-stu-id="ba76a-116">Value type objects cannot have reference equality because when an instance of a value type is assigned to a variable, a copy of the value is made.</span></span> <span data-ttu-id="ba76a-117">Portanto, não é possível ter dois structs desconvertidos que referenciam o mesmo local na memória.</span><span class="sxs-lookup"><span data-stu-id="ba76a-117">Therefore you can never have two unboxed structs that refer to the same location in memory.</span></span> <span data-ttu-id="ba76a-118">Além disso, se <xref:System.Object.ReferenceEquals%2A> for usado para comparar dois tipos de valor, o resultado sempre será `false`, mesmo se os valores contidos nos objetos forem idênticos.</span><span class="sxs-lookup"><span data-stu-id="ba76a-118">Furthermore, if you use <xref:System.Object.ReferenceEquals%2A> to compare two value types, the result will always be `false`, even if the values that are contained in the objects are all identical.</span></span> <span data-ttu-id="ba76a-119">Isso ocorre porque cada variável é convertido em uma instância de objeto separada.</span><span class="sxs-lookup"><span data-stu-id="ba76a-119">This is because each variable is boxed into a separate object instance.</span></span> <span data-ttu-id="ba76a-120">Para obter mais informações, consulte [Como Testar a Igualdade de Referência (Identidade)](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).</span><span class="sxs-lookup"><span data-stu-id="ba76a-120">For more information, see [How to: Test for Reference Equality (Identity)](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).</span></span>  
  
## <a name="value-equality"></a><span data-ttu-id="ba76a-121">Igualdade de Valor</span><span class="sxs-lookup"><span data-stu-id="ba76a-121">Value Equality</span></span>  
 <span data-ttu-id="ba76a-122">Igualdade de valor significa que dois objetos contêm o mesmo valor ou valores.</span><span class="sxs-lookup"><span data-stu-id="ba76a-122">Value equality means that two objects contain the same value or values.</span></span> <span data-ttu-id="ba76a-123">Para tipos de valor primitivos, como [int](../../../csharp/language-reference/keywords/int.md) ou [bool](../../../csharp/language-reference/keywords/bool.md), os testes de igualdade de valor são simples.</span><span class="sxs-lookup"><span data-stu-id="ba76a-123">For primitive value types such as [int](../../../csharp/language-reference/keywords/int.md) or [bool](../../../csharp/language-reference/keywords/bool.md), tests for value equality are straightforward.</span></span> <span data-ttu-id="ba76a-124">É possível usar o operador [==](../../../csharp/language-reference/operators/equality-comparison-operator.md), conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ba76a-124">You can use the [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) operator, as shown in the following example.</span></span>  
  
```csharp  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.   
if( b == a)   
{  
    // The two integers are equal.  
}  
```  
  
 <span data-ttu-id="ba76a-125">Para a maioria dos outros tipos, o teste de igualdade de valor é mais complexo, pois é necessário entender como o tipo o define.</span><span class="sxs-lookup"><span data-stu-id="ba76a-125">For most other types, testing for value equality is more complex because it requires that you understand how the type defines it.</span></span> <span data-ttu-id="ba76a-126">Para classes e structs que têm vários campos ou propriedades, a igualdade de valor geralmente é definida para determinar que todos os campos ou propriedades tenham o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="ba76a-126">For classes and structs that have multiple fields or properties, value equality is often defined to mean that all fields or properties have the same value.</span></span> <span data-ttu-id="ba76a-127">Por exemplo, dois objetos `Point` podem ser definidos para serem equivalentes se pointA.X for igual a pointB.X e pointA.Y for igual a pointB.Y.</span><span class="sxs-lookup"><span data-stu-id="ba76a-127">For example, two `Point` objects might be defined to be equivalent if pointA.X is equal to pointB.X and pointA.Y is equal to pointB.Y.</span></span>  
  
 <span data-ttu-id="ba76a-128">No entanto, não há nenhuma exigência de que a equivalência seja baseada em todos os campos em um tipo.</span><span class="sxs-lookup"><span data-stu-id="ba76a-128">However, there is no requirement that equivalence be based on all the fields in a type.</span></span> <span data-ttu-id="ba76a-129">Ela pode ser baseada em um subconjunto.</span><span class="sxs-lookup"><span data-stu-id="ba76a-129">It can be based on a subset.</span></span> <span data-ttu-id="ba76a-130">Ao comparar tipos que não são de sua propriedade, certifique-se de que a forma como a equivalência é definida especificamente para esse tipo foi entendida.</span><span class="sxs-lookup"><span data-stu-id="ba76a-130">When you compare types that you do not own, you should make sure to understand specifically how equivalence is defined for that type.</span></span> <span data-ttu-id="ba76a-131">Para obter mais informações sobre como definir a igualdade de valor em suas próprias classes e structs, consulte [Como Definir a Igualdade de Valor para um Tipo](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).</span><span class="sxs-lookup"><span data-stu-id="ba76a-131">For more information about how to define value equality in your own classes and structs, see [How to: Define Value Equality for a Type](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).</span></span>  
  
### <a name="value-equality-for-floating-point-values"></a><span data-ttu-id="ba76a-132">Igualdade de Valor para Valores de Ponto Flutuante</span><span class="sxs-lookup"><span data-stu-id="ba76a-132">Value Equality for Floating Point Values</span></span>  
 <span data-ttu-id="ba76a-133">Comparações de igualdade de valores de ponto flutuante ([double](../../../csharp/language-reference/keywords/double.md) e [float](../../../csharp/language-reference/keywords/float.md)) são problemáticas em razão da imprecisão aritmética do ponto flutuante em computadores binários.</span><span class="sxs-lookup"><span data-stu-id="ba76a-133">Equality comparisons of floating point values ([double](../../../csharp/language-reference/keywords/double.md) and [float](../../../csharp/language-reference/keywords/float.md)) are problematic because of the imprecision of floating point arithmetic on binary computers.</span></span> <span data-ttu-id="ba76a-134">Para obter mais informações, consulte os comentários no tópico <xref:System.Double?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="ba76a-134">For more information, see the remarks in the topic <xref:System.Double?displayProperty=fullName>.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="ba76a-135">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="ba76a-135">Related Topics</span></span>  
  
|<span data-ttu-id="ba76a-136">Título</span><span class="sxs-lookup"><span data-stu-id="ba76a-136">Title</span></span>|<span data-ttu-id="ba76a-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba76a-137">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ba76a-138">Como testar a igualdade de referência (identidade)</span><span class="sxs-lookup"><span data-stu-id="ba76a-138">How to: Test for Reference Equality (Identity)</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)|<span data-ttu-id="ba76a-139">Descreve como determinar se duas variáveis têm igualdade de referência.</span><span class="sxs-lookup"><span data-stu-id="ba76a-139">Describes how to determine whether two variables have reference equality.</span></span>|  
|[<span data-ttu-id="ba76a-140">Como definir a igualdade de valor para um tipo</span><span class="sxs-lookup"><span data-stu-id="ba76a-140">How to: Define Value Equality for a Type</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)|<span data-ttu-id="ba76a-141">Descreve como fornecer uma definição personalizada de igualdade de valor a um tipo.</span><span class="sxs-lookup"><span data-stu-id="ba76a-141">Describes how to provide a custom definition of value equality for a type.</span></span>|  
|[<span data-ttu-id="ba76a-142">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="ba76a-142">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)|<span data-ttu-id="ba76a-143">Fornece links para informações detalhadas sobre recursos importantes da linguagem C# e recursos disponíveis para o C# por meio do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ba76a-143">Provides links to detailed information about important C# language features and features that are available to C# through the .NET Framework.</span></span>|  
|[<span data-ttu-id="ba76a-144">Tipos</span><span class="sxs-lookup"><span data-stu-id="ba76a-144">Types</span></span>](../../../csharp/programming-guide/types/index.md)|<span data-ttu-id="ba76a-145">Fornece informações sobre o sistema de tipos do C# e links para mais informações.</span><span class="sxs-lookup"><span data-stu-id="ba76a-145">Provides information about the C# type system and links to additional information.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba76a-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba76a-146">See Also</span></span>  
 [<span data-ttu-id="ba76a-147">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="ba76a-147">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)

