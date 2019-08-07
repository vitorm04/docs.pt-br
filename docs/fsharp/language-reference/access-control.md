---
title: Controle de acesso
description: Saiba como controlar o acesso a elementos de programação, como tipos, métodos e funções, na linguagem de F# programação.
ms.date: 05/16/2016
ms.openlocfilehash: 38f8f3fd4114c0428fbe8baca71594cd07740b2c
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817859"
---
# <a name="access-control"></a><span data-ttu-id="025f9-103">Controle de acesso</span><span class="sxs-lookup"><span data-stu-id="025f9-103">Access Control</span></span>

<span data-ttu-id="025f9-104">O *controle de acesso* refere-se à declaração de quais clientes podem usar determinados elementos do programa, como tipos, métodos e funções.</span><span class="sxs-lookup"><span data-stu-id="025f9-104">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>

## <a name="basics-of-access-control"></a><span data-ttu-id="025f9-105">Noções básicas do controle de acesso</span><span class="sxs-lookup"><span data-stu-id="025f9-105">Basics of Access Control</span></span>

<span data-ttu-id="025f9-106">No F#, os especificadores `public`de controle de `internal`acesso, `private` e podem ser aplicados a módulos, tipos, métodos, definições de valor, funções, propriedades e campos explícitos.</span><span class="sxs-lookup"><span data-stu-id="025f9-106">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>

- <span data-ttu-id="025f9-107">`public`indica que a entidade pode ser acessada por todos os chamadores.</span><span class="sxs-lookup"><span data-stu-id="025f9-107">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="025f9-108">`internal`indica que a entidade pode ser acessada somente do mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="025f9-108">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="025f9-109">`private`indica que a entidade pode ser acessada somente do tipo ou módulo delimitador.</span><span class="sxs-lookup"><span data-stu-id="025f9-109">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>

> [!NOTE]
> <span data-ttu-id="025f9-110">O especificador `protected` de acesso não é F#usado no, embora seja aceitável se você estiver usando tipos criados em linguagens que dão `protected` suporte ao acesso.</span><span class="sxs-lookup"><span data-stu-id="025f9-110">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="025f9-111">Portanto, se você substituir um método protegido, seu método permanecerá acessível somente dentro da classe e seus descendentes.</span><span class="sxs-lookup"><span data-stu-id="025f9-111">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="025f9-112">Em geral, o especificador é colocado na frente do nome da entidade, exceto quando um `mutable` especificador ou `inline` é usado, que aparece após o especificador de controle de acesso.</span><span class="sxs-lookup"><span data-stu-id="025f9-112">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="025f9-113">Se nenhum especificador de acesso for usado, o `public`padrão será, `let` exceto para associações em um tipo, que são `private` sempre para o tipo.</span><span class="sxs-lookup"><span data-stu-id="025f9-113">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="025f9-114">As assinaturas F# no fornecem outro mecanismo para controlar o F# acesso aos elementos do programa.</span><span class="sxs-lookup"><span data-stu-id="025f9-114">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="025f9-115">As assinaturas não são necessárias para o controle de acesso.</span><span class="sxs-lookup"><span data-stu-id="025f9-115">Signatures are not required for access control.</span></span> <span data-ttu-id="025f9-116">Para saber mais, confira [Assinaturas](signatures.md).</span><span class="sxs-lookup"><span data-stu-id="025f9-116">For more information, see [Signatures](signatures.md).</span></span>

## <a name="rules-for-access-control"></a><span data-ttu-id="025f9-117">Regras para controle de acesso</span><span class="sxs-lookup"><span data-stu-id="025f9-117">Rules for Access Control</span></span>

<span data-ttu-id="025f9-118">O controle de acesso está sujeito às seguintes regras:</span><span class="sxs-lookup"><span data-stu-id="025f9-118">Access control is subject to the following rules:</span></span>

- <span data-ttu-id="025f9-119">Declarações de herança (ou seja, o uso `inherit` de para especificar uma classe base para uma classe), declarações de interface (ou seja, especificar que uma classe implementa uma interface) e membros abstratos sempre têm a mesma acessibilidade que o tipo delimitador.</span><span class="sxs-lookup"><span data-stu-id="025f9-119">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="025f9-120">Portanto, um especificador de controle de acesso não pode ser usado nessas construções.</span><span class="sxs-lookup"><span data-stu-id="025f9-120">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="025f9-121">A acessibilidade para casos individuais em uma união discriminada é determinada pela acessibilidade da união discriminada em si.</span><span class="sxs-lookup"><span data-stu-id="025f9-121">Accessibility for individual cases in a discriminated union is determined by the accessibility of the discriminated union itself.</span></span> <span data-ttu-id="025f9-122">Ou seja, um caso de União específico não é menos acessível do que a União em si.</span><span class="sxs-lookup"><span data-stu-id="025f9-122">That is, a particular union case is no less accessible than the union itself.</span></span>

- <span data-ttu-id="025f9-123">A acessibilidade para campos individuais de um tipo de registro é determinada pela acessibilidade do próprio registro.</span><span class="sxs-lookup"><span data-stu-id="025f9-123">Accessibility for individual fields of a record type is determined by the accessibility of the record itself.</span></span> <span data-ttu-id="025f9-124">Ou seja, um rótulo de registro específico não é menos acessível do que o próprio registro.</span><span class="sxs-lookup"><span data-stu-id="025f9-124">That is, a particular record label is no less accessible than the record itself.</span></span>

## <a name="example"></a><span data-ttu-id="025f9-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="025f9-125">Example</span></span>

<span data-ttu-id="025f9-126">O código a seguir ilustra o uso de especificadores de controle de acesso.</span><span class="sxs-lookup"><span data-stu-id="025f9-126">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="025f9-127">Há dois arquivos no projeto `Module1.fs` e. `Module2.fs`</span><span class="sxs-lookup"><span data-stu-id="025f9-127">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="025f9-128">Cada arquivo é implicitamente um módulo.</span><span class="sxs-lookup"><span data-stu-id="025f9-128">Each file is implicitly a module.</span></span> <span data-ttu-id="025f9-129">Portanto, há dois módulos, `Module1` e. `Module2`</span><span class="sxs-lookup"><span data-stu-id="025f9-129">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="025f9-130">Um tipo privado e um tipo interno são definidos em `Module1`.</span><span class="sxs-lookup"><span data-stu-id="025f9-130">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="025f9-131">O tipo particular não pode ser acessado de `Module2`, mas o tipo interno pode.</span><span class="sxs-lookup"><span data-stu-id="025f9-131">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet1.fs)]

<span data-ttu-id="025f9-132">O código a seguir testa a acessibilidade dos tipos criados no `Module1.fs`.</span><span class="sxs-lookup"><span data-stu-id="025f9-132">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a><span data-ttu-id="025f9-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="025f9-133">See also</span></span>

- [<span data-ttu-id="025f9-134">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="025f9-134">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="025f9-135">Assinaturas</span><span class="sxs-lookup"><span data-stu-id="025f9-135">Signatures</span></span>](signatures.md)
