---
title: Herança (F#)
description: "Saiba como especificar relações de herança F # usando a palavra-chave 'inherit'."
ms.date: 05/16/2016
ms.openlocfilehash: e4d79244fb9bada5db0c5c4c7179d4bfe6e21f3d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864463"
---
# <a name="inheritance"></a><span data-ttu-id="c2897-103">Herança</span><span class="sxs-lookup"><span data-stu-id="c2897-103">Inheritance</span></span>

<span data-ttu-id="c2897-104">Herança é usada para modelar a relação "é um" ou subtipagem na programação orientada a objeto.</span><span class="sxs-lookup"><span data-stu-id="c2897-104">Inheritance is used to model the "is-a" relationship, or subtyping, in object-oriented programming.</span></span>

## <a name="specifying-inheritance-relationships"></a><span data-ttu-id="c2897-105">Especificando relações de herança</span><span class="sxs-lookup"><span data-stu-id="c2897-105">Specifying Inheritance Relationships</span></span>

<span data-ttu-id="c2897-106">Especificar relações de herança usando o `inherit` palavra-chave em uma declaração de classe.</span><span class="sxs-lookup"><span data-stu-id="c2897-106">You specify inheritance relationships by using the `inherit` keyword in a class declaration.</span></span> <span data-ttu-id="c2897-107">A forma sintática básica é mostrada no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c2897-107">The basic syntactical form is shown in the following example.</span></span>

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

<span data-ttu-id="c2897-108">Uma classe pode ter no máximo uma classe base direta.</span><span class="sxs-lookup"><span data-stu-id="c2897-108">A class can have at most one direct base class.</span></span> <span data-ttu-id="c2897-109">Se você não especificar uma classe base usando o `inherit` palavra-chave, a classe herda implicitamente de `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="c2897-109">If you do not specify a base class by using the `inherit` keyword, the class implicitly inherits from `System.Object`.</span></span>

## <a name="inherited-members"></a><span data-ttu-id="c2897-110">Membros herdados</span><span class="sxs-lookup"><span data-stu-id="c2897-110">Inherited Members</span></span>

<span data-ttu-id="c2897-111">Se uma classe herda de outra classe, os métodos e membros da classe base estão disponíveis para os usuários da classe derivada, como se fossem membros diretos da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c2897-111">If a class inherits from another class, the methods and members of the base class are available to users of the derived class as if they were direct members of the derived class.</span></span>

<span data-ttu-id="c2897-112">Quaisquer associações let e parâmetros do construtor são particulares para uma classe e, portanto, não podem ser acessados de classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="c2897-112">Any let bindings and constructor parameters are private to a class and, therefore, cannot be accessed from derived classes.</span></span>

<span data-ttu-id="c2897-113">A palavra-chave `base` está disponível em classes derivadas e refere-se à instância de classe base.</span><span class="sxs-lookup"><span data-stu-id="c2897-113">The keyword `base` is available in derived classes and refers to the base class instance.</span></span> <span data-ttu-id="c2897-114">Ele é usado como o identificador de Self.</span><span class="sxs-lookup"><span data-stu-id="c2897-114">It is used like the self-identifier.</span></span>

## <a name="virtual-methods-and-overrides"></a><span data-ttu-id="c2897-115">Substituições e métodos virtuais</span><span class="sxs-lookup"><span data-stu-id="c2897-115">Virtual Methods and Overrides</span></span>

<span data-ttu-id="c2897-116">Métodos virtuais (e propriedades) funcionam um pouco diferente no F # em comparação com outras linguagens .NET.</span><span class="sxs-lookup"><span data-stu-id="c2897-116">Virtual methods (and properties) work somewhat differently in F# as compared to other .NET languages.</span></span> <span data-ttu-id="c2897-117">Para declarar um novo membro virtual, você deve usar o `abstract` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="c2897-117">To declare a new virtual member, you use the `abstract` keyword.</span></span> <span data-ttu-id="c2897-118">Para fazer isso, independentemente se você fornecer uma implementação padrão para esse método.</span><span class="sxs-lookup"><span data-stu-id="c2897-118">You do this regardless of whether you provide a default implementation for that method.</span></span> <span data-ttu-id="c2897-119">Portanto, uma definição completa de um método virtual em uma classe base segue este padrão:</span><span class="sxs-lookup"><span data-stu-id="c2897-119">Thus a complete definition of a virtual method in a base class follows this pattern:</span></span>

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="c2897-120">E, em uma classe derivada, uma substituição do método virtual segue este padrão:</span><span class="sxs-lookup"><span data-stu-id="c2897-120">And in a derived class, an override of this virtual method follows this pattern:</span></span>

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="c2897-121">Se você omitir a implementação padrão na classe base, a classe base se torna uma classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="c2897-121">If you omit the default implementation in the base class, the base class becomes an abstract class.</span></span>

<span data-ttu-id="c2897-122">O exemplo de código a seguir ilustra a declaração de um novo método virtual `function1` em uma classe base e como substituí-la em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c2897-122">The following code example illustrates the declaration of a new virtual method `function1` in a base class and how to override it in a derived class.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a><span data-ttu-id="c2897-123">Construtores e herança</span><span class="sxs-lookup"><span data-stu-id="c2897-123">Constructors and Inheritance</span></span>

<span data-ttu-id="c2897-124">O construtor para a classe base deve ser chamado na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c2897-124">The constructor for the base class must be called in the derived class.</span></span> <span data-ttu-id="c2897-125">Os argumentos para o construtor de classe base aparecem na lista de argumentos a `inherit` cláusula.</span><span class="sxs-lookup"><span data-stu-id="c2897-125">The arguments for the base class constructor appear in the argument list in the `inherit` clause.</span></span> <span data-ttu-id="c2897-126">Os valores que são usados devem ser determinados dos argumentos fornecidos para o construtor de classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c2897-126">The values that are used must be determined from the arguments supplied to the derived class constructor.</span></span>

<span data-ttu-id="c2897-127">O código a seguir mostra uma classe base e uma classe derivada, em que a classe derivada chama o construtor de classe base na cláusula herdar:</span><span class="sxs-lookup"><span data-stu-id="c2897-127">The following code shows a base class and a derived class, where the derived class calls the base class constructor in the inherit clause:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

<span data-ttu-id="c2897-128">No caso de vários construtores, o código a seguir pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="c2897-128">In the case of multiple constructors, the following code can be used.</span></span> <span data-ttu-id="c2897-129">A primeira linha dos construtores de classe derivada é o `inherit` cláusula e os campos aparecem como campos explícitos são declarados com o `val` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="c2897-129">The first line of the derived class constructors is the `inherit` clause, and the fields appear as explicit fields that are declared with the `val` keyword.</span></span> <span data-ttu-id="c2897-130">Para obter mais informações, consulte [campos explícitos: A `val` palavra-chave](members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="c2897-130">For more information, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

```fsharp
type BaseClass =
    val string1 : string
    new (str) = { string1 = str }
    new () = { string1 = "" }

type DerivedClass =
    inherit BaseClass

    val string2 : string
    new (str1, str2) = { inherit BaseClass(str1); string2 = str2 }
    new (str2) = { inherit BaseClass(); string2 = str2 }

let obj1 = DerivedClass("A", "B")
let obj2 = DerivedClass("A")
```

## <a name="alternatives-to-inheritance"></a><span data-ttu-id="c2897-131">Alternativas à herança</span><span class="sxs-lookup"><span data-stu-id="c2897-131">Alternatives to Inheritance</span></span>

<span data-ttu-id="c2897-132">Em casos em que uma pequena modificação de um tipo é necessária, considere o uso de uma expressão de objeto como uma alternativa para herança.</span><span class="sxs-lookup"><span data-stu-id="c2897-132">In cases where a minor modification of a type is required, consider using an object expression as an alternative to inheritance.</span></span> <span data-ttu-id="c2897-133">O exemplo a seguir ilustra o uso de uma expressão de objeto como uma alternativa para criar um novo tipo derivado:</span><span class="sxs-lookup"><span data-stu-id="c2897-133">The following example illustrates the use of an object expression as an alternative to creating a new derived type:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

<span data-ttu-id="c2897-134">Para obter mais informações sobre expressões de objeto, consulte [expressões do objeto](object-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c2897-134">For more information about object expressions, see [Object Expressions](object-expressions.md).</span></span>

<span data-ttu-id="c2897-135">Quando você estiver criando hierarquias de objeto, considere o uso de uma união discriminada em vez da herança.</span><span class="sxs-lookup"><span data-stu-id="c2897-135">When you are creating object hierarchies, consider using a discriminated union instead of inheritance.</span></span> <span data-ttu-id="c2897-136">As uniões discriminadas também podem comportamento do modelo variado de objetos diferentes que compartilham um tipo geral comum.</span><span class="sxs-lookup"><span data-stu-id="c2897-136">Discriminated unions can also model varied behavior of different objects that share a common overall type.</span></span> <span data-ttu-id="c2897-137">Uma união discriminada única pode muitas vezes eliminar a necessidade de um número de classes derivadas que são pequenas variações uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="c2897-137">A single discriminated union can often eliminate the need for a number of derived classes that are minor variations of each other.</span></span> <span data-ttu-id="c2897-138">Para obter informações sobre as uniões discriminadas, consulte [uniões discriminadas](discriminated-unions.md).</span><span class="sxs-lookup"><span data-stu-id="c2897-138">For information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c2897-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2897-139">See also</span></span>

- [<span data-ttu-id="c2897-140">Expressões de Objeto</span><span class="sxs-lookup"><span data-stu-id="c2897-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="c2897-141">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="c2897-141">F# Language Reference</span></span>](index.md)
