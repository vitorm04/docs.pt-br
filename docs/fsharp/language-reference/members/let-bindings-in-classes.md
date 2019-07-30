---
title: Associações let em classes
description: Saiba como definir campos privados e funções particulares para F# classes usando associações ' Let ' na definição de classe.
ms.date: 05/16/2016
ms.openlocfilehash: 0086d3a91f85395c2bd0555f978c5d951c363357
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627475"
---
# <a name="let-bindings-in-classes"></a><span data-ttu-id="faed8-103">Associações let em classes</span><span class="sxs-lookup"><span data-stu-id="faed8-103">let Bindings in Classes</span></span>

<span data-ttu-id="faed8-104">Você pode definir campos privados e funções particulares para F# classes usando `let` associações na definição de classe.</span><span class="sxs-lookup"><span data-stu-id="faed8-104">You can define private fields and private functions for F# classes by using `let` bindings in the class definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="faed8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="faed8-105">Syntax</span></span>

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a><span data-ttu-id="faed8-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="faed8-106">Remarks</span></span>

<span data-ttu-id="faed8-107">A sintaxe anterior aparece depois do cabeçalho da classe e das declarações de herança, mas antes de qualquer definição de membro.</span><span class="sxs-lookup"><span data-stu-id="faed8-107">The previous syntax appears after the class heading and inheritance declarations but before any member definitions.</span></span> <span data-ttu-id="faed8-108">A sintaxe é como a de `let` associações fora de classes, mas os nomes definidos em uma classe têm um escopo limitado à classe.</span><span class="sxs-lookup"><span data-stu-id="faed8-108">The syntax is like that of `let` bindings outside of classes, but the names defined in a class have a scope that is limited to the class.</span></span> <span data-ttu-id="faed8-109">Uma `let` associação cria um campo ou função particular; para expor dados ou funções publicamente, declare uma propriedade ou um método de membro.</span><span class="sxs-lookup"><span data-stu-id="faed8-109">A `let` binding creates a private field or function; to expose data or functions publicly, declare a property or a member method.</span></span>

<span data-ttu-id="faed8-110">Uma `let` associação que não é estática é chamada de associação `let` de instância.</span><span class="sxs-lookup"><span data-stu-id="faed8-110">A `let` binding that is not static is called an instance `let` binding.</span></span> <span data-ttu-id="faed8-111">As `let` associações de instância são executadas quando objetos são criados.</span><span class="sxs-lookup"><span data-stu-id="faed8-111">Instance `let` bindings execute when objects are created.</span></span> <span data-ttu-id="faed8-112">As `let` associações estáticas fazem parte do inicializador estático para a classe, que tem a garantia de executar antes de o tipo ser usado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="faed8-112">Static `let` bindings are part of the static initializer for the class, which is guaranteed to execute before the type is first used.</span></span>

<span data-ttu-id="faed8-113">O código dentro das `let` associações de instância pode usar os parâmetros do construtor primário.</span><span class="sxs-lookup"><span data-stu-id="faed8-113">The code within instance `let` bindings can use the primary constructor's parameters.</span></span>

<span data-ttu-id="faed8-114">Os modificadores de atributos e de acessibilidade não `let` são permitidos em associações em classes.</span><span class="sxs-lookup"><span data-stu-id="faed8-114">Attributes and accessibility modifiers are not permitted on `let` bindings in classes.</span></span>

<span data-ttu-id="faed8-115">Os exemplos de código a seguir ilustram `let` vários tipos de associações em classes.</span><span class="sxs-lookup"><span data-stu-id="faed8-115">The following code examples illustrate several types of `let` bindings in classes.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

<span data-ttu-id="faed8-116">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="faed8-116">The output is as follows.</span></span>

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a><span data-ttu-id="faed8-117">Maneiras alternativas de criar campos</span><span class="sxs-lookup"><span data-stu-id="faed8-117">Alternative Ways to Create Fields</span></span>

<span data-ttu-id="faed8-118">Você também pode usar a `val` palavra-chave para criar um campo privado.</span><span class="sxs-lookup"><span data-stu-id="faed8-118">You can also use the `val` keyword to create a private field.</span></span> <span data-ttu-id="faed8-119">Ao usar a `val` palavra-chave, o campo não recebe um valor quando o objeto é criado, mas, em vez disso, é inicializado com um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="faed8-119">When using the `val` keyword, the field is not given a value when the object is created, but instead is initialized with a default value.</span></span> <span data-ttu-id="faed8-120">Para obter mais informações, [consulte campos explícitos: A palavra-](explicit-fields-the-val-keyword.md)chave Val.</span><span class="sxs-lookup"><span data-stu-id="faed8-120">For more information, see [Explicit Fields: The val Keyword](explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="faed8-121">Você também pode definir campos privados em uma classe usando uma definição de membro e adicionando a palavra `private` -chave à definição.</span><span class="sxs-lookup"><span data-stu-id="faed8-121">You can also define private fields in a class by using a member definition and adding the keyword `private` to the definition.</span></span> <span data-ttu-id="faed8-122">Isso pode ser útil se você espera alterar a acessibilidade de um membro sem reescrever seu código.</span><span class="sxs-lookup"><span data-stu-id="faed8-122">This can be useful if you expect to change the accessibility of a member without rewriting your code.</span></span> <span data-ttu-id="faed8-123">Para saber mais, veja [Controle de acesso](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="faed8-123">For more information, see [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="faed8-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="faed8-124">See also</span></span>

- [<span data-ttu-id="faed8-125">Membros</span><span class="sxs-lookup"><span data-stu-id="faed8-125">Members</span></span>](index.md)
- [<span data-ttu-id="faed8-126">`do`Associações em Classes</span><span class="sxs-lookup"><span data-stu-id="faed8-126">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)
- [<span data-ttu-id="faed8-127">`let`Associações</span><span class="sxs-lookup"><span data-stu-id="faed8-127">`let` Bindings</span></span>](../functions/let-bindings.md)
