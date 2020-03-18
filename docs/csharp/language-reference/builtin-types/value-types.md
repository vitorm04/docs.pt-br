---
title: Tipos de valor - referência C#
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 406e5b8bbe0802146a65bb4b9a053e753a7827ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399577"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="19286-102">Tipos de valor (referência C#)</span><span class="sxs-lookup"><span data-stu-id="19286-102">Value types (C# reference)</span></span>

<span data-ttu-id="19286-103">*Tipos de valor* e [tipos de referência](../keywords/reference-types.md) são as duas principais categorias dos tipos C#.</span><span class="sxs-lookup"><span data-stu-id="19286-103">*Value types* and [reference types](../keywords/reference-types.md) are the two main categories of C# types.</span></span> <span data-ttu-id="19286-104">Uma variável de um tipo de valor contém uma instância do tipo.</span><span class="sxs-lookup"><span data-stu-id="19286-104">A variable of a value type contains an instance of the type.</span></span> <span data-ttu-id="19286-105">Isso difere de uma variável de um tipo de referência, que contém uma referência a uma instância do tipo.</span><span class="sxs-lookup"><span data-stu-id="19286-105">This differs from a variable of a reference type, which contains a reference to an instance of the type.</span></span> <span data-ttu-id="19286-106">Por padrão, na [atribuição,](../operators/assignment-operator.md)passando um argumento para um método e retornando um resultado do método, os valores variáveis são copiados.</span><span class="sxs-lookup"><span data-stu-id="19286-106">By default, on [assignment](../operators/assignment-operator.md), passing an argument to a method, and returning a method result, variable values are copied.</span></span> <span data-ttu-id="19286-107">No caso de variáveis de tipo de valor, as instâncias de tipo correspondentes são copiadas.</span><span class="sxs-lookup"><span data-stu-id="19286-107">In the case of value-type variables, the corresponding type instances are copied.</span></span> <span data-ttu-id="19286-108">O exemplo a seguir demonstra esse comportamento:</span><span class="sxs-lookup"><span data-stu-id="19286-108">The following example demonstrates that behavior:</span></span>

[!code-csharp[copy of values](snippets/ValueTypes.cs#ValueTypeCopied)]

<span data-ttu-id="19286-109">Como o exemplo anterior mostra, as operações em uma variável de tipo de valor afetam apenas essa instância do tipo de valor, armazenada na variável.</span><span class="sxs-lookup"><span data-stu-id="19286-109">As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.</span></span>

<span data-ttu-id="19286-110">Se um tipo de valor contiver um membro de dados de um tipo de referência, apenas a referência à instância do tipo de referência será copiada quando uma instância de tipo de valor for copiada.</span><span class="sxs-lookup"><span data-stu-id="19286-110">If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied.</span></span> <span data-ttu-id="19286-111">Tanto a cópia quanto a instância original do tipo de valor têm acesso à mesma instância do tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="19286-111">Both the copy and original value-type instance have access to the same reference-type instance.</span></span> <span data-ttu-id="19286-112">O exemplo a seguir demonstra esse comportamento:</span><span class="sxs-lookup"><span data-stu-id="19286-112">The following example demonstrates that behavior:</span></span>

[!code-csharp[shallow copy](snippets/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> <span data-ttu-id="19286-113">Para tornar seu código menos propenso a erros e mais robusto, defina e use tipos de valor imutáveis.</span><span class="sxs-lookup"><span data-stu-id="19286-113">To make your code less error-prone and more robust, define and use immutable value types.</span></span> <span data-ttu-id="19286-114">Este artigo usa tipos de valor mutáveis apenas para fins de demonstração.</span><span class="sxs-lookup"><span data-stu-id="19286-114">This article uses mutable value types only for demonstration purposes.</span></span>

## <a name="kinds-of-value-types"></a><span data-ttu-id="19286-115">Tipos de tipos de valor</span><span class="sxs-lookup"><span data-stu-id="19286-115">Kinds of value types</span></span>

<span data-ttu-id="19286-116">Um tipo de valor pode ser um dos dois tipos a seguir:</span><span class="sxs-lookup"><span data-stu-id="19286-116">A value type can be one of the two following kinds:</span></span>

- <span data-ttu-id="19286-117">um [tipo de estrutura,](struct.md)que encapsula dados e funcionalidades relacionadas</span><span class="sxs-lookup"><span data-stu-id="19286-117">a [structure type](struct.md), which encapsulates data and related functionality</span></span>
- <span data-ttu-id="19286-118">um [tipo de enumeração,](enum.md)que é definido por um conjunto de constantes nomeadas e representa uma escolha ou uma combinação de escolhas</span><span class="sxs-lookup"><span data-stu-id="19286-118">an [enumeration type](enum.md), which is defined by a set of named constants and represents a choice or a combination of choices</span></span>

<span data-ttu-id="19286-119">Um [tipo](nullable-value-types.md) `T?` de valor anulado representa todos os `T` valores do seu tipo de valor subjacente e um valor [nulo](../keywords/null.md) adicional.</span><span class="sxs-lookup"><span data-stu-id="19286-119">A [nullable value type](nullable-value-types.md) `T?` represents all values of its underlying value type `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="19286-120">Você não `null` pode atribuir a uma variável de um tipo de valor, a menos que seja um tipo de valor anulado.</span><span class="sxs-lookup"><span data-stu-id="19286-120">You cannot assign `null` to a variable of a value type, unless it's a nullable value type.</span></span>

## <a name="built-in-value-types"></a><span data-ttu-id="19286-121">Tipos de valor incorporado</span><span class="sxs-lookup"><span data-stu-id="19286-121">Built-in value types</span></span>

<span data-ttu-id="19286-122">C# fornece os seguintes tipos de valor embutidos, também conhecidos como *tipos simples:*</span><span class="sxs-lookup"><span data-stu-id="19286-122">C# provides the following built-in value types, also known as *simple types*:</span></span>

- [<span data-ttu-id="19286-123">Tipos numéricos integrais</span><span class="sxs-lookup"><span data-stu-id="19286-123">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="19286-124">Tipos numéricos de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="19286-124">Floating-point numeric types</span></span>](floating-point-numeric-types.md)
- <span data-ttu-id="19286-125">[bool](bool.md) que representa um valor booleano</span><span class="sxs-lookup"><span data-stu-id="19286-125">[bool](bool.md) that represents a Boolean value</span></span>
- <span data-ttu-id="19286-126">[char](char.md) que representa um caractere Unicode UTF-16</span><span class="sxs-lookup"><span data-stu-id="19286-126">[char](char.md) that represents a Unicode UTF-16 character</span></span>

<span data-ttu-id="19286-127">Todos os tipos simples são tipos de estrutura e diferem de outros tipos de estrutura, pois permitem certas operações adicionais:</span><span class="sxs-lookup"><span data-stu-id="19286-127">All simple types are structure types and differ from other structure types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="19286-128">Você pode usar literais para fornecer um valor de um tipo simples.</span><span class="sxs-lookup"><span data-stu-id="19286-128">You can use literals to provide a value of a simple type.</span></span> <span data-ttu-id="19286-129">Por exemplo, `'A'` é um literal do tipo `char` e `2001` é um literal do tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="19286-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="19286-130">Você pode declarar constantes dos tipos simples com a palavra-chave [const](../keywords/const.md).</span><span class="sxs-lookup"><span data-stu-id="19286-130">You can declare constants of the simple types with the [const](../keywords/const.md) keyword.</span></span> <span data-ttu-id="19286-131">Não é possível ter constantes de outros tipos de estrutura.</span><span class="sxs-lookup"><span data-stu-id="19286-131">It's not possible to have constants of other structure types.</span></span>

- <span data-ttu-id="19286-132">Expressões constantes, cujos operands são todas constantes dos tipos simples, são avaliadas no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="19286-132">Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.</span></span>

<span data-ttu-id="19286-133">Começando com C# 7.0, C# suporta [tuplas de valor](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="19286-133">Beginning with C# 7.0, C# supports [value tuples](../../tuples.md).</span></span> <span data-ttu-id="19286-134">Uma tuple de valor é um tipo de valor, mas não um tipo simples.</span><span class="sxs-lookup"><span data-stu-id="19286-134">A value tuple is a value type, but not a simple type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="19286-135">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="19286-135">C# language specification</span></span>

<span data-ttu-id="19286-136">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="19286-136">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="19286-137">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="19286-137">Value types</span></span>](~/_csharplang/spec/types.md#value-types)
- [<span data-ttu-id="19286-138">Tipos simples</span><span class="sxs-lookup"><span data-stu-id="19286-138">Simple types</span></span>](~/_csharplang/spec/types.md#simple-types)
- [<span data-ttu-id="19286-139">Variáveis</span><span class="sxs-lookup"><span data-stu-id="19286-139">Variables</span></span>](~/_csharplang/spec/variables.md)

## <a name="see-also"></a><span data-ttu-id="19286-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="19286-140">See also</span></span>

- [<span data-ttu-id="19286-141">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="19286-141">C# reference</span></span>](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [<span data-ttu-id="19286-142">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="19286-142">Reference types</span></span>](../keywords/reference-types.md)
