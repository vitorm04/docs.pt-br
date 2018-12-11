---
title: Controle de acesso (F#)
description: Aprenda a controlar o acesso aos elementos de programação, como tipos, métodos e funções, no F# linguagem de programação.
ms.date: 05/16/2016
ms.openlocfilehash: 136eba5ec33fa6128e677b614fc0ace3c71d17df
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153703"
---
# <a name="access-control"></a><span data-ttu-id="a57bf-103">Controle de acesso</span><span class="sxs-lookup"><span data-stu-id="a57bf-103">Access Control</span></span>

<span data-ttu-id="a57bf-104">*Controle de acesso* refere-se ao declarar a quais clientes podem usar determinados elementos do programa, como tipos, métodos e funções.</span><span class="sxs-lookup"><span data-stu-id="a57bf-104">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>

## <a name="basics-of-access-control"></a><span data-ttu-id="a57bf-105">Noções básicas de controle de acesso</span><span class="sxs-lookup"><span data-stu-id="a57bf-105">Basics of Access Control</span></span>

<span data-ttu-id="a57bf-106">No F#, os especificadores de controle de acesso `public`, `internal`, e `private` pode ser aplicado a módulos, tipos, métodos, definições de valor, funções, propriedades e campos explícitos.</span><span class="sxs-lookup"><span data-stu-id="a57bf-106">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>

- <span data-ttu-id="a57bf-107">`public` indica que a entidade pode ser acessada por todos os chamadores.</span><span class="sxs-lookup"><span data-stu-id="a57bf-107">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="a57bf-108">`internal` indica que a entidade pode ser acessada somente do mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="a57bf-108">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="a57bf-109">`private` indica que a entidade pode ser acessada somente de módulo ou tipo de delimitador.</span><span class="sxs-lookup"><span data-stu-id="a57bf-109">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>

> [!NOTE]
> <span data-ttu-id="a57bf-110">O especificador de acesso `protected` não é usado no F#, embora seja aceitável se você estiver usando tipos criados em linguagens que dão suporte a `protected` acesso.</span><span class="sxs-lookup"><span data-stu-id="a57bf-110">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="a57bf-111">Portanto, se você substituir um método protegido, o método permanece acessível somente dentro da classe e seus descendentes.</span><span class="sxs-lookup"><span data-stu-id="a57bf-111">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="a57bf-112">Em geral, o especificador é colocado na frente do nome da entidade, exceto quando um `mutable` ou `inline` especificador for usado, o que aparecer após o especificador de controle de acesso.</span><span class="sxs-lookup"><span data-stu-id="a57bf-112">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="a57bf-113">Se nenhum especificador de acesso for usado, o padrão é `public`, exceto para `let` associações em um tipo, que são sempre `private` para o tipo.</span><span class="sxs-lookup"><span data-stu-id="a57bf-113">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="a57bf-114">As assinaturas no F# fornecem outro mecanismo para controlar o acesso ao F# elementos do programa.</span><span class="sxs-lookup"><span data-stu-id="a57bf-114">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="a57bf-115">Assinaturas não são necessárias para controle de acesso.</span><span class="sxs-lookup"><span data-stu-id="a57bf-115">Signatures are not required for access control.</span></span> <span data-ttu-id="a57bf-116">Para saber mais, confira [Assinaturas](signatures.md).</span><span class="sxs-lookup"><span data-stu-id="a57bf-116">For more information, see [Signatures](signatures.md).</span></span>

## <a name="rules-for-access-control"></a><span data-ttu-id="a57bf-117">Regras para o controle de acesso</span><span class="sxs-lookup"><span data-stu-id="a57bf-117">Rules for Access Control</span></span>

<span data-ttu-id="a57bf-118">Controle de acesso está sujeito às seguintes regras:</span><span class="sxs-lookup"><span data-stu-id="a57bf-118">Access control is subject to the following rules:</span></span>

- <span data-ttu-id="a57bf-119">Declarações de herança (ou seja, o uso de `inherit` para especificar uma classe base para uma classe), declarações (isto é, especificando que uma classe implementa uma interface) de interface e abstrair os membros têm sempre a mesma acessibilidade que o tipo delimitador.</span><span class="sxs-lookup"><span data-stu-id="a57bf-119">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="a57bf-120">Portanto, um especificador de controle de acesso não pode ser usado nessas construções.</span><span class="sxs-lookup"><span data-stu-id="a57bf-120">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="a57bf-121">Acessibilidade para casos individuais em uma união discriminada é determinada pela acessibilidade da união discriminada em si.</span><span class="sxs-lookup"><span data-stu-id="a57bf-121">Accessibility for individual cases in a discriminated union is determined by the accessibility of the discriminated union itself.</span></span> <span data-ttu-id="a57bf-122">Ou seja, um caso específico de união é não menos acessível do que a própria união.</span><span class="sxs-lookup"><span data-stu-id="a57bf-122">That is, a particular union case is no less accessible than the union itself.</span></span>

- <span data-ttu-id="a57bf-123">Acessibilidade campos individuais de um tipo de registro não não determinada pela acessibilidade do registro em si.</span><span class="sxs-lookup"><span data-stu-id="a57bf-123">Accessibility for individual fields of a record type cannot is determined by the accessibility of the record itself.</span></span> <span data-ttu-id="a57bf-124">Ou seja, um rótulo de determinado registro é não menos acessível que o registro em si.</span><span class="sxs-lookup"><span data-stu-id="a57bf-124">That is, a particular record label is no less accessible than the record itself.</span></span>

## <a name="example"></a><span data-ttu-id="a57bf-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a57bf-125">Example</span></span>

<span data-ttu-id="a57bf-126">O código a seguir ilustra o uso dos especificadores de controle de acesso.</span><span class="sxs-lookup"><span data-stu-id="a57bf-126">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="a57bf-127">Existem dois arquivos no projeto, `Module1.fs` e `Module2.fs`.</span><span class="sxs-lookup"><span data-stu-id="a57bf-127">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="a57bf-128">Cada arquivo é implicitamente um módulo.</span><span class="sxs-lookup"><span data-stu-id="a57bf-128">Each file is implicitly a module.</span></span> <span data-ttu-id="a57bf-129">Portanto, há dois módulos, `Module1` e `Module2`.</span><span class="sxs-lookup"><span data-stu-id="a57bf-129">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="a57bf-130">Um tipo particular e um tipo interno são definidos em `Module1`.</span><span class="sxs-lookup"><span data-stu-id="a57bf-130">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="a57bf-131">O tipo particular não pode ser acessado de `Module2`, mas o tipo interno pode.</span><span class="sxs-lookup"><span data-stu-id="a57bf-131">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]

<span data-ttu-id="a57bf-132">O código a seguir testa a acessibilidade dos tipos criados no `Module1.fs`.</span><span class="sxs-lookup"><span data-stu-id="a57bf-132">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a><span data-ttu-id="a57bf-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a57bf-133">See also</span></span>

- [<span data-ttu-id="a57bf-134">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="a57bf-134">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="a57bf-135">Assinaturas</span><span class="sxs-lookup"><span data-stu-id="a57bf-135">Signatures</span></span>](signatures.md)
