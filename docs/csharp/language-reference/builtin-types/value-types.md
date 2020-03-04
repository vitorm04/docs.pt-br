---
title: Tipos de valor C# -referência
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: a2b9dce3b0ca5e66cfc0fbdbbf8f341abca0b636
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239723"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="c8224-102">Tipos de valorC# (referência)</span><span class="sxs-lookup"><span data-stu-id="c8224-102">Value types (C# reference)</span></span>

<span data-ttu-id="c8224-103">*Tipos de valor* e [tipos de referência](../keywords/reference-types.md) são as duas categorias C# principais de tipos.</span><span class="sxs-lookup"><span data-stu-id="c8224-103">*Value types* and [reference types](../keywords/reference-types.md) are the two main categories of C# types.</span></span> <span data-ttu-id="c8224-104">Uma variável de um tipo Value contém uma instância do tipo.</span><span class="sxs-lookup"><span data-stu-id="c8224-104">A variable of a value type contains an instance of the type.</span></span> <span data-ttu-id="c8224-105">Isso é diferente de uma variável de um tipo de referência, que contém uma referência a uma instância do tipo.</span><span class="sxs-lookup"><span data-stu-id="c8224-105">This differs from a variable of a reference type, which contains a reference to an instance of the type.</span></span> <span data-ttu-id="c8224-106">Por padrão, na [atribuição](../operators/assignment-operator.md), passando um argumento para um método e retornando um resultado de método, valores de variáveis são copiados.</span><span class="sxs-lookup"><span data-stu-id="c8224-106">By default, on [assignment](../operators/assignment-operator.md), passing an argument to a method, and returning a method result, variable values are copied.</span></span> <span data-ttu-id="c8224-107">No caso de variáveis de tipo de valor, as instâncias de tipo correspondentes são copiadas.</span><span class="sxs-lookup"><span data-stu-id="c8224-107">In the case of value-type variables, the corresponding type instances are copied.</span></span> <span data-ttu-id="c8224-108">O exemplo a seguir demonstra esse comportamento:</span><span class="sxs-lookup"><span data-stu-id="c8224-108">The following example demonstrates that behavior:</span></span>

[!code-csharp[copy of values](~/samples/snippets/csharp/language-reference/builtin-types/ValueTypes.cs#ValueTypeCopied)]

<span data-ttu-id="c8224-109">Como mostra o exemplo anterior, as operações em uma variável de tipo de valor afetam apenas essa instância do tipo de valor, armazenado na variável.</span><span class="sxs-lookup"><span data-stu-id="c8224-109">As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.</span></span>

<span data-ttu-id="c8224-110">Se um tipo de valor contiver um membro de dados de um tipo de referência, somente a referência à instância do tipo de referência será copiada quando uma instância de tipo de valor for copiada.</span><span class="sxs-lookup"><span data-stu-id="c8224-110">If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied.</span></span> <span data-ttu-id="c8224-111">A instância de tipo de valor de cópia e original tem acesso à mesma instância de tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="c8224-111">Both the copy and original value-type instance have access to the same reference-type instance.</span></span> <span data-ttu-id="c8224-112">O exemplo a seguir demonstra esse comportamento:</span><span class="sxs-lookup"><span data-stu-id="c8224-112">The following example demonstrates that behavior:</span></span>

[!code-csharp[shallow copy](~/samples/snippets/csharp/language-reference/builtin-types/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> <span data-ttu-id="c8224-113">Para tornar seu código menos propenso a erros e mais robusto, defina e use tipos de valor imutável.</span><span class="sxs-lookup"><span data-stu-id="c8224-113">To make your code less error-prone and more robust, define and use immutable value types.</span></span> <span data-ttu-id="c8224-114">Este artigo usa tipos de valores mutáveis somente para fins de demonstração.</span><span class="sxs-lookup"><span data-stu-id="c8224-114">This article uses mutable value types only for demonstration purposes.</span></span>

## <a name="kinds-of-value-types"></a><span data-ttu-id="c8224-115">Tipos de tipos de valor</span><span class="sxs-lookup"><span data-stu-id="c8224-115">Kinds of value types</span></span>

<span data-ttu-id="c8224-116">Um tipo de valor pode ser um dos dois tipos a seguir:</span><span class="sxs-lookup"><span data-stu-id="c8224-116">A value type can be one of the two following kinds:</span></span>

- <span data-ttu-id="c8224-117">um [tipo de estrutura](struct.md), que encapsula dados e funcionalidade relacionada</span><span class="sxs-lookup"><span data-stu-id="c8224-117">a [structure type](struct.md), which encapsulates data and related functionality</span></span>
- <span data-ttu-id="c8224-118">um [tipo de enumeração](enum.md), que é definido por um conjunto de constantes nomeadas e representa uma opção ou uma combinação de opções</span><span class="sxs-lookup"><span data-stu-id="c8224-118">an [enumeration type](enum.md), which is defined by a set of named constants and represents a choice or a combination of choices</span></span>

<span data-ttu-id="c8224-119">Um [tipo de valor anulável](nullable-value-types.md) `T?` representa todos os valores de seu tipo de valor subjacente `T` e um valor [nulo](../keywords/null.md) adicional.</span><span class="sxs-lookup"><span data-stu-id="c8224-119">A [nullable value type](nullable-value-types.md) `T?` represents all values of its underlying value type `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="c8224-120">Você não pode atribuir `null` a uma variável de um tipo de valor, a menos que seja um tipo de valor anulável.</span><span class="sxs-lookup"><span data-stu-id="c8224-120">You cannot assign `null` to a variable of a value type, unless it's a nullable value type.</span></span>

## <a name="built-in-value-types"></a><span data-ttu-id="c8224-121">Tipos de valores internos</span><span class="sxs-lookup"><span data-stu-id="c8224-121">Built-in value types</span></span>

<span data-ttu-id="c8224-122">C#fornece os seguintes tipos de valor internos, também conhecidos como *tipos simples*:</span><span class="sxs-lookup"><span data-stu-id="c8224-122">C# provides the following built-in value types, also known as *simple types*:</span></span>

- [<span data-ttu-id="c8224-123">Tipos numéricos inteiros</span><span class="sxs-lookup"><span data-stu-id="c8224-123">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="c8224-124">Tipos numéricos de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="c8224-124">Floating-point numeric types</span></span>](floating-point-numeric-types.md)
- <span data-ttu-id="c8224-125">[bool](bool.md) que representa um valor booliano</span><span class="sxs-lookup"><span data-stu-id="c8224-125">[bool](bool.md) that represents a Boolean value</span></span>
- <span data-ttu-id="c8224-126">[Char](char.md) que representa um caractere Unicode UTF-16</span><span class="sxs-lookup"><span data-stu-id="c8224-126">[char](char.md) that represents a Unicode UTF-16 character</span></span>

<span data-ttu-id="c8224-127">Todos os tipos simples são tipos de estrutura e diferem de outros tipos de estrutura, pois permitem determinadas operações adicionais:</span><span class="sxs-lookup"><span data-stu-id="c8224-127">All simple types are structure types and differ from other structure types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="c8224-128">Você pode usar literais para fornecer um valor de um tipo simples.</span><span class="sxs-lookup"><span data-stu-id="c8224-128">You can use literals to provide a value of a simple type.</span></span> <span data-ttu-id="c8224-129">Por exemplo, `'A'` é um literal do tipo `char` e `2001` é um literal do tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="c8224-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="c8224-130">Você pode declarar constantes dos tipos simples com a palavra-chave [const](../keywords/const.md).</span><span class="sxs-lookup"><span data-stu-id="c8224-130">You can declare constants of the simple types with the [const](../keywords/const.md) keyword.</span></span> <span data-ttu-id="c8224-131">Não é possível ter constantes de outros tipos de estrutura.</span><span class="sxs-lookup"><span data-stu-id="c8224-131">It's not possible to have constants of other structure types.</span></span>

- <span data-ttu-id="c8224-132">Expressões constantes, cujos operandos são todas constantes dos tipos simples, são avaliadas no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="c8224-132">Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.</span></span>

<span data-ttu-id="c8224-133">A partir C# do 7,0 C# , o dá suporte a [tuplas de valor](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="c8224-133">Beginning with C# 7.0, C# supports [value tuples](../../tuples.md).</span></span> <span data-ttu-id="c8224-134">Uma tupla de valor é um tipo de valor, mas não um tipo simples.</span><span class="sxs-lookup"><span data-stu-id="c8224-134">A value tuple is a value type, but not a simple type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c8224-135">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="c8224-135">C# language specification</span></span>

<span data-ttu-id="c8224-136">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="c8224-136">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="c8224-137">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="c8224-137">Value types</span></span>](~/_csharplang/spec/types.md#value-types)
- [<span data-ttu-id="c8224-138">Tipos simples</span><span class="sxs-lookup"><span data-stu-id="c8224-138">Simple types</span></span>](~/_csharplang/spec/types.md#simple-types)
- [<span data-ttu-id="c8224-139">Variáveis</span><span class="sxs-lookup"><span data-stu-id="c8224-139">Variables</span></span>](~/_csharplang/spec/variables.md)

## <a name="see-also"></a><span data-ttu-id="c8224-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="c8224-140">See also</span></span>

- [<span data-ttu-id="c8224-141">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="c8224-141">C# reference</span></span>](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [<span data-ttu-id="c8224-142">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="c8224-142">Reference types</span></span>](../keywords/reference-types.md)
