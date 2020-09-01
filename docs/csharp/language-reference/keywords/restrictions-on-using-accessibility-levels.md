---
description: Restrições ao uso de níveis de acessibilidade – Referência em C#
title: Restrições ao uso de níveis de acessibilidade – Referência em C#
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 542e463e41c70f2e8aed5c20dc1294e296a88518
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136987"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="3a8cb-103">Restrições ao uso de níveis de acessibilidade (Referência em C#)</span><span class="sxs-lookup"><span data-stu-id="3a8cb-103">Restrictions on using accessibility levels (C# Reference)</span></span>

<span data-ttu-id="3a8cb-104">Quando você especifica um tipo em uma declaração, verifique se o nível de acessibilidade do tipo é dependente do nível de acessibilidade de um membro ou de outro tipo.</span><span class="sxs-lookup"><span data-stu-id="3a8cb-104">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="3a8cb-105">Por exemplo, a classe base direta deve ser, pelo menos, tão acessível quanto a classe derivada.</span><span class="sxs-lookup"><span data-stu-id="3a8cb-105">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="3a8cb-106">As seguintes declarações causam um erro do compilador porque a classe base `BaseClass` é menos acessível que a `MyClass`:</span><span class="sxs-lookup"><span data-stu-id="3a8cb-106">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

<span data-ttu-id="3a8cb-107">A tabela a seguir resume as restrições nos níveis de acessibilidade declarada.</span><span class="sxs-lookup"><span data-stu-id="3a8cb-107">The following table summarizes the restrictions on declared accessibility levels.</span></span>

|<span data-ttu-id="3a8cb-108">Contexto</span><span class="sxs-lookup"><span data-stu-id="3a8cb-108">Context</span></span>|<span data-ttu-id="3a8cb-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a8cb-109">Remarks</span></span>|
|-------------|-------------|
|[<span data-ttu-id="3a8cb-110">Classes</span><span class="sxs-lookup"><span data-stu-id="3a8cb-110">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="3a8cb-111">A classe base direta de um tipo de classe deve ser, pelo menos, tão acessível quanto o próprio tipo de classe.</span><span class="sxs-lookup"><span data-stu-id="3a8cb-111">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|
|[<span data-ttu-id="3a8cb-112">Interfaces</span><span class="sxs-lookup"><span data-stu-id="3a8cb-112">Interfaces</span></span>](../../programming-guide/interfaces/index.md)|<span data-ttu-id="3a8cb-113">As interfaces base explícitas de um tipo de interface devem ser, pelo menos, tão acessíveis quanto o próprio tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="3a8cb-113">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|
|[<span data-ttu-id="3a8cb-114">Representantes</span><span class="sxs-lookup"><span data-stu-id="3a8cb-114">Delegates</span></span>](../../programming-guide/delegates/index.md)|<span data-ttu-id="3a8cb-115">O tipo de retorno e os tipos de parâmetro de um tipo delegado devem ser, pelo menos, tão acessíveis quanto o próprio tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="3a8cb-115">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|
|[<span data-ttu-id="3a8cb-116">Constantes</span><span class="sxs-lookup"><span data-stu-id="3a8cb-116">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="3a8cb-117">O tipo de uma constante deve ser, pelo menos, tão acessível quanto a própria constante.</span><span class="sxs-lookup"><span data-stu-id="3a8cb-117">The type of a constant must be at least as accessible as the constant itself.</span></span>|
|[<span data-ttu-id="3a8cb-118">Fields</span><span class="sxs-lookup"><span data-stu-id="3a8cb-118">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="3a8cb-119">O tipo de um campo deve ser, pelo menos, tão acessível quanto o próprio campo.</span><span class="sxs-lookup"><span data-stu-id="3a8cb-119">The type of a field must be at least as accessible as the field itself.</span></span>|
|[<span data-ttu-id="3a8cb-120">Métodos</span><span class="sxs-lookup"><span data-stu-id="3a8cb-120">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="3a8cb-121">O tipo de retorno e os tipos de parâmetro de um método devem ser, pelo menos, tão acessíveis quanto o próprio método.</span><span class="sxs-lookup"><span data-stu-id="3a8cb-121">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|
|[<span data-ttu-id="3a8cb-122">Propriedades</span><span class="sxs-lookup"><span data-stu-id="3a8cb-122">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="3a8cb-123">O tipo de uma propriedade deve ser, pelo menos, tão acessível quanto a propriedade em si.</span><span class="sxs-lookup"><span data-stu-id="3a8cb-123">The type of a property must be at least as accessible as the property itself.</span></span>|
|[<span data-ttu-id="3a8cb-124">Eventos</span><span class="sxs-lookup"><span data-stu-id="3a8cb-124">Events</span></span>](../../programming-guide/events/index.md)|<span data-ttu-id="3a8cb-125">O tipo de um evento deve ser, pelo menos, tão acessível quanto o próprio evento.</span><span class="sxs-lookup"><span data-stu-id="3a8cb-125">The type of an event must be at least as accessible as the event itself.</span></span>|
|[<span data-ttu-id="3a8cb-126">Indexadores</span><span class="sxs-lookup"><span data-stu-id="3a8cb-126">Indexers</span></span>](../../programming-guide/indexers/index.md)|<span data-ttu-id="3a8cb-127">O tipo e os tipos de parâmetro de um indexador devem ser, pelo menos, tão acessíveis quanto o próprio indexador.</span><span class="sxs-lookup"><span data-stu-id="3a8cb-127">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|
|[<span data-ttu-id="3a8cb-128">Operadores</span><span class="sxs-lookup"><span data-stu-id="3a8cb-128">Operators</span></span>](../operators/index.md)|<span data-ttu-id="3a8cb-129">O tipo de retorno e os tipos de parâmetro de um operador devem ser, pelo menos, tão acessíveis quanto o próprio operador.</span><span class="sxs-lookup"><span data-stu-id="3a8cb-129">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|
|[<span data-ttu-id="3a8cb-130">Construtores</span><span class="sxs-lookup"><span data-stu-id="3a8cb-130">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="3a8cb-131">Os tipos de parâmetro de um construtor devem ser, pelo menos, tão acessíveis quanto o próprio construtor.</span><span class="sxs-lookup"><span data-stu-id="3a8cb-131">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|

## <a name="example"></a><span data-ttu-id="3a8cb-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3a8cb-132">Example</span></span>

<span data-ttu-id="3a8cb-133">O exemplo a seguir contém declarações incorretas de tipos diferentes.</span><span class="sxs-lookup"><span data-stu-id="3a8cb-133">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="3a8cb-134">O comentário que segue cada declaração indica o erro do compilador esperado.</span><span class="sxs-lookup"><span data-stu-id="3a8cb-134">The comment following each declaration indicates the expected compiler error.</span></span>

```csharp
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

## <a name="c-language-specification"></a><span data-ttu-id="3a8cb-135">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="3a8cb-135">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3a8cb-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="3a8cb-136">See also</span></span>

- [<span data-ttu-id="3a8cb-137">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="3a8cb-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3a8cb-138">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="3a8cb-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3a8cb-139">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="3a8cb-139">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3a8cb-140">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="3a8cb-140">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="3a8cb-141">Domínio de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="3a8cb-141">Accessibility Domain</span></span>](accessibility-domain.md)
- [<span data-ttu-id="3a8cb-142">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="3a8cb-142">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="3a8cb-143">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="3a8cb-143">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="3a8cb-144">public</span><span class="sxs-lookup"><span data-stu-id="3a8cb-144">public</span></span>](public.md)
- [<span data-ttu-id="3a8cb-145">particulares</span><span class="sxs-lookup"><span data-stu-id="3a8cb-145">private</span></span>](private.md)
- [<span data-ttu-id="3a8cb-146">protegidos</span><span class="sxs-lookup"><span data-stu-id="3a8cb-146">protected</span></span>](protected.md)
- [<span data-ttu-id="3a8cb-147">interno</span><span class="sxs-lookup"><span data-stu-id="3a8cb-147">internal</span></span>](internal.md)
