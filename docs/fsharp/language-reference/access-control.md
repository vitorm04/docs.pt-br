---
title: Controle de acesso (F#)
description: "Aprenda a controlar o acesso aos elementos de programação, como tipos, métodos e as funções, em F # linguagem de programação."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 955b06fe-d1cd-431d-8db6-93e83b697453
ms.openlocfilehash: a02e20a585a0456577901f2762a0eeb0e3ecd2f0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="access-control"></a><span data-ttu-id="2fad1-104">Controle de acesso</span><span class="sxs-lookup"><span data-stu-id="2fad1-104">Access Control</span></span>

<span data-ttu-id="2fad1-105">*Controle de acesso* refere-se ao declarando que os clientes podem usar determinados elementos do programa, como tipos, métodos e funções.</span><span class="sxs-lookup"><span data-stu-id="2fad1-105">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>


## <a name="basics-of-access-control"></a><span data-ttu-id="2fad1-106">Noções básicas de controle de acesso</span><span class="sxs-lookup"><span data-stu-id="2fad1-106">Basics of Access Control</span></span>
<span data-ttu-id="2fad1-107">Em F #, o acesso controle especificadores `public`, `internal`, e `private` pode ser aplicado a módulos, tipos, métodos, definições de valores, funções, propriedades e campos explícitos.</span><span class="sxs-lookup"><span data-stu-id="2fad1-107">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>


- <span data-ttu-id="2fad1-108">`public`indica que a entidade pode ser acessada por todos os chamadores.</span><span class="sxs-lookup"><span data-stu-id="2fad1-108">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="2fad1-109">`internal`indica que a entidade pode ser acessada somente do mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="2fad1-109">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="2fad1-110">`private`Indica se a entidade pode ser acessada apenas no delimitador tipo ou módulo.</span><span class="sxs-lookup"><span data-stu-id="2fad1-110">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>


>[!NOTE] 
<span data-ttu-id="2fad1-111">O especificador de acesso `protected` não é usada em F #, embora seja aceitável se você estiver usando tipos criados em idiomas que dão suporte a `protected` acesso.</span><span class="sxs-lookup"><span data-stu-id="2fad1-111">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="2fad1-112">Portanto, se você substituir um método protegido, o método permanece acessível somente dentro da classe e seus descendentes.</span><span class="sxs-lookup"><span data-stu-id="2fad1-112">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="2fad1-113">Em geral, o especificador é colocado na frente do nome da entidade, exceto quando uma `mutable` ou `inline` especificador for usado, o que aparecer após o especificador de controle de acesso.</span><span class="sxs-lookup"><span data-stu-id="2fad1-113">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="2fad1-114">Se nenhum especificador de acesso for usado, o padrão é `public`, exceto para `let` associações em um tipo, que são sempre `private` para o tipo.</span><span class="sxs-lookup"><span data-stu-id="2fad1-114">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="2fad1-115">Assinaturas em F # fornecem outro mecanismo para controlar o acesso aos elementos do programa F #.</span><span class="sxs-lookup"><span data-stu-id="2fad1-115">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="2fad1-116">As assinaturas não são necessárias para controle de acesso.</span><span class="sxs-lookup"><span data-stu-id="2fad1-116">Signatures are not required for access control.</span></span> <span data-ttu-id="2fad1-117">Para saber mais, confira [Assinaturas](signatures.md).</span><span class="sxs-lookup"><span data-stu-id="2fad1-117">For more information, see [Signatures](signatures.md).</span></span>


## <a name="rules-for-access-control"></a><span data-ttu-id="2fad1-118">Regras de controle de acesso</span><span class="sxs-lookup"><span data-stu-id="2fad1-118">Rules for Access Control</span></span>
<span data-ttu-id="2fad1-119">Controle de acesso está sujeito às seguintes regras:</span><span class="sxs-lookup"><span data-stu-id="2fad1-119">Access control is subject to the following rules:</span></span>


- <span data-ttu-id="2fad1-120">Declarações de herança (ou seja, o uso de `inherit` para especificar uma classe base para uma classe), interface declarações (isto é, especificando uma classe implementa uma interface) e abstrato membros sempre têm a mesma acessibilidade que o tipo de delimitador.</span><span class="sxs-lookup"><span data-stu-id="2fad1-120">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="2fad1-121">Portanto, um especificador de controle de acesso não pode ser usado em dessas construções.</span><span class="sxs-lookup"><span data-stu-id="2fad1-121">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="2fad1-122">Casos individuais em uma união discriminada não podem ter seus próprios modificadores de controle de acesso separados do tipo de união.</span><span class="sxs-lookup"><span data-stu-id="2fad1-122">Individual cases in a discriminated union cannot have their own access control modifiers separate from the union type.</span></span>

- <span data-ttu-id="2fad1-123">Campos individuais de um tipo de registro não podem ter seus próprios modificadores de controle de acesso separados do tipo de registro.</span><span class="sxs-lookup"><span data-stu-id="2fad1-123">Individual fields of a record type cannot have their own access control modifiers separate from the record type.</span></span>


## <a name="example"></a><span data-ttu-id="2fad1-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2fad1-124">Example</span></span>
<span data-ttu-id="2fad1-125">O código a seguir ilustra o uso de especificadores de controle de acesso.</span><span class="sxs-lookup"><span data-stu-id="2fad1-125">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="2fad1-126">Há dois arquivos no projeto, `Module1.fs` e `Module2.fs`.</span><span class="sxs-lookup"><span data-stu-id="2fad1-126">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="2fad1-127">Cada arquivo é implicitamente um módulo.</span><span class="sxs-lookup"><span data-stu-id="2fad1-127">Each file is implicitly a module.</span></span> <span data-ttu-id="2fad1-128">Portanto, há dois módulos, `Module1` e `Module2`.</span><span class="sxs-lookup"><span data-stu-id="2fad1-128">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="2fad1-129">Um tipo particular e um tipo interno são definidos no `Module1`.</span><span class="sxs-lookup"><span data-stu-id="2fad1-129">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="2fad1-130">O tipo particular não pode ser acessado de `Module2`, mas o tipo interno.</span><span class="sxs-lookup"><span data-stu-id="2fad1-130">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]
    
<span data-ttu-id="2fad1-131">O código a seguir testa a acessibilidade dos tipos criados no `Module1.fs`.</span><span class="sxs-lookup"><span data-stu-id="2fad1-131">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]
    
## <a name="see-also"></a><span data-ttu-id="2fad1-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fad1-132">See Also</span></span>
[<span data-ttu-id="2fad1-133">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="2fad1-133">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="2fad1-134">Assinaturas</span><span class="sxs-lookup"><span data-stu-id="2fad1-134">Signatures</span></span>](signatures.md)
