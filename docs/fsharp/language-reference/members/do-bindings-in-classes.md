---
title: Associações do em classes (F#)
description: "Saiba como usar F # 'do' associação em uma definição de classe, que executa ações quando o objeto é criado ou quando o tipo é usado pela primeira vez."
ms.date: 05/16/2016
ms.openlocfilehash: e54a5bde52bf6973cc338c929ba99e6fd5b53127
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43801510"
---
# <a name="do-bindings-in-classes"></a><span data-ttu-id="9e510-103">Associações do em classes</span><span class="sxs-lookup"><span data-stu-id="9e510-103">do Bindings in Classes</span></span>

<span data-ttu-id="9e510-104">Um `do` associação em uma definição de classe executa ações quando o objeto é construído ou, para um estático `do` associação, quando o tipo é usado primeiro.</span><span class="sxs-lookup"><span data-stu-id="9e510-104">A `do` binding in a class definition performs actions when the object is constructed or, for a static `do` binding, when the type is first used.</span></span>

## <a name="syntax"></a><span data-ttu-id="9e510-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e510-105">Syntax</span></span>

```fsharp
[static] do expression
```

## <a name="remarks"></a><span data-ttu-id="9e510-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="9e510-106">Remarks</span></span>

<span data-ttu-id="9e510-107">Um `do` associação é exibida junto com ou após `let` associações, mas antes de definições de membro em uma definição de classe.</span><span class="sxs-lookup"><span data-stu-id="9e510-107">A `do` binding appears together with or after `let` bindings but before member definitions in a class definition.</span></span> <span data-ttu-id="9e510-108">Embora o `do` palavra-chave é opcional para o `do` associações no nível de módulo, não é opcional para `do` ligações em uma definição de classe.</span><span class="sxs-lookup"><span data-stu-id="9e510-108">Although the `do` keyword is optional for `do` bindings at the module level, it is not optional for `do` bindings in a class definition.</span></span>

<span data-ttu-id="9e510-109">Para a construção de cada objeto de qualquer determinado tipo, não estáticos `do` associações e não-estático `let` associações são executadas na ordem em que aparecem na definição de classe.</span><span class="sxs-lookup"><span data-stu-id="9e510-109">For the construction of every object of any given type, non-static `do` bindings and non-static `let` bindings are executed in the order in which they appear in the class definition.</span></span> <span data-ttu-id="9e510-110">Vários `do` associações podem ocorrer em um tipo.</span><span class="sxs-lookup"><span data-stu-id="9e510-110">Multiple `do` bindings can occur in one type.</span></span> <span data-ttu-id="9e510-111">O não-estático `let` associações e não-estático `do` associações tornam-se o corpo do construtor primário.</span><span class="sxs-lookup"><span data-stu-id="9e510-111">The non-static `let` bindings and the non-static `do` bindings become the body of the primary constructor.</span></span> <span data-ttu-id="9e510-112">O código não-estático `do` seção de associações pode fazer referência a parâmetros do construtor primário e todos os valores ou funções que são definidas na `let` seção de associações.</span><span class="sxs-lookup"><span data-stu-id="9e510-112">The code in the non-static `do` bindings section can reference the primary constructor parameters and any values or functions that are defined in the `let` bindings section.</span></span>

<span data-ttu-id="9e510-113">Não-estático `do` associações podem acessar membros da classe, desde que a classe tem um identificador de autoatendimento que é definido por um `as` palavra-chave na classe de título e, desde que todos os usos desses membros são qualificados com o identificador de autoatendimento para a classe.</span><span class="sxs-lookup"><span data-stu-id="9e510-113">Non-static `do` bindings can access members of the class as long as the class has a self identifier that is defined by an `as` keyword in the class heading, and as long as all uses of those members are qualified with the self identifier for the class.</span></span>

<span data-ttu-id="9e510-114">Porque `let` associações inicializar os campos privados de uma classe, que é geralmente necessário para garantir que os membros se comportam conforme o esperado, `do` associações geralmente são colocadas depois `let` associações de forma que o código a `do` associação pode Execute com um objeto totalmente inicializado.</span><span class="sxs-lookup"><span data-stu-id="9e510-114">Because `let` bindings initialize the private fields of a class, which is often necessary to guarantee that members behave as expected, `do` bindings are usually put after `let` bindings so that code in the `do` binding can execute with a fully initialized object.</span></span> <span data-ttu-id="9e510-115">Se seu código tentar usar um membro antes que a inicialização é concluída, uma InvalidOperationException é gerada.</span><span class="sxs-lookup"><span data-stu-id="9e510-115">If your code attempts to use a member before the initialization is complete, an InvalidOperationException is raised.</span></span>

<span data-ttu-id="9e510-116">Estático `do` ligações podem fazer referência a membros estáticos ou campos de fechamento de classe, mas não campos ou membros de instância.</span><span class="sxs-lookup"><span data-stu-id="9e510-116">Static `do` bindings can reference static members or fields of the enclosing class but not instance members or fields.</span></span> <span data-ttu-id="9e510-117">Estático `do` associações se tornam parte do inicializador estático para a classe, que é a garantia de serem executados antes que a classe é usada pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="9e510-117">Static `do` bindings become part of the static initializer for the class, which is guaranteed to execute before the class is first used.</span></span>

<span data-ttu-id="9e510-118">Atributos são ignorados para `do` associações de tipos.</span><span class="sxs-lookup"><span data-stu-id="9e510-118">Attributes are ignored for `do` bindings in types.</span></span> <span data-ttu-id="9e510-119">Se um atributo é necessário para o código que é executado em um `do` de associação, ela deverá ser aplicada para o construtor primário.</span><span class="sxs-lookup"><span data-stu-id="9e510-119">If an attribute is required for code that executes in a `do` binding, it must be applied to the primary constructor.</span></span>

<span data-ttu-id="9e510-120">No código a seguir, uma classe tem um estático `do` associação e um não-estático `do` associação.</span><span class="sxs-lookup"><span data-stu-id="9e510-120">In the following code, a class has a static `do` binding and a non-static `do` binding.</span></span> <span data-ttu-id="9e510-121">O objeto tem um construtor que tem dois parâmetros, `a` e `b`, e dois campos particulares são definidos na `let` associações para a classe.</span><span class="sxs-lookup"><span data-stu-id="9e510-121">The object has a constructor that has two parameters, `a` and `b`, and two private fields are defined in the `let` bindings for the class.</span></span> <span data-ttu-id="9e510-122">Duas propriedades também são definidas.</span><span class="sxs-lookup"><span data-stu-id="9e510-122">Two properties are also defined.</span></span> <span data-ttu-id="9e510-123">Todos eles estão no escopo em não-estático `do` seção de associações, conforme é ilustrado pela linha que imprime todos esses valores.</span><span class="sxs-lookup"><span data-stu-id="9e510-123">All of these are in scope in the non-static `do` bindings section, as is illustrated by the line that prints all those values.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

<span data-ttu-id="9e510-124">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="9e510-124">The output is as follows.</span></span>

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a><span data-ttu-id="9e510-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e510-125">See also</span></span>

- [<span data-ttu-id="9e510-126">Membros</span><span class="sxs-lookup"><span data-stu-id="9e510-126">Members</span></span>](index.md)
- [<span data-ttu-id="9e510-127">Classes</span><span class="sxs-lookup"><span data-stu-id="9e510-127">Classes</span></span>](../classes.md)
- [<span data-ttu-id="9e510-128">Construtores</span><span class="sxs-lookup"><span data-stu-id="9e510-128">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="9e510-129">`let`Associações em Classes</span><span class="sxs-lookup"><span data-stu-id="9e510-129">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
- [<span data-ttu-id="9e510-130">`do` Associações</span><span class="sxs-lookup"><span data-stu-id="9e510-130">`do` Bindings</span></span>](../functions/do-Bindings.md)
