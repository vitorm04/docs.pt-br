---
title: Propriedades indexadas (F#)
description: 'Saiba mais sobre as propriedades indexadas do F #, que são propriedades que fornecem acesso de matriz aos dados ordenados.'
ms.date: 05/16/2016
ms.openlocfilehash: e56e4e2ea3f35df4c8ec46012357242cb6ce69f3
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43749587"
---
# <a name="indexed-properties"></a><span data-ttu-id="7564c-103">Propriedades indexadas</span><span class="sxs-lookup"><span data-stu-id="7564c-103">Indexed Properties</span></span>

<span data-ttu-id="7564c-104">*Propriedades indexadas* são ordenadas de propriedades que fornecem acesso de matriz aos dados.</span><span class="sxs-lookup"><span data-stu-id="7564c-104">*Indexed properties* are properties that provide array-like access to ordered data.</span></span> <span data-ttu-id="7564c-105">Eles vêm em três formas:</span><span class="sxs-lookup"><span data-stu-id="7564c-105">They come in three forms:</span></span>

* `Item`
* `Ordinal`
* `Cardinal`

<span data-ttu-id="7564c-106">Um membro em F # deve ser nomeado um desses três nomes para fornecer acesso de matriz.</span><span class="sxs-lookup"><span data-stu-id="7564c-106">An F# member must be named one of these three names to provide array-like access.</span></span> <span data-ttu-id="7564c-107">`IndexerName` é usado para representar qualquer uma das três opções abaixo:</span><span class="sxs-lookup"><span data-stu-id="7564c-107">`IndexerName` is used to represent any of the three options below:</span></span>

## <a name="syntax"></a><span data-ttu-id="7564c-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7564c-108">Syntax</span></span>

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.IndexerName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.IndexerName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.IndexerName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.IndexerName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a><span data-ttu-id="7564c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="7564c-109">Remarks</span></span>

<span data-ttu-id="7564c-110">As formas de sintaxe anterior mostram como definir as propriedades indexadas com as duas uma `get` e uma `set` método, ter um `get` somente, no método ou tem um `set` somente no método.</span><span class="sxs-lookup"><span data-stu-id="7564c-110">The forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="7564c-111">Você também pode combinar dois a sintaxe mostrada para somente get e a sintaxe mostrada para apenas o conjunto e produzir uma propriedade que tem get e set.</span><span class="sxs-lookup"><span data-stu-id="7564c-111">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="7564c-112">Este último formulário permite que você coloque os modificadores de acessibilidade diferente e atributos em get e métodos definidos.</span><span class="sxs-lookup"><span data-stu-id="7564c-112">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="7564c-113">Quando o *IndexerName* é `Item`, o compilador trata a propriedade como uma propriedade indexada padrão.</span><span class="sxs-lookup"><span data-stu-id="7564c-113">When the *IndexerName* is `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="7564c-114">Um *propriedade default indexada* é uma propriedade que você pode acessar usando a sintaxe de matriz na instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="7564c-114">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="7564c-115">Por exemplo, se `obj` é um objeto do tipo que define essa propriedade, a sintaxe `obj.[index]` é usado para acessar a propriedade.</span><span class="sxs-lookup"><span data-stu-id="7564c-115">For example, if `obj` is an object of the type that defines this property, the syntax `obj.[index]` is used to access the property.</span></span>

<span data-ttu-id="7564c-116">A sintaxe para acessar uma propriedade indexada de não-padrão é fornecer o nome da propriedade e o índice entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="7564c-116">The syntax for accessing a nondefault indexed property is to provide the name of the property and the index in parentheses.</span></span> <span data-ttu-id="7564c-117">Por exemplo, se a propriedade é `Ordinal`, você escreve `obj.Ordinal(index)` para acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="7564c-117">For example, if the property is `Ordinal`, you write `obj.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="7564c-118">Independentemente de qual formulário usar, você sempre deve usar o formulário na forma curried para o `set` método em uma propriedade indexada.</span><span class="sxs-lookup"><span data-stu-id="7564c-118">Regardless of which form you use, you should always use the curried form for the `set` method on an indexed property.</span></span> <span data-ttu-id="7564c-119">Para obter informações sobre funções via currying, consulte [funções](../functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="7564c-119">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="7564c-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7564c-120">Example</span></span>

<span data-ttu-id="7564c-121">O exemplo de código a seguir ilustra a definição e uso do padrão e propriedades indexadas de não-padrão obter e definir métodos.</span><span class="sxs-lookup"><span data-stu-id="7564c-121">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="7564c-122">Saída</span><span class="sxs-lookup"><span data-stu-id="7564c-122">Output</span></span>

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a><span data-ttu-id="7564c-123">Propriedades indexadas com diversas variáveis de índice</span><span class="sxs-lookup"><span data-stu-id="7564c-123">Indexed Properties with Multiple Index Variables</span></span>

<span data-ttu-id="7564c-124">Propriedades indexadas podem ter mais de uma variável de índice.</span><span class="sxs-lookup"><span data-stu-id="7564c-124">Indexed properties can have more than one index variable.</span></span> <span data-ttu-id="7564c-125">Nesse caso, as variáveis são separadas por vírgulas quando a propriedade é usada.</span><span class="sxs-lookup"><span data-stu-id="7564c-125">In that case, the variables are separated by commas when the property is used.</span></span> <span data-ttu-id="7564c-126">O método set em tal propriedade deve ter dois argumentos na forma curried, o primeiro deles é uma tupla que contém as chaves e o segundo é o valor que está sendo definido.</span><span class="sxs-lookup"><span data-stu-id="7564c-126">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value being set.</span></span>

<span data-ttu-id="7564c-127">O código a seguir demonstra o uso de uma propriedade indexada com diversas variáveis de índice.</span><span class="sxs-lookup"><span data-stu-id="7564c-127">The following code demonstrates the use of an indexed property with multiple index variables.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]

## <a name="see-also"></a><span data-ttu-id="7564c-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7564c-128">See also</span></span>

- [<span data-ttu-id="7564c-129">Membros</span><span class="sxs-lookup"><span data-stu-id="7564c-129">Members</span></span>](index.md)
