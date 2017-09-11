---
title: "Restrições ao uso de níveis de acessibilidade (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
caps.latest.revision: 21
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
ms.openlocfilehash: 8e49afd38fd776593b87f065a079da0d546df4a6
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="b8a87-102">Restrições ao uso de níveis de acessibilidade (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b8a87-102">Restrictions on Using Accessibility Levels (C# Reference)</span></span>
<span data-ttu-id="b8a87-103">Quando você especifica um tipo em uma declaração, verifique se o nível de acessibilidade do tipo é dependente do nível de acessibilidade de um membro ou de outro tipo.</span><span class="sxs-lookup"><span data-stu-id="b8a87-103">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="b8a87-104">Por exemplo, a classe base direta deve ser, pelo menos, tão acessível quanto a classe derivada.</span><span class="sxs-lookup"><span data-stu-id="b8a87-104">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="b8a87-105">As seguintes declarações causam um erro do compilador porque a classe base `BaseClass` é menos acessível que a `MyClass`:</span><span class="sxs-lookup"><span data-stu-id="b8a87-105">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>  
  
```  
class BaseClass {...}  
public class MyClass: BaseClass {...} // Error  
```  
  
 <span data-ttu-id="b8a87-106">A tabela a seguir resume as restrições nos níveis de acessibilidade declarada.</span><span class="sxs-lookup"><span data-stu-id="b8a87-106">The following table summarizes the restrictions on declared accessibility levels.</span></span>  
  
|<span data-ttu-id="b8a87-107">Contexto</span><span class="sxs-lookup"><span data-stu-id="b8a87-107">Context</span></span>|<span data-ttu-id="b8a87-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8a87-108">Remarks</span></span>|  
|-------------|-------------|  
|[<span data-ttu-id="b8a87-109">Classes</span><span class="sxs-lookup"><span data-stu-id="b8a87-109">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="b8a87-110">A classe base direta de um tipo de classe deve ser, pelo menos, tão acessível quanto o próprio tipo de classe.</span><span class="sxs-lookup"><span data-stu-id="b8a87-110">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|  
|[<span data-ttu-id="b8a87-111">Interfaces</span><span class="sxs-lookup"><span data-stu-id="b8a87-111">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)|<span data-ttu-id="b8a87-112">As interfaces base explícitas de um tipo de interface devem ser, pelo menos, tão acessíveis quanto o próprio tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="b8a87-112">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|  
|[<span data-ttu-id="b8a87-113">Delegados</span><span class="sxs-lookup"><span data-stu-id="b8a87-113">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)|<span data-ttu-id="b8a87-114">O tipo de retorno e os tipos de parâmetro de um tipo delegado devem ser, pelo menos, tão acessíveis quanto o próprio tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="b8a87-114">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|  
|[<span data-ttu-id="b8a87-115">Constantes</span><span class="sxs-lookup"><span data-stu-id="b8a87-115">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="b8a87-116">O tipo de uma constante deve ser, pelo menos, tão acessível quanto a própria constante.</span><span class="sxs-lookup"><span data-stu-id="b8a87-116">The type of a constant must be at least as accessible as the constant itself.</span></span>|  
|[<span data-ttu-id="b8a87-117">Campos</span><span class="sxs-lookup"><span data-stu-id="b8a87-117">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="b8a87-118">O tipo de um campo deve ser, pelo menos, tão acessível quanto o próprio campo.</span><span class="sxs-lookup"><span data-stu-id="b8a87-118">The type of a field must be at least as accessible as the field itself.</span></span>|  
|[<span data-ttu-id="b8a87-119">Métodos</span><span class="sxs-lookup"><span data-stu-id="b8a87-119">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="b8a87-120">O tipo de retorno e os tipos de parâmetro de um método devem ser, pelo menos, tão acessíveis quanto o próprio método.</span><span class="sxs-lookup"><span data-stu-id="b8a87-120">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|  
|[<span data-ttu-id="b8a87-121">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b8a87-121">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="b8a87-122">O tipo de uma propriedade deve ser, pelo menos, tão acessível quanto a propriedade em si.</span><span class="sxs-lookup"><span data-stu-id="b8a87-122">The type of a property must be at least as accessible as the property itself.</span></span>|  
|[<span data-ttu-id="b8a87-123">Eventos</span><span class="sxs-lookup"><span data-stu-id="b8a87-123">Events</span></span>](../../../csharp/programming-guide/events/index.md)|<span data-ttu-id="b8a87-124">O tipo de um evento deve ser, pelo menos, tão acessível quanto o próprio evento.</span><span class="sxs-lookup"><span data-stu-id="b8a87-124">The type of an event must be at least as accessible as the event itself.</span></span>|  
|[<span data-ttu-id="b8a87-125">Indexadores</span><span class="sxs-lookup"><span data-stu-id="b8a87-125">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)|<span data-ttu-id="b8a87-126">O tipo e os tipos de parâmetro de um indexador devem ser, pelo menos, tão acessíveis quanto o próprio indexador.</span><span class="sxs-lookup"><span data-stu-id="b8a87-126">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|  
|[<span data-ttu-id="b8a87-127">Operadores</span><span class="sxs-lookup"><span data-stu-id="b8a87-127">Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|<span data-ttu-id="b8a87-128">O tipo de retorno e os tipos de parâmetro de um operador devem ser, pelo menos, tão acessíveis quanto o próprio operador.</span><span class="sxs-lookup"><span data-stu-id="b8a87-128">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|  
|[<span data-ttu-id="b8a87-129">Construtores</span><span class="sxs-lookup"><span data-stu-id="b8a87-129">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="b8a87-130">Os tipos de parâmetro de um construtor devem ser, pelo menos, tão acessíveis quanto o próprio construtor.</span><span class="sxs-lookup"><span data-stu-id="b8a87-130">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b8a87-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8a87-131">Example</span></span>  
 <span data-ttu-id="b8a87-132">O exemplo a seguir contém declarações incorretas de tipos diferentes.</span><span class="sxs-lookup"><span data-stu-id="b8a87-132">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="b8a87-133">O comentário que segue cada declaração indica o erro do compilador esperado.</span><span class="sxs-lookup"><span data-stu-id="b8a87-133">The comment following each declaration indicates the expected compiler error.</span></span>  
  
```  
// Restrictions on Using Accessibility Levels  
// CS0052 expected as well as CS0053, CS0056, and CS0057  
// To make the program work, change access level of both class B  
// and MyPrivateMethod() to public.  
  
using System;  
  
// A delegate:  
delegate int MyDelegate();  
  
class B  
{  
    // A private method:  
    static int MyPrivateMethod()  
    {  
        return 0;  
    }  
}  
  
public class A  
{  
    // Error: The type B is less accessible than the field A.myField.  
    public B myField = new B();  
  
    // Error: The type B is less accessible  
    // than the constant A.myConst.  
    public readonly B myConst = new B();  
  
    public B MyMethod()  
    {  
        // Error: The type B is less accessible   
        // than the method A.MyMethod.  
        return new B();  
    }  
  
    // Error: The type B is less accessible than the property A.MyProp  
    public B MyProp  
    {  
        set  
        {  
        }  
    }  
  
    MyDelegate d = new MyDelegate(B.MyPrivateMethod);  
    // Even when B is declared public, you still get the error:   
    // "The parameter B.MyPrivateMethod is not accessible due to   
    // protection level."  
  
    public static B operator +(A m1, B m2)  
    {  
        // Error: The type B is less accessible  
        // than the operator A.operator +(A,B)  
        return new B();  
    }  
  
    static void Main()  
    {  
        Console.Write("Compiled successfully");  
    }  
}  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="b8a87-134">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b8a87-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b8a87-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8a87-135">See Also</span></span>  
 <span data-ttu-id="b8a87-136">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="b8a87-136">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="b8a87-137">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b8a87-137">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b8a87-138">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="b8a87-138">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="b8a87-139">[Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="b8a87-139">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="b8a87-140">[Domínio de acessibilidade](../../../csharp/language-reference/keywords/accessibility-domain.md) </span><span class="sxs-lookup"><span data-stu-id="b8a87-140">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md) </span></span>  
 <span data-ttu-id="b8a87-141">[Níveis de Acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="b8a87-141">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="b8a87-142">[Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="b8a87-142">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 <span data-ttu-id="b8a87-143">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="b8a87-143">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="b8a87-144">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="b8a87-144">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="b8a87-145">[protected](../../../csharp/language-reference/keywords/protected.md) </span><span class="sxs-lookup"><span data-stu-id="b8a87-145">[protected](../../../csharp/language-reference/keywords/protected.md) </span></span>  
 [<span data-ttu-id="b8a87-146">internal</span><span class="sxs-lookup"><span data-stu-id="b8a87-146">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)

