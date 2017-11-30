---
title: Classes abstratas (F#)
description: "Saiba mais sobre F # classes abstratas, que deixar alguns ou todos os membros não implementados e representam a funcionalidade comum de um conjunto diversificado de tipos de objeto."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a3dcc335-433b-4672-ac2d-ae6b11b816f3
ms.openlocfilehash: 209bcca70318db59506011b1f2bb74a09bf3814a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="abstract-classes"></a><span data-ttu-id="1bcf7-104">Classes abstratas</span><span class="sxs-lookup"><span data-stu-id="1bcf7-104">Abstract Classes</span></span>

<span data-ttu-id="1bcf7-105">*Classes abstratas* são classes que deixam alguns ou todos os membros não implementados, para que as implementações podem ser fornecidas por classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-105">*Abstract classes* are classes that leave some or all members unimplemented, so that implementations can be provided by derived classes.</span></span>

## <a name="syntax"></a><span data-ttu-id="1bcf7-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1bcf7-106">Syntax</span></span>

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a><span data-ttu-id="1bcf7-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="1bcf7-107">Remarks</span></span>
<span data-ttu-id="1bcf7-108">Em programação orientada a objeto, uma classe abstrata é usada como uma classe base de uma hierarquia e representa a funcionalidade comum de um conjunto diversificado de tipos de objeto.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-108">In object-oriented programming, an abstract class is used as a base class of a hierarchy, and represents common functionality of a diverse set of object types.</span></span> <span data-ttu-id="1bcf7-109">Como o "abstrato" nome implica, classes abstratas geralmente não correspondem diretamente em concretas entidades no domínio do problema.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-109">As the name "abstract" implies, abstract classes often do not correspond directly onto concrete entities in the problem domain.</span></span> <span data-ttu-id="1bcf7-110">No entanto, eles representam o que muitas entidades concretas diferentes têm em comum.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-110">However, they do represent what many different concrete entities have in common.</span></span>

<span data-ttu-id="1bcf7-111">Classes abstratas devem ter o `AbstractClass` atributo.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-111">Abstract classes must have the `AbstractClass` attribute.</span></span> <span data-ttu-id="1bcf7-112">Pode ter implementado e não implementado membros.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-112">They can have implemented and unimplemented members.</span></span> <span data-ttu-id="1bcf7-113">O uso do termo *abstrata* quando aplicado a uma classe é igual de outras linguagens .NET; no entanto, o uso do termo *abstrata* quando aplicado a métodos (e propriedades) é um pouco diferente em F # do seu Use em outras linguagens .NET.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-113">The use of the term *abstract* when applied to a class is the same as in other .NET languages; however, the use of the term *abstract* when applied to methods (and properties) is a little different in F# from its use in other .NET languages.</span></span> <span data-ttu-id="1bcf7-114">Em F #, quando um método é marcado com o `abstract` palavra-chave, isso indica que um membro tem uma entrada, conhecida como um *slot de expedição virtual*, na tabela interna de funções virtuais para esse tipo.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-114">In F#, when a method is marked with the `abstract` keyword, this indicates that a member has an entry, known as a *virtual dispatch slot*, in the internal table of virtual functions for that type.</span></span> <span data-ttu-id="1bcf7-115">Em outras palavras, o método é virtual, embora o `virtual` palavra-chave não é usada na linguagem F #.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-115">In other words, the method is virtual, although the `virtual` keyword is not used in the F# language.</span></span> <span data-ttu-id="1bcf7-116">A palavra-chave `abstract` é usado em métodos virtuais, independentemente se o método é implementado.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-116">The keyword `abstract` is used on virtual methods regardless of whether the method is implemented.</span></span> <span data-ttu-id="1bcf7-117">A declaração de um slot de expedição virtual é separada da definição de um método para esse slot de expedição.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-117">The declaration of a virtual dispatch slot is separate from the definition of a method for that dispatch slot.</span></span> <span data-ttu-id="1bcf7-118">Portanto, o equivalente de uma declaração de método virtual e uma definição em outra linguagem .NET F # é uma combinação de uma declaração de método abstract e uma definição separada, com um o `default` palavra-chave ou o `override` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-118">Therefore, the F# equivalent of a virtual method declaration and definition in another .NET language is a combination of both an abstract method declaration and a separate definition, with either the `default` keyword or the `override` keyword.</span></span> <span data-ttu-id="1bcf7-119">Para obter mais informações e exemplos, consulte [métodos](members/methods.md).</span><span class="sxs-lookup"><span data-stu-id="1bcf7-119">For more information and examples, see [Methods](members/methods.md).</span></span>

<span data-ttu-id="1bcf7-120">Uma classe é considerada abstrata somente se houver métodos abstratos que declarada, mas não definidos.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-120">A class is considered abstract only if there are abstract methods that are declared but not defined.</span></span> <span data-ttu-id="1bcf7-121">Portanto, as classes que têm métodos abstratos não são necessariamente abstratas de classes.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-121">Therefore, classes that have abstract methods are not necessarily abstract classes.</span></span> <span data-ttu-id="1bcf7-122">A menos que uma classe possui indefinido métodos abstratos, não use o **AbstractClass** atributo.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-122">Unless a class has undefined abstract methods, do not use the **AbstractClass** attribute.</span></span>

<span data-ttu-id="1bcf7-123">Na sintaxe anterior, *modificador de acessibilidade* pode ser `public`, `private` ou `internal`.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-123">In the previous syntax, *accessibility-modifier* can be `public`, `private` or `internal`.</span></span> <span data-ttu-id="1bcf7-124">Para saber mais, veja [Controle de acesso](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="1bcf7-124">For more information, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="1bcf7-125">Assim como acontece com outros tipos, classes abstratas podem ter uma classe base e um ou mais interfaces base.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-125">As with other types, abstract classes can have a base class and one or more base interfaces.</span></span> <span data-ttu-id="1bcf7-126">Cada classe base ou interface aparece em uma linha separada junto com o `inherit` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-126">Each base class or interface appears on a separate line together with the `inherit` keyword.</span></span>

<span data-ttu-id="1bcf7-127">A definição do tipo de classe abstrata pode conter membros totalmente definidos, mas também pode conter membros abstratos.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-127">The type definition of an abstract class can contain fully defined members, but it can also contain abstract members.</span></span> <span data-ttu-id="1bcf7-128">A sintaxe para membros abstratos é exibida separadamente na sintaxe anterior.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-128">The syntax for abstract members is shown separately in the previous syntax.</span></span> <span data-ttu-id="1bcf7-129">Nessa sintaxe, o *assinatura de tipo* de um membro é uma lista que contém os tipos de parâmetro na ordem e os tipos de retorno, separados por `->` tokens e/ou `*` tokens conforme apropriado na forma curried e tupla parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-129">In this syntax, the *type signature* of a member is a list that contains the parameter types in order and the return types, separated by `->` tokens and/or `*` tokens as appropriate for curried and tupled parameters.</span></span> <span data-ttu-id="1bcf7-130">A sintaxe para assinaturas de tipo de membro abstrato é o mesmo que o usado em arquivos de assinatura e se mostrado pelo IntelliSense no Editor de código do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-130">The syntax for abstract member type signatures is the same as that used in signature files and that shown by IntelliSense in the Visual Studio Code Editor.</span></span>

<span data-ttu-id="1bcf7-131">O código a seguir ilustra uma classe abstrata forma, que tem duas classes de derivado não-abstrato, quadrado e círculo.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-131">The following code illustrates an abstract class Shape, which has two non-abstract derived classes, Square and Circle.</span></span> <span data-ttu-id="1bcf7-132">O exemplo mostra como usar propriedades, métodos e classes abstratas.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-132">The example shows how to use abstract classes, methods, and properties.</span></span> <span data-ttu-id="1bcf7-133">No exemplo, a forma de classe abstrata representa os elementos comuns do círculo de entidades concreta e quadrado.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-133">In the example, the abstract class Shape represents the common elements of the concrete entities circle and square.</span></span> <span data-ttu-id="1bcf7-134">Os recursos comuns de todas as formas (em um sistema de coordenadas bidimensional) são abstraídos limite para a classe de forma: a posição na grade, um ângulo de rotação e as propriedades de área e o perímetro.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-134">The common features of all shapes (in a two-dimensional coordinate system) are abstracted out into the Shape class: the position on the grid, an angle of rotation, and the area and perimeter properties.</span></span> <span data-ttu-id="1bcf7-135">Esses podem ser substituídas, com exceção de posição, o comportamento dos quais não é possível alterar formas individuais.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-135">These can be overridden, except for position, the behavior of which individual shapes cannot change.</span></span>

<span data-ttu-id="1bcf7-136">O método de rotação pode ser substituído, como a classe do círculo, que é a rotação invariável devido a seu simetria.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-136">The rotation method can be overridden, as in the Circle class, which is rotation invariant because of its symmetry.</span></span> <span data-ttu-id="1bcf7-137">Para a classe do círculo, o método de rotação é substituído por um método que não faz nada.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-137">So in the Circle class, the rotation method is replaced by a method that does nothing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

<span data-ttu-id="1bcf7-138">**Saída:**</span><span class="sxs-lookup"><span data-stu-id="1bcf7-138">**Output:**</span></span>

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a><span data-ttu-id="1bcf7-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1bcf7-139">See Also</span></span>
[<span data-ttu-id="1bcf7-140">Classes</span><span class="sxs-lookup"><span data-stu-id="1bcf7-140">Classes</span></span>](classes.md)

[<span data-ttu-id="1bcf7-141">Membros</span><span class="sxs-lookup"><span data-stu-id="1bcf7-141">Members</span></span>](members/index.md)

[<span data-ttu-id="1bcf7-142">Métodos</span><span class="sxs-lookup"><span data-stu-id="1bcf7-142">Methods</span></span>](members/methods.md)

[<span data-ttu-id="1bcf7-143">Propriedades</span><span class="sxs-lookup"><span data-stu-id="1bcf7-143">Properties</span></span>](members/Properties.md)
