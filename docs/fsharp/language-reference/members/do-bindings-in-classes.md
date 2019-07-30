---
title: Associações do em classes
description: Saiba como usar uma F# Associação ' do ' em uma definição de classe, que executa ações quando o objeto é construído ou quando o tipo é usado pela primeira vez.
ms.date: 05/16/2016
ms.openlocfilehash: ced4f1bb17d9e23bf51cc79b5a275cc334cca013
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627581"
---
# <a name="do-bindings-in-classes"></a><span data-ttu-id="69576-103">Associações do em classes</span><span class="sxs-lookup"><span data-stu-id="69576-103">do Bindings in Classes</span></span>

<span data-ttu-id="69576-104">Uma `do` associação em uma definição de classe executa ações quando o objeto é construído ou, para uma `do` associação estática, quando o tipo é usado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="69576-104">A `do` binding in a class definition performs actions when the object is constructed or, for a static `do` binding, when the type is first used.</span></span>

## <a name="syntax"></a><span data-ttu-id="69576-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69576-105">Syntax</span></span>

```fsharp
[static] do expression
```

## <a name="remarks"></a><span data-ttu-id="69576-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="69576-106">Remarks</span></span>

<span data-ttu-id="69576-107">Uma `do` Associação aparece junto com ou após `let` associações, mas antes das definições de membro em uma definição de classe.</span><span class="sxs-lookup"><span data-stu-id="69576-107">A `do` binding appears together with or after `let` bindings but before member definitions in a class definition.</span></span> <span data-ttu-id="69576-108">Embora a `do` palavra-chave seja `do` opcional para associações no nível do módulo, ela não é opcional `do` para associações em uma definição de classe.</span><span class="sxs-lookup"><span data-stu-id="69576-108">Although the `do` keyword is optional for `do` bindings at the module level, it is not optional for `do` bindings in a class definition.</span></span>

<span data-ttu-id="69576-109">Para a construção de todos os objetos de qualquer tipo, associações não estáticas `do` e associações não-estáticas `let` são executadas na ordem em que aparecem na definição de classe.</span><span class="sxs-lookup"><span data-stu-id="69576-109">For the construction of every object of any given type, non-static `do` bindings and non-static `let` bindings are executed in the order in which they appear in the class definition.</span></span> <span data-ttu-id="69576-110">Várias `do` associações podem ocorrer em um tipo.</span><span class="sxs-lookup"><span data-stu-id="69576-110">Multiple `do` bindings can occur in one type.</span></span> <span data-ttu-id="69576-111">As associações não estáticas `let` e as vinculações não-estáticas `do` se tornam o corpo do construtor primário.</span><span class="sxs-lookup"><span data-stu-id="69576-111">The non-static `let` bindings and the non-static `do` bindings become the body of the primary constructor.</span></span> <span data-ttu-id="69576-112">O código na seção de associações não `do` estáticas pode referenciar os parâmetros do construtor primário e quaisquer valores ou funções que estejam definidos `let` na seção associações.</span><span class="sxs-lookup"><span data-stu-id="69576-112">The code in the non-static `do` bindings section can reference the primary constructor parameters and any values or functions that are defined in the `let` bindings section.</span></span>

<span data-ttu-id="69576-113">As associações não `do` estáticas podem acessar os membros da classe, desde que a classe tenha um autoidentifier definido por uma `as` palavra-chave no título da classe e, desde que todos os usos desses membros sejam qualificados com o autoidentificador da classe.</span><span class="sxs-lookup"><span data-stu-id="69576-113">Non-static `do` bindings can access members of the class as long as the class has a self identifier that is defined by an `as` keyword in the class heading, and as long as all uses of those members are qualified with the self identifier for the class.</span></span>

<span data-ttu-id="69576-114">Como `let` as associações inicializam os campos privados de uma classe, o que geralmente é necessário para garantir que os membros se `do` comportem conforme o esperado `let` , as associações geralmente são colocadas após `do` associações para que o código na associação possa Execute com um objeto totalmente inicializado.</span><span class="sxs-lookup"><span data-stu-id="69576-114">Because `let` bindings initialize the private fields of a class, which is often necessary to guarantee that members behave as expected, `do` bindings are usually put after `let` bindings so that code in the `do` binding can execute with a fully initialized object.</span></span> <span data-ttu-id="69576-115">Se o seu código tentar usar um membro antes da conclusão da inicialização, um InvalidOperationException será gerado.</span><span class="sxs-lookup"><span data-stu-id="69576-115">If your code attempts to use a member before the initialization is complete, an InvalidOperationException is raised.</span></span>

<span data-ttu-id="69576-116">As `do` associações estáticas podem referenciar membros estáticos ou campos da classe delimitadora, mas não membros ou campos de instância.</span><span class="sxs-lookup"><span data-stu-id="69576-116">Static `do` bindings can reference static members or fields of the enclosing class but not instance members or fields.</span></span> <span data-ttu-id="69576-117">As `do` associações estáticas tornam-se parte do inicializador estático para a classe, que tem a garantia de executar antes de a classe ser usada pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="69576-117">Static `do` bindings become part of the static initializer for the class, which is guaranteed to execute before the class is first used.</span></span>

<span data-ttu-id="69576-118">Os atributos são ignorados para `do` associações em tipos.</span><span class="sxs-lookup"><span data-stu-id="69576-118">Attributes are ignored for `do` bindings in types.</span></span> <span data-ttu-id="69576-119">Se um atributo for necessário para o código que é executado em `do` uma associação, ele deve ser aplicado ao Construtor principal.</span><span class="sxs-lookup"><span data-stu-id="69576-119">If an attribute is required for code that executes in a `do` binding, it must be applied to the primary constructor.</span></span>

<span data-ttu-id="69576-120">No código a seguir, uma classe tem uma associação `do` estática e uma associação não estática `do` .</span><span class="sxs-lookup"><span data-stu-id="69576-120">In the following code, a class has a static `do` binding and a non-static `do` binding.</span></span> <span data-ttu-id="69576-121">O objeto tem um construtor que tem dois parâmetros, `a` `b`e dois `let` campos privados são definidos nas associações para a classe.</span><span class="sxs-lookup"><span data-stu-id="69576-121">The object has a constructor that has two parameters, `a` and `b`, and two private fields are defined in the `let` bindings for the class.</span></span> <span data-ttu-id="69576-122">Duas propriedades também são definidas.</span><span class="sxs-lookup"><span data-stu-id="69576-122">Two properties are also defined.</span></span> <span data-ttu-id="69576-123">Todos eles estão no escopo na seção de associações não estáticas `do` , como é ilustrado pela linha que imprime todos esses valores.</span><span class="sxs-lookup"><span data-stu-id="69576-123">All of these are in scope in the non-static `do` bindings section, as is illustrated by the line that prints all those values.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

<span data-ttu-id="69576-124">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="69576-124">The output is as follows.</span></span>

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a><span data-ttu-id="69576-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69576-125">See also</span></span>

- [<span data-ttu-id="69576-126">Membros</span><span class="sxs-lookup"><span data-stu-id="69576-126">Members</span></span>](index.md)
- [<span data-ttu-id="69576-127">Classes</span><span class="sxs-lookup"><span data-stu-id="69576-127">Classes</span></span>](../classes.md)
- [<span data-ttu-id="69576-128">Construtores</span><span class="sxs-lookup"><span data-stu-id="69576-128">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="69576-129">`let`Associações em Classes</span><span class="sxs-lookup"><span data-stu-id="69576-129">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
- [<span data-ttu-id="69576-130">`do`Associações</span><span class="sxs-lookup"><span data-stu-id="69576-130">`do` Bindings</span></span>](../functions/do-Bindings.md)
