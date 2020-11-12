---
title: com expressão-referência C#
description: Saiba mais sobre uma expressão with que executa mutação não destrutiva de registros C#
ms.date: 11/12/2020
f1_keywords:
- with_CSharpKeyword
helpviewer_keywords:
- with expression [C#]
- with operator [C#]
ms.openlocfilehash: 8412dfe8663703d3b201fe98b5f4752da1b344cf
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94556706"
---
# <a name="with-expression-c-reference"></a><span data-ttu-id="f40aa-103">expressão with (referência C#)</span><span class="sxs-lookup"><span data-stu-id="f40aa-103">with expression (C# reference)</span></span>

<span data-ttu-id="f40aa-104">Disponível em C# 9,0 e posterior, uma `with` expressão produz uma cópia de seu operando de [registro](../../whats-new/csharp-9.md#record-types) com as propriedades e os campos especificados modificados:</span><span class="sxs-lookup"><span data-stu-id="f40aa-104">Available in C# 9.0 and later, a `with` expression produces a copy of its [record](../../whats-new/csharp-9.md#record-types) operand with the specified properties and fields modified:</span></span>

:::code language="csharp" source="snippets/with-expression/BasicExample.cs" :::

<span data-ttu-id="f40aa-105">Como mostra o exemplo anterior, você usa a sintaxe do [inicializador de objeto](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) para especificar quais membros modificar e seus novos valores.</span><span class="sxs-lookup"><span data-stu-id="f40aa-105">As the preceding example shows, you use [object initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) syntax to specify what members to modify and their new values.</span></span> <span data-ttu-id="f40aa-106">Em uma `with` expressão, um operando à esquerda deve ser de um tipo de registro.</span><span class="sxs-lookup"><span data-stu-id="f40aa-106">In a `with` expression, a left-hand operand must be of a record type.</span></span>

<span data-ttu-id="f40aa-107">O resultado de uma `with` expressão tem o mesmo tipo de tempo de execução que o operando da expressão, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f40aa-107">The result of a `with` expression has the same runtime type as the expression's operand, as the following example shows:</span></span>

:::code language="csharp" source="snippets/with-expression/InheritanceExample.cs" :::

<span data-ttu-id="f40aa-108">No caso de um membro de tipo de referência, somente a referência a uma instância é copiada quando um registro é copiado.</span><span class="sxs-lookup"><span data-stu-id="f40aa-108">In case of a reference-type member, only the reference to an instance is copied when a record is copied.</span></span> <span data-ttu-id="f40aa-109">A cópia e o registro original têm acesso à mesma instância de tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="f40aa-109">Both the copy and original record have access to the same reference-type instance.</span></span> <span data-ttu-id="f40aa-110">O exemplo a seguir demonstra esse comportamento:</span><span class="sxs-lookup"><span data-stu-id="f40aa-110">The following example demonstrates that behavior:</span></span>

:::code language="csharp" source="snippets/with-expression/ExampleWithReferenceType.cs" :::

<span data-ttu-id="f40aa-111">Qualquer tipo de registro tem o *Construtor de cópia*.</span><span class="sxs-lookup"><span data-stu-id="f40aa-111">Any record type has the *copy constructor*.</span></span> <span data-ttu-id="f40aa-112">Esse é um construtor com um único parâmetro do tipo de registro que o contém.</span><span class="sxs-lookup"><span data-stu-id="f40aa-112">That is a constructor with a single parameter of the containing record type.</span></span> <span data-ttu-id="f40aa-113">Ele copia o estado de seu argumento para uma nova instância de registro.</span><span class="sxs-lookup"><span data-stu-id="f40aa-113">It copies the state of its argument to a new record instance.</span></span> <span data-ttu-id="f40aa-114">Na avaliação de uma `with` expressão, o construtor de cópia é chamado para instanciar uma nova instância de registro com base em um registro original.</span><span class="sxs-lookup"><span data-stu-id="f40aa-114">At evaluation of a `with` expression, the copy constructor gets called to instantiate a new record instance based on an original record.</span></span> <span data-ttu-id="f40aa-115">Depois disso, a nova instância é atualizada de acordo com as modificações especificadas.</span><span class="sxs-lookup"><span data-stu-id="f40aa-115">After that, the new instance gets updated according to the specified modifications.</span></span> <span data-ttu-id="f40aa-116">Por padrão, o construtor de cópia é implícito, ou seja, gerado pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="f40aa-116">By default, the copy constructor is implicit, that is, compiler-generated.</span></span> <span data-ttu-id="f40aa-117">Se você precisar personalizar a semântica de cópia de registro, declare explicitamente um construtor de cópia com o comportamento desejado.</span><span class="sxs-lookup"><span data-stu-id="f40aa-117">If you need to customize the record copy semantics, explicitly declare a copy constructor with the desired behavior.</span></span> <span data-ttu-id="f40aa-118">O exemplo a seguir atualiza o exemplo anterior com um construtor de cópia explícito.</span><span class="sxs-lookup"><span data-stu-id="f40aa-118">The following example updates the preceding example with an explicit copy constructor.</span></span> <span data-ttu-id="f40aa-119">O novo comportamento de cópia é copiar itens de lista em vez de uma referência de lista quando um registro é copiado:</span><span class="sxs-lookup"><span data-stu-id="f40aa-119">The new copy behavior is to copy list items instead of a list reference when a record is copied:</span></span>

:::code language="csharp" source="snippets/with-expression/UserDefinedCopyConstructor.cs" :::

## <a name="c-language-specification"></a><span data-ttu-id="f40aa-120">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f40aa-120">C# language specification</span></span>

<span data-ttu-id="f40aa-121">Para obter mais informações, consulte as seções a seguir da [proposta de recurso de registros observação](~/_csharplang/proposals/csharp-9.0/records.md):</span><span class="sxs-lookup"><span data-stu-id="f40aa-121">For more information, see the following sections of the [records feature proposal note](~/_csharplang/proposals/csharp-9.0/records.md):</span></span>

- [<span data-ttu-id="f40aa-122">`with` expressão</span><span class="sxs-lookup"><span data-stu-id="f40aa-122">`with` expression</span></span>](~/_csharplang/proposals/csharp-9.0/records.md#with-expression)
- [<span data-ttu-id="f40aa-123">Copiar e clonar Membros</span><span class="sxs-lookup"><span data-stu-id="f40aa-123">Copy and Clone members</span></span>](~/_csharplang/proposals/csharp-9.0/records.md#copy-and-clone-members)

## <a name="see-also"></a><span data-ttu-id="f40aa-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="f40aa-124">See also</span></span>

- [<span data-ttu-id="f40aa-125">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="f40aa-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f40aa-126">Operadores e expressões C#</span><span class="sxs-lookup"><span data-stu-id="f40aa-126">C# operators and expressions</span></span>](index.md)
