---
title: "expressões de valor padrão (guia de programação em C#)"
description: "As expressões de valor padrão produzem o valor padrão para qualquer tipo de referência ou tipo de valor"
ms.date: 2017-08-23
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 1e548df4de2c07934313311a7ffcfae82be76000
ms.openlocfilehash: 7b5b53d7ed92c6f6377a3e494daf1d02a4cf0934
ms.contentlocale: pt-br
ms.lasthandoff: 08/29/2017

---
# <a name="default-value-expressions-c-programming-guide"></a><span data-ttu-id="995dd-103">Expressões de valor padrão (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="995dd-103">default value expressions (C# programming guide)</span></span>

<span data-ttu-id="995dd-104">Uma expressão de valor padrão produz o valor padrão para um tipo.</span><span class="sxs-lookup"><span data-stu-id="995dd-104">A default value expression produces the default value for a type.</span></span> <span data-ttu-id="995dd-105">As expressões de valores padrão são úteis principalmente em classes e métodos genéricos.</span><span class="sxs-lookup"><span data-stu-id="995dd-105">Default value expressions are particularly useful in generic classes and methods.</span></span> <span data-ttu-id="995dd-106">Um problema que surge ao usar genéricos é como atribuir um valor padrão a um tipo parametrizado `T` quando você ainda não sabe o seguinte:</span><span class="sxs-lookup"><span data-stu-id="995dd-106">One issue that arises using generics is how to assign a default value to a parameterized type `T` when you do not know the following in advance:</span></span>

- <span data-ttu-id="995dd-107">Se `T` é um tipo de referência ou um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="995dd-107">Whether `T` is a reference type or a value type.</span></span>
- <span data-ttu-id="995dd-108">Quando `T` é um tipo de valor, se ele é um valor numérico ou um struct definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="995dd-108">If `T` is a value type, whether is a numeric value or a user-defined struct.</span></span>

 <span data-ttu-id="995dd-109">Dada uma variável `t` de um tipo parametrizado `T`, a instrução `t = null` só será válida se `T` for um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="995dd-109">Given a variable `t` of a parameterized type `T`, the statement `t = null` is only valid if `T` is a reference type.</span></span> <span data-ttu-id="995dd-110">A atribuição `t = 0` funciona apenas para tipos de valor numérico, mas não para structs.</span><span class="sxs-lookup"><span data-stu-id="995dd-110">The assignment `t = 0` only works for numeric value types but not for structs.</span></span> <span data-ttu-id="995dd-111">A solução é usar uma expressão de valor padrão, que retorna `null` para tipos de referência (tipos de classes e tipos de interface) e zero para tipos de valor numérico.</span><span class="sxs-lookup"><span data-stu-id="995dd-111">The solution is to use a default value expression, which returns `null` for reference types (class types and interface types) and zero for numeric value types.</span></span> <span data-ttu-id="995dd-112">Para estruturas definidas pelo usuário, ela retorna o struct inicializado para o padrão de bit zero, que produz 0 ou `null` para cada membro dependendo se tal membro é um tipo de valor ou de referência.</span><span class="sxs-lookup"><span data-stu-id="995dd-112">For user-defined structs, it returns the struct initialized to the zero bit pattern, which produces 0 or `null` for each member depending on whether that member is a value or reference type.</span></span> <span data-ttu-id="995dd-113">Para tipos que permitem valor nulo, `default` retorna um <xref:System.Nullable%601?displayProperty=fullName>, que é inicializado como qualquer struct.</span><span class="sxs-lookup"><span data-stu-id="995dd-113">For nullable value types, `default` returns a <xref:System.Nullable%601?displayProperty=fullName>, which is initialized like any struct.</span></span>

<span data-ttu-id="995dd-114">A expressão `default(T)` não é limitada a classes e métodos genéricos.</span><span class="sxs-lookup"><span data-stu-id="995dd-114">The `default(T)` expression is not limited to generic classes and methods.</span></span> <span data-ttu-id="995dd-115">As expressões de valor padrão podem ser usadas com qualquer tipo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="995dd-115">Default value expressions can be used with any managed type.</span></span> <span data-ttu-id="995dd-116">Todas estas expressões são válidas:</span><span class="sxs-lookup"><span data-stu-id="995dd-116">Any of these expressions are valid:</span></span>

 <span data-ttu-id="995dd-117">[!code-cs[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]</span><span class="sxs-lookup"><span data-stu-id="995dd-117">[!code-cs[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]</span></span>

 <span data-ttu-id="995dd-118">O exemplo da classe `GenericList<T>` a seguir mostra como usar o operador `default(T)` em uma classe genérica.</span><span class="sxs-lookup"><span data-stu-id="995dd-118">The following example from the `GenericList<T>` class shows how to use the `default(T)` operator in a generic class.</span></span> <span data-ttu-id="995dd-119">Para obter mais informações, consulte [Visão geral de genéricos](../generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="995dd-119">For more information, see [Generics Overview](../generics/introduction-to-generics.md).</span></span>

 <span data-ttu-id="995dd-120">[!code-cs[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]</span><span class="sxs-lookup"><span data-stu-id="995dd-120">[!code-cs[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]</span></span>

## <a name="default-literal-and-type-inference"></a><span data-ttu-id="995dd-121">Inferência de tipo e literal padrão</span><span class="sxs-lookup"><span data-stu-id="995dd-121">default literal and type inference</span></span>

<span data-ttu-id="995dd-122">A partir do C# 7.1, o literal `default` pode ser usado para expressões de valor padrão quando o compilador pode inferir o tipo da expressão.</span><span class="sxs-lookup"><span data-stu-id="995dd-122">Beginning with C# 7.1, the `default` literal can be used for default value expressions when the compiler can infer the type of the expression.</span></span> <span data-ttu-id="995dd-123">O literal `default` produz o mesmo valor que o equivalente `default(T)`, em que `T` é o tipo inferido.</span><span class="sxs-lookup"><span data-stu-id="995dd-123">The `default` literal produces the same value as the equivalent `default(T)` where `T` is the inferred type.</span></span> <span data-ttu-id="995dd-124">Isso pode tornar código mais conciso, reduzindo a redundância de declarar um tipo mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="995dd-124">This can make code more concise by reducing the redundancy of declaring a type more than once.</span></span> <span data-ttu-id="995dd-125">O literal `default` pode ser usado em todos os locais a seguir:</span><span class="sxs-lookup"><span data-stu-id="995dd-125">The `default` literal can be used in any of the following locations:</span></span>

- <span data-ttu-id="995dd-126">inicializador de variável</span><span class="sxs-lookup"><span data-stu-id="995dd-126">variable initializer</span></span>
- <span data-ttu-id="995dd-127">atribuição de variável</span><span class="sxs-lookup"><span data-stu-id="995dd-127">variable assignment</span></span>
- <span data-ttu-id="995dd-128">declarando o valor padrão para um parâmetro opcional</span><span class="sxs-lookup"><span data-stu-id="995dd-128">declaring the default value for an optional parameter</span></span>
- <span data-ttu-id="995dd-129">fornecendo o valor para um argumento de chamada de método</span><span class="sxs-lookup"><span data-stu-id="995dd-129">providing the value for a method call argument</span></span>
- <span data-ttu-id="995dd-130">instrução de retorno (ou expressão em um membro no corpo da expressão)</span><span class="sxs-lookup"><span data-stu-id="995dd-130">return statement (or expression in an expression bodied member)</span></span>

<span data-ttu-id="995dd-131">O exemplo a seguir mostra vários tipos de uso do literal `default` em uma expressão de valor padrão:</span><span class="sxs-lookup"><span data-stu-id="995dd-131">The following example shows many usages of the `default` literal in a default value expression:</span></span>

<span data-ttu-id="995dd-132">[!code-cs[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]</span><span class="sxs-lookup"><span data-stu-id="995dd-132">[!code-cs[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]</span></span>

## <a name="see-also"></a><span data-ttu-id="995dd-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="995dd-133">See also</span></span>

 <span data-ttu-id="995dd-134"><xref:System.Collections.Generic>[Guia de Programação em C#](../index.md) </span><span class="sxs-lookup"><span data-stu-id="995dd-134"><xref:System.Collections.Generic> [C# Programming Guide](../index.md) </span></span>  
 <span data-ttu-id="995dd-135">[Genéricos](../generics/index.md) </span><span class="sxs-lookup"><span data-stu-id="995dd-135">[Generics](../generics/index.md) </span></span>  
 <span data-ttu-id="995dd-136">[Métodos Genéricos](../generics/generic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="995dd-136">[Generic Methods](../generics/generic-methods.md) </span></span>  
 [<span data-ttu-id="995dd-137">Genéricos</span><span class="sxs-lookup"><span data-stu-id="995dd-137">Generics</span></span>](~/docs/standard/generics/index.md)   

