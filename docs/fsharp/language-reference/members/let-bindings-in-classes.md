---
title: "Associações let em classes (F#)"
description: "Saiba como definir campos particulares e funções privadas para classes de F # usando associações 'let' na definição de classe."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9d3710f5-68b1-4e4c-b02b-27fe018f20e8
ms.openlocfilehash: 1337cc0794e366e8c39745f5c45065362c9c38c9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="let-bindings-in-classes"></a><span data-ttu-id="72756-104">Associações let em classes</span><span class="sxs-lookup"><span data-stu-id="72756-104">let Bindings in Classes</span></span>

<span data-ttu-id="72756-105">Você pode definir funções privadas para classes de F # e campos particulares usando `let` associações na definição de classe.</span><span class="sxs-lookup"><span data-stu-id="72756-105">You can define private fields and private functions for F# classes by using `let` bindings in the class definition.</span></span>


## <a name="syntax"></a><span data-ttu-id="72756-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72756-106">Syntax</span></span>

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a><span data-ttu-id="72756-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="72756-107">Remarks</span></span>
<span data-ttu-id="72756-108">A sintaxe anterior é exibido após as declarações de título e herança de classe, mas antes de quaisquer definições de membro.</span><span class="sxs-lookup"><span data-stu-id="72756-108">The previous syntax appears after the class heading and inheritance declarations but before any member definitions.</span></span> <span data-ttu-id="72756-109">A sintaxe é semelhante de `let` associações fora de classes, mas os nomes definidos em uma classe têm um escopo limitado à classe.</span><span class="sxs-lookup"><span data-stu-id="72756-109">The syntax is like that of `let` bindings outside of classes, but the names defined in a class have a scope that is limited to the class.</span></span> <span data-ttu-id="72756-110">Um `let` associação cria um campo particular ou uma função; para expor dados ou funções publicamente, declarar uma propriedade ou um método de membro.</span><span class="sxs-lookup"><span data-stu-id="72756-110">A `let` binding creates a private field or function; to expose data or functions publicly, declare a property or a member method.</span></span>

<span data-ttu-id="72756-111">Um `let` que a associação não é estático é chamado de uma instância `let` associação.</span><span class="sxs-lookup"><span data-stu-id="72756-111">A `let` binding that is not static is called an instance `let` binding.</span></span> <span data-ttu-id="72756-112">Instância `let` associações executar quando objetos são criados.</span><span class="sxs-lookup"><span data-stu-id="72756-112">Instance `let` bindings execute when objects are created.</span></span> <span data-ttu-id="72756-113">Estático `let` associações fazem parte do inicializador estático da classe, que é garantido para executar antes que o tipo é usado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="72756-113">Static `let` bindings are part of the static initializer for the class, which is guaranteed to execute before the type is first used.</span></span>

<span data-ttu-id="72756-114">O código na instância `let` associações podem usar os parâmetros do construtor primário.</span><span class="sxs-lookup"><span data-stu-id="72756-114">The code within instance `let` bindings can use the primary constructor's parameters.</span></span>

<span data-ttu-id="72756-115">Atributos e modificadores de acessibilidade não são permitidos em `let` associações em classes.</span><span class="sxs-lookup"><span data-stu-id="72756-115">Attributes and accessibility modifiers are not permitted on `let` bindings in classes.</span></span>

<span data-ttu-id="72756-116">Os exemplos de código a seguir ilustram a vários tipos de `let` associações em classes.</span><span class="sxs-lookup"><span data-stu-id="72756-116">The following code examples illustrate several types of `let` bindings in classes.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

<span data-ttu-id="72756-117">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="72756-117">The output is as follows.</span></span>

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a><span data-ttu-id="72756-118">Maneiras alternativas de criar campos</span><span class="sxs-lookup"><span data-stu-id="72756-118">Alternative Ways to Create Fields</span></span>
<span data-ttu-id="72756-119">Você também pode usar o `val` palavra-chave para criar um campo particular.</span><span class="sxs-lookup"><span data-stu-id="72756-119">You can also use the `val` keyword to create a private field.</span></span> <span data-ttu-id="72756-120">Ao usar o `val` palavra-chave, o campo não tem um valor quando o objeto é criado, mas em vez disso, é inicializado com um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="72756-120">When using the `val` keyword, the field is not given a value when the object is created, but instead is initialized with a default value.</span></span> <span data-ttu-id="72756-121">Para obter mais informações, consulte [campos explícitos: A val palavra-chave](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="72756-121">For more information, see [Explicit Fields: The val Keyword](explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="72756-122">Você também pode definir campos particulares em uma classe usando uma definição de membro e adicionando a palavra-chave `private` na definição.</span><span class="sxs-lookup"><span data-stu-id="72756-122">You can also define private fields in a class by using a member definition and adding the keyword `private` to the definition.</span></span> <span data-ttu-id="72756-123">Isso pode ser útil se você pretende alterar a acessibilidade de um membro sem recriação de seu código.</span><span class="sxs-lookup"><span data-stu-id="72756-123">This can be useful if you expect to change the accessibility of a member without rewriting your code.</span></span> <span data-ttu-id="72756-124">Para saber mais, veja [Controle de acesso](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="72756-124">For more information, see [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="72756-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72756-125">See Also</span></span>
[<span data-ttu-id="72756-126">Membros</span><span class="sxs-lookup"><span data-stu-id="72756-126">Members</span></span>](index.md)

[<span data-ttu-id="72756-127">`do`Associações em Classes</span><span class="sxs-lookup"><span data-stu-id="72756-127">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)

[<span data-ttu-id="72756-128">`let`Associações</span><span class="sxs-lookup"><span data-stu-id="72756-128">`let` Bindings</span></span>](../functions/let-bindings.md)
