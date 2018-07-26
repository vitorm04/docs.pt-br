---
title: where (restrição de tipo genérico) (Referência de C#)
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 94db10c81af55030dfcf6e210a86658c84868e42
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961075"
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="77fc9-102">where (restrição de tipo genérico) (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="77fc9-102">where (generic type constraint) (C# Reference)</span></span>

<span data-ttu-id="77fc9-103">A cláusula `where` em uma definição genérica especifica restrições sobre os tipos que são usados como argumentos para parâmetros de tipo em um tipo genérico, método, delegado ou função local.</span><span class="sxs-lookup"><span data-stu-id="77fc9-103">The `where` clause in a generic definition specifies constraints on the types that are used as arguments for type parameters in a generic type, method, delegate, or local function.</span></span> <span data-ttu-id="77fc9-104">Restrições podem especificar interfaces, classes base ou exigir que um tipo genérico seja uma referência, valor ou tipo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="77fc9-104">Constraints can specify interfaces, base classes, or require a generic type to be a reference, value or unmanaged type.</span></span> <span data-ttu-id="77fc9-105">Elas declaram funcionalidades que o argumento de tipo deve ter.</span><span class="sxs-lookup"><span data-stu-id="77fc9-105">They declare capabilities that the type argument must possess.</span></span>

<span data-ttu-id="77fc9-106">Por exemplo, você pode declarar uma classe genérica, `MyGenericClass`, de modo que o parâmetro de tipo `T` implementa a interface <xref:System.IComparable%601>:</span><span class="sxs-lookup"><span data-stu-id="77fc9-106">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> <span data-ttu-id="77fc9-107">Para obter mais informações sobre a cláusula where em uma expressão de consulta, consulte [Cláusula where](where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="77fc9-107">For more information on the where clause in a query expression, see [where clause](where-clause.md).</span></span>

<span data-ttu-id="77fc9-108">A cláusula `where` também pode incluir uma restrição de classe base.</span><span class="sxs-lookup"><span data-stu-id="77fc9-108">The `where` clause can also include a base class constraint.</span></span> <span data-ttu-id="77fc9-109">A restrição de classe base declara que um tipo a ser usado como um argumento de tipo para aquele tipo genérico tem a classe especificada como uma classe base (ou é que a classe base) a ser usada como um argumento de tipo para aquele tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="77fc9-109">The base class constraint states that a type to be used as a type argument for that generic type has the specified class as a base class (or is that base class) to be used as a type argument for that generic type.</span></span> <span data-ttu-id="77fc9-110">Se a restrição de classe base for usada, ela deverá aparecer antes de qualquer outra restrição nesse parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="77fc9-110">If the base class constraint is used, it must appear before any other constraints on that type parameter.</span></span> <span data-ttu-id="77fc9-111">Alguns tipos não têm permissão como uma restrição de classe base: <xref:System.Object>, <xref:System.Array> e <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="77fc9-111">Some types are disallowed as a base class constraint: <xref:System.Object>, <xref:System.Array>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="77fc9-112">Antes do C# 7.3, <xref:System.Enum>, <xref:System.Delegate> e <xref:System.MulticastDelegate> também não tinham permissão como restrições de classe base.</span><span class="sxs-lookup"><span data-stu-id="77fc9-112">Prior to C# 7.3, <xref:System.Enum>, <xref:System.Delegate>, and <xref:System.MulticastDelegate> were also disallowed as base class constraints.</span></span> <span data-ttu-id="77fc9-113">O exemplo a seguir mostra os tipos que agora podem ser especificados como classe base:</span><span class="sxs-lookup"><span data-stu-id="77fc9-113">The following example shows the types that can now be specified as a base class:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

<span data-ttu-id="77fc9-114">A cláusula `where` pode especificar que o tipo é um `class` ou um `struct`.</span><span class="sxs-lookup"><span data-stu-id="77fc9-114">The `where` clause can specify that the type is a `class` or a `struct`.</span></span> <span data-ttu-id="77fc9-115">A restrição `struct` elimina a necessidade de especificar uma restrição de classe base de `System.ValueType`.</span><span class="sxs-lookup"><span data-stu-id="77fc9-115">The `struct` constraint removes the need to specify a base class constraint of `System.ValueType`.</span></span> <span data-ttu-id="77fc9-116">O tipo `System.ValueType` não pode ser usado como uma restrição de classe base.</span><span class="sxs-lookup"><span data-stu-id="77fc9-116">The `System.ValueType` type may not be used as a base class constraint.</span></span> <span data-ttu-id="77fc9-117">O exemplo a seguir mostra as restrições `class` e `struct`:</span><span class="sxs-lookup"><span data-stu-id="77fc9-117">The following example shows both the `class` and `struct` constraints:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

<span data-ttu-id="77fc9-118">A cláusula `where` também pode incluir uma restrição `unmanaged`.</span><span class="sxs-lookup"><span data-stu-id="77fc9-118">The `where` clause may also include an `unmanaged` constraint.</span></span> <span data-ttu-id="77fc9-119">A restrição `unmanaged` limita o parâmetro de tipo a tipos conhecidos como **tipos não gerenciados**.</span><span class="sxs-lookup"><span data-stu-id="77fc9-119">The `unmanaged` constraint limits the type parameter to types known as **unmanaged types**.</span></span> <span data-ttu-id="77fc9-120">Um **tipo não gerenciado** é um tipo que não é um tipo de referência e não contém campos de tipo de referência em nenhum nível de aninhamento.</span><span class="sxs-lookup"><span data-stu-id="77fc9-120">An **unmanaged type** is a type that isn't a reference type and doesn't contain reference type fields at any level of nesting.</span></span> <span data-ttu-id="77fc9-121">Usando a restrição `unmanaged`, é mais fácil escrever o código de interoperabilidade de nível baixo em C#.</span><span class="sxs-lookup"><span data-stu-id="77fc9-121">The `unmanaged` constraint makes it easier to write low-level interop code in C#.</span></span> <span data-ttu-id="77fc9-122">Essa restrição habilita rotinas reutilizáveis em todos os tipos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="77fc9-122">This constraint enables reusable routines across all unmanaged types.</span></span> <span data-ttu-id="77fc9-123">A restrição `unmanaged` não pode ser combinada à restrição `class` ou `struct`.</span><span class="sxs-lookup"><span data-stu-id="77fc9-123">The `unmanaged` constraint can't be combined with the `class` or `struct` constraint.</span></span> <span data-ttu-id="77fc9-124">A restrição `unmanaged` impõe que o tipo deve ser um `struct`:</span><span class="sxs-lookup"><span data-stu-id="77fc9-124">The `unmanaged` constraint enforces that the type must be a `struct`:</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

<span data-ttu-id="77fc9-125">A cláusula `where` também pode incluir uma restrição de construtor, `new()`.</span><span class="sxs-lookup"><span data-stu-id="77fc9-125">The `where` clause may also include a constructor constraint, `new()`.</span></span> <span data-ttu-id="77fc9-126">Essa restrição torna possível criar uma instância de um parâmetro de tipo usando o operador `new`.</span><span class="sxs-lookup"><span data-stu-id="77fc9-126">That constraint makes it possible to create an instance of a type parameter using the `new` operator.</span></span> <span data-ttu-id="77fc9-127">A [restrição new()](new-constraint.md) informa o compilador que qualquer argumento de tipo fornecido deve ter um construtor – ou padrão – sem parâmetros acessível.</span><span class="sxs-lookup"><span data-stu-id="77fc9-127">The [new() Constraint](new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="77fc9-128">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="77fc9-128">For example:</span></span>

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

<span data-ttu-id="77fc9-129">A restrição `new()` aparece por último na cláusula `where`.</span><span class="sxs-lookup"><span data-stu-id="77fc9-129">The `new()` constraint appears last in the `where` clause.</span></span> <span data-ttu-id="77fc9-130">A restrição `new()` não pode ser combinada às restrições `struct` ou `unmanaged`.</span><span class="sxs-lookup"><span data-stu-id="77fc9-130">The `new()` constraint can't be combined with the `struct` or `unmanaged` constraints.</span></span> <span data-ttu-id="77fc9-131">Todos os tipos que satisfazem as restrições devem ter um construtor sem parâmetros acessível, tornando a restrição `new()` redundante.</span><span class="sxs-lookup"><span data-stu-id="77fc9-131">All types satisfying those constraints must have an accessible parameterless constructor, making the `new()` constraint redundant.</span></span>

<span data-ttu-id="77fc9-132">Com vários parâmetros de tipo, use uma cláusula `where` para cada parâmetro de tipo, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="77fc9-132">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

<span data-ttu-id="77fc9-133">Você também pode anexar restrições a parâmetros de tipo de métodos genéricos, como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="77fc9-133">You can also attach constraints to type parameters of generic methods, as shown in the following example:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

<span data-ttu-id="77fc9-134">Observe que a sintaxe para descrever as restrições de parâmetro de tipo em delegados é a mesma que a dos métodos:</span><span class="sxs-lookup"><span data-stu-id="77fc9-134">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

<span data-ttu-id="77fc9-135">Para obter informações sobre delegados genéricos, consulte [Delegados genéricos](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="77fc9-135">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>

<span data-ttu-id="77fc9-136">Para obter detalhes sobre a sintaxe e o uso de restrições, consulte [Restrições a parâmetros de tipo](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="77fc9-136">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="77fc9-137">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="77fc9-137">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="77fc9-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77fc9-138">See also</span></span>

 [<span data-ttu-id="77fc9-139">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="77fc9-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="77fc9-140">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="77fc9-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="77fc9-141">Introdução aos genéricos</span><span class="sxs-lookup"><span data-stu-id="77fc9-141">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="77fc9-142">Restrição new</span><span class="sxs-lookup"><span data-stu-id="77fc9-142">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)  
 [<span data-ttu-id="77fc9-143">Restrições a parâmetros de tipo</span><span class="sxs-lookup"><span data-stu-id="77fc9-143">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
