---
title: expressões de valor padrão (guia de programação em C#)
description: As expressões de valor padrão produzem o valor padrão para qualquer tipo de referência ou tipo de valor
ms.date: 04/25/2018
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.openlocfilehash: 94866f22fb3ad921a834cffb16fe17e44cef5965
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44222286"
---
# <a name="default-value-expressions-c-programming-guide"></a><span data-ttu-id="07f4b-103">Expressões de valor padrão (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="07f4b-103">default value expressions (C# programming guide)</span></span>

<span data-ttu-id="07f4b-104">Uma expressão de valor padrão `default(T)` produz o valor padrão de um tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="07f4b-104">A default value expression `default(T)` produces the default value of a type `T`.</span></span> <span data-ttu-id="07f4b-105">A tabela a seguir mostra os valores que são produzidos para vários tipos:</span><span class="sxs-lookup"><span data-stu-id="07f4b-105">The following table shows which values are produced for various types:</span></span>

|<span data-ttu-id="07f4b-106">Tipo</span><span class="sxs-lookup"><span data-stu-id="07f4b-106">Type</span></span>|<span data-ttu-id="07f4b-107">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="07f4b-107">Default value</span></span>|
|---------|---------|
|<span data-ttu-id="07f4b-108">Qualquer tipo de referência</span><span class="sxs-lookup"><span data-stu-id="07f4b-108">Any reference type</span></span>|`null`|
|<span data-ttu-id="07f4b-109">Tipo de valor numérico</span><span class="sxs-lookup"><span data-stu-id="07f4b-109">Numeric value type</span></span>|<span data-ttu-id="07f4b-110">Zero</span><span class="sxs-lookup"><span data-stu-id="07f4b-110">Zero</span></span>|
|[<span data-ttu-id="07f4b-111">bool</span><span class="sxs-lookup"><span data-stu-id="07f4b-111">bool</span></span>](../../language-reference/keywords/bool.md)|`false`|
|[<span data-ttu-id="07f4b-112">char</span><span class="sxs-lookup"><span data-stu-id="07f4b-112">char</span></span>](../../language-reference/keywords/char.md)|`'\0'`|
|[<span data-ttu-id="07f4b-113">enum</span><span class="sxs-lookup"><span data-stu-id="07f4b-113">enum</span></span>](../../language-reference/keywords/enum.md)|<span data-ttu-id="07f4b-114">O valor é produzido pela expressão `(E)0`, em que `E` é o identificador de enumeração.</span><span class="sxs-lookup"><span data-stu-id="07f4b-114">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="07f4b-115">struct</span><span class="sxs-lookup"><span data-stu-id="07f4b-115">struct</span></span>](../../language-reference/keywords/struct.md)|<span data-ttu-id="07f4b-116">O valor produzido pela configuração de todos os campos de tipo de valor para seus valores padrão e de todos os campos de tipo de referência para `null`.</span><span class="sxs-lookup"><span data-stu-id="07f4b-116">The value produced by setting all value type fields to their default value and all reference type fields to `null`.</span></span>|
|<span data-ttu-id="07f4b-117">Tipo que permite valor nulo</span><span class="sxs-lookup"><span data-stu-id="07f4b-117">Nullable type</span></span>|<span data-ttu-id="07f4b-118">Uma instância para a qual a propriedade <xref:System.Nullable%601.HasValue%2A> é `false` e a propriedade <xref:System.Nullable%601.Value%2A> não está definida.</span><span class="sxs-lookup"><span data-stu-id="07f4b-118">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span>|

<span data-ttu-id="07f4b-119">As expressões de valores padrão são úteis principalmente em classes e métodos genéricos.</span><span class="sxs-lookup"><span data-stu-id="07f4b-119">Default value expressions are particularly useful in generic classes and methods.</span></span> <span data-ttu-id="07f4b-120">Um problema que surge ao usar genéricos é como atribuir um valor padrão de um tipo parametrizado `T` quando você ainda não sabe o seguinte:</span><span class="sxs-lookup"><span data-stu-id="07f4b-120">One issue that arises using generics is how to assign a default value of a parameterized type `T` when you don't know the following in advance:</span></span>

- <span data-ttu-id="07f4b-121">Se `T` é um tipo de referência ou um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="07f4b-121">Whether `T` is a reference type or a value type.</span></span>
- <span data-ttu-id="07f4b-122">Se `T` é um tipo de valor, seja um valor numérico ou um struct.</span><span class="sxs-lookup"><span data-stu-id="07f4b-122">If `T` is a value type, whether it's a numeric value or a struct.</span></span>

 <span data-ttu-id="07f4b-123">Dada uma variável `t` de um tipo parametrizado `T`, a instrução `t = null` só será válida se `T` for um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="07f4b-123">Given a variable `t` of a parameterized type `T`, the statement `t = null` is only valid if `T` is a reference type.</span></span> <span data-ttu-id="07f4b-124">A atribuição `t = 0` funciona apenas para tipos de valor numérico, mas não para structs.</span><span class="sxs-lookup"><span data-stu-id="07f4b-124">The assignment `t = 0` only works for numeric value types but not for structs.</span></span> <span data-ttu-id="07f4b-125">Para resolver isso, use uma expressão de valor padrão:</span><span class="sxs-lookup"><span data-stu-id="07f4b-125">To solve that, use a default value expression:</span></span>

```csharp
T t = default(T);
```

<span data-ttu-id="07f4b-126">A expressão `default(T)` não é limitada a classes e métodos genéricos.</span><span class="sxs-lookup"><span data-stu-id="07f4b-126">The `default(T)` expression is not limited to generic classes and methods.</span></span> <span data-ttu-id="07f4b-127">As expressões de valor padrão podem ser usadas com qualquer tipo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="07f4b-127">Default value expressions can be used with any managed type.</span></span> <span data-ttu-id="07f4b-128">Todas estas expressões são válidas:</span><span class="sxs-lookup"><span data-stu-id="07f4b-128">Any of these expressions are valid:</span></span>

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 <span data-ttu-id="07f4b-129">O exemplo da classe `GenericList<T>` a seguir mostra como usar o operador `default(T)` em uma classe genérica.</span><span class="sxs-lookup"><span data-stu-id="07f4b-129">The following example from the `GenericList<T>` class shows how to use the `default(T)` operator in a generic class.</span></span> <span data-ttu-id="07f4b-130">Para obter mais informações, consulte [Introdução aos Genéricos](../generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="07f4b-130">For more information, see [Introduction to Generics](../generics/introduction-to-generics.md).</span></span>

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a><span data-ttu-id="07f4b-131">Inferência de tipo e literal padrão</span><span class="sxs-lookup"><span data-stu-id="07f4b-131">default literal and type inference</span></span>

<span data-ttu-id="07f4b-132">A partir do C# 7.1, o literal `default` pode ser usado para expressões de valor padrão quando o compilador pode inferir o tipo da expressão.</span><span class="sxs-lookup"><span data-stu-id="07f4b-132">Beginning with C# 7.1, the `default` literal can be used for default value expressions when the compiler can infer the type of the expression.</span></span> <span data-ttu-id="07f4b-133">O literal `default` produz o mesmo valor que o equivalente `default(T)`, em que `T` é o tipo inferido.</span><span class="sxs-lookup"><span data-stu-id="07f4b-133">The `default` literal produces the same value as the equivalent `default(T)` where `T` is the inferred type.</span></span> <span data-ttu-id="07f4b-134">Isso pode tornar código mais conciso, reduzindo a redundância de declarar um tipo mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="07f4b-134">This can make code more concise by reducing the redundancy of declaring a type more than once.</span></span> <span data-ttu-id="07f4b-135">O literal `default` pode ser usado em todos os locais a seguir:</span><span class="sxs-lookup"><span data-stu-id="07f4b-135">The `default` literal can be used in any of the following locations:</span></span>

- <span data-ttu-id="07f4b-136">inicializador de variável</span><span class="sxs-lookup"><span data-stu-id="07f4b-136">variable initializer</span></span>
- <span data-ttu-id="07f4b-137">atribuição de variável</span><span class="sxs-lookup"><span data-stu-id="07f4b-137">variable assignment</span></span>
- <span data-ttu-id="07f4b-138">declarando o valor padrão para um parâmetro opcional</span><span class="sxs-lookup"><span data-stu-id="07f4b-138">declaring the default value for an optional parameter</span></span>
- <span data-ttu-id="07f4b-139">fornecendo o valor para um argumento de chamada de método</span><span class="sxs-lookup"><span data-stu-id="07f4b-139">providing the value for a method call argument</span></span>
- <span data-ttu-id="07f4b-140">instrução de retorno (ou expressão em um membro no corpo da expressão)</span><span class="sxs-lookup"><span data-stu-id="07f4b-140">return statement (or expression in an expression bodied member)</span></span>

<span data-ttu-id="07f4b-141">O exemplo a seguir mostra vários tipos de uso do literal `default` em uma expressão de valor padrão:</span><span class="sxs-lookup"><span data-stu-id="07f4b-141">The following example shows many usages of the `default` literal in a default value expression:</span></span>

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a><span data-ttu-id="07f4b-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07f4b-142">See Also</span></span>

- <xref:System.Collections.Generic>  
- [<span data-ttu-id="07f4b-143">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="07f4b-143">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="07f4b-144">Genéricos (guia de programação em C#)</span><span class="sxs-lookup"><span data-stu-id="07f4b-144">Generics (C# Programming Guide)</span></span>](../generics/index.md)  
- [<span data-ttu-id="07f4b-145">Métodos genéricos</span><span class="sxs-lookup"><span data-stu-id="07f4b-145">Generic Methods</span></span>](../generics/generic-methods.md)  
- [<span data-ttu-id="07f4b-146">Genéricos no .NET</span><span class="sxs-lookup"><span data-stu-id="07f4b-146">Generics in .NET</span></span>](~/docs/standard/generics/index.md)  
- [<span data-ttu-id="07f4b-147">Tabela de valores padrão</span><span class="sxs-lookup"><span data-stu-id="07f4b-147">Default values table</span></span>](../../language-reference/keywords/default-values-table.md)
