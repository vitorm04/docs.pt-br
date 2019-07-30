---
title: Delegados
description: Saiba como trabalhar com delegados no F#.
ms.date: 05/16/2016
ms.openlocfilehash: 65875897d5fc4b2ac66f1dfbe913f29fb74137cd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630363"
---
# <a name="delegates"></a><span data-ttu-id="4092a-103">Delegados</span><span class="sxs-lookup"><span data-stu-id="4092a-103">Delegates</span></span>

<span data-ttu-id="4092a-104">Um delegado representa uma chamada de função como um objeto.</span><span class="sxs-lookup"><span data-stu-id="4092a-104">A delegate represents a function call as an object.</span></span> <span data-ttu-id="4092a-105">No F#, normalmente você deve usar valores de função para representar funções como valores de primeira classe; no entanto, os delegados são usados na .NET Framework e, portanto, são necessários quando você interopera com APIs que os esperam.</span><span class="sxs-lookup"><span data-stu-id="4092a-105">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="4092a-106">Eles também podem ser usados durante a criação de bibliotecas criadas para uso de outras linguagens de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4092a-106">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>

## <a name="syntax"></a><span data-ttu-id="4092a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4092a-107">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="4092a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="4092a-108">Remarks</span></span>

<span data-ttu-id="4092a-109">Na sintaxe anterior, `type1` representa o tipo de argumento ou os tipos e `type2` representa o tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="4092a-109">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="4092a-110">Os tipos de argumento que são representados por `type1` são automaticamente na forma curried.</span><span class="sxs-lookup"><span data-stu-id="4092a-110">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="4092a-111">Isso sugere que, para esse tipo, você use um formulário de tupla se os argumentos da função de destino forem na forma curried e uma tupla entre parênteses para argumentos que já estão no formulário de tupla.</span><span class="sxs-lookup"><span data-stu-id="4092a-111">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="4092a-112">O currying automático remove um conjunto de parênteses, deixando um argumento de tupla que corresponda ao método de destino.</span><span class="sxs-lookup"><span data-stu-id="4092a-112">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="4092a-113">Consulte o exemplo de código para a sintaxe que você deve usar em cada caso.</span><span class="sxs-lookup"><span data-stu-id="4092a-113">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="4092a-114">Delegados podem ser anexados F# a valores de função e métodos estáticos ou de instância.</span><span class="sxs-lookup"><span data-stu-id="4092a-114">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="4092a-115">F#os valores de função podem ser passados diretamente como argumentos para delegar construtores.</span><span class="sxs-lookup"><span data-stu-id="4092a-115">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="4092a-116">Para um método estático, você constrói o delegado usando o nome da classe e o método.</span><span class="sxs-lookup"><span data-stu-id="4092a-116">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="4092a-117">Para um método de instância, você fornece a instância de objeto e o método em um argumento.</span><span class="sxs-lookup"><span data-stu-id="4092a-117">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="4092a-118">Em ambos os casos, o operador de acesso`.`de membro () é usado.</span><span class="sxs-lookup"><span data-stu-id="4092a-118">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="4092a-119">O `Invoke` método no tipo delegado chama a função encapsulada.</span><span class="sxs-lookup"><span data-stu-id="4092a-119">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="4092a-120">Além disso, os delegados podem ser passados como valores de função referenciando o nome do método Invoke sem os parênteses.</span><span class="sxs-lookup"><span data-stu-id="4092a-120">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="4092a-121">O código a seguir mostra a sintaxe para criar delegados que representam vários métodos em uma classe.</span><span class="sxs-lookup"><span data-stu-id="4092a-121">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="4092a-122">Dependendo se o método é um método estático ou um método de instância e se ele tem argumentos no formulário de tupla ou no formulário na forma curried, a sintaxe para declarar e atribuir o delegado é um pouco diferente.</span><span class="sxs-lookup"><span data-stu-id="4092a-122">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="4092a-123">O código a seguir mostra algumas das diferentes maneiras que você pode trabalhar com delegados.</span><span class="sxs-lookup"><span data-stu-id="4092a-123">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="4092a-124">A saída do exemplo de código anterior é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="4092a-124">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="4092a-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4092a-125">See also</span></span>

- [<span data-ttu-id="4092a-126">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="4092a-126">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="4092a-127">Parâmetros e Argumentos</span><span class="sxs-lookup"><span data-stu-id="4092a-127">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="4092a-128">Eventos</span><span class="sxs-lookup"><span data-stu-id="4092a-128">Events</span></span>](./members/events.md)
