---
title: Propriedades indexadas
description: Saiba mais sobre propriedades indexadas no F#, que permitem o acesso do tipo matriz a dados ordenados.
ms.date: 10/17/2018
ms.openlocfilehash: 379417e31b8e178d8c939e5b23dc144bfb17e562
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627564"
---
# <a name="indexed-properties"></a><span data-ttu-id="dfb32-103">Propriedades indexadas</span><span class="sxs-lookup"><span data-stu-id="dfb32-103">Indexed Properties</span></span>

<span data-ttu-id="dfb32-104">Ao definir uma classe que abstrai os dados ordenados, às vezes pode ser útil fornecer acesso indexado a esses dados sem expor a implementação subjacente.</span><span class="sxs-lookup"><span data-stu-id="dfb32-104">When defining a class that abstracts over ordered data, it can sometimes be helpful to provide indexed access to that data without exposing the underlying implementation.</span></span> <span data-ttu-id="dfb32-105">Isso é feito com o `Item` membro.</span><span class="sxs-lookup"><span data-stu-id="dfb32-105">This is done with the `Item` member.</span></span>

## <a name="syntax"></a><span data-ttu-id="dfb32-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dfb32-106">Syntax</span></span>

```fsharp
// Indexed property that can be read and written to
member self-identifier.Item
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property can only be read
member self-identifier.Item
    with get(index-values) =
        get-member-body

// Indexed property that can only be set
member self-identifier.Item
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a><span data-ttu-id="dfb32-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="dfb32-107">Remarks</span></span>

<span data-ttu-id="dfb32-108">Os formulários da sintaxe anterior mostram como `get` definir propriedades indexadas que têm um e um `set` método, só têm um `get` método ou só têm um `set` método.</span><span class="sxs-lookup"><span data-stu-id="dfb32-108">The forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="dfb32-109">Você também pode combinar a sintaxe mostrada somente para get e a sintaxe mostrada somente para Set e produzir uma propriedade que tenha Get e Set.</span><span class="sxs-lookup"><span data-stu-id="dfb32-109">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="dfb32-110">Este último formulário permite que você coloque atributos e modificadores de acessibilidade diferentes nos métodos get e Set.</span><span class="sxs-lookup"><span data-stu-id="dfb32-110">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="dfb32-111">Usando o nome `Item`, o compilador trata a propriedade como uma propriedade indexada padrão.</span><span class="sxs-lookup"><span data-stu-id="dfb32-111">By using the name `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="dfb32-112">Uma *propriedade indexada padrão* é uma propriedade que você pode acessar usando a sintaxe do tipo matriz na instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="dfb32-112">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="dfb32-113">Por exemplo, se `o` for um objeto do tipo que define essa propriedade, a sintaxe `o.[index]` será usada para acessar a propriedade.</span><span class="sxs-lookup"><span data-stu-id="dfb32-113">For example, if `o` is an object of the type that defines this property, the syntax `o.[index]` is used to access the property.</span></span>

<span data-ttu-id="dfb32-114">A sintaxe para acessar uma propriedade indexada não padrão é fornecer o nome da propriedade e o índice entre parênteses, assim como um membro regular.</span><span class="sxs-lookup"><span data-stu-id="dfb32-114">The syntax for accessing a non-default indexed property is to provide the name of the property and the index in parentheses, just like a regular member.</span></span> <span data-ttu-id="dfb32-115">Por exemplo, se a propriedade on `o` for chamada `Ordinal`, você escreverá `o.Ordinal(index)` para acessá-la.</span><span class="sxs-lookup"><span data-stu-id="dfb32-115">For example, if the property on `o` is called `Ordinal`, you write `o.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="dfb32-116">Independentemente do formulário usado, você sempre deve usar o formulário na forma curried para o método set em uma propriedade indexada.</span><span class="sxs-lookup"><span data-stu-id="dfb32-116">Regardless of which form you use, you should always use the curried form for the set method on an indexed property.</span></span> <span data-ttu-id="dfb32-117">Para obter informações sobre as funções do na forma curried, consulte [funções](../functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="dfb32-117">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="dfb32-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dfb32-118">Example</span></span>

<span data-ttu-id="dfb32-119">O exemplo de código a seguir ilustra a definição e o uso de propriedades indexadas padrão e não padrão que têm métodos get e Set.</span><span class="sxs-lookup"><span data-stu-id="dfb32-119">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="dfb32-120">Saída</span><span class="sxs-lookup"><span data-stu-id="dfb32-120">Output</span></span>

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a><span data-ttu-id="dfb32-121">Propriedades indexadas com vários valores de índice</span><span class="sxs-lookup"><span data-stu-id="dfb32-121">Indexed Properties with multiple index values</span></span>

<span data-ttu-id="dfb32-122">As propriedades indexadas podem ter mais de um valor de índice.</span><span class="sxs-lookup"><span data-stu-id="dfb32-122">Indexed properties can have more than one index value.</span></span> <span data-ttu-id="dfb32-123">Nesse caso, os valores são separados por vírgulas quando a propriedade é usada.</span><span class="sxs-lookup"><span data-stu-id="dfb32-123">In that case, the values are separated by commas when the property is used.</span></span> <span data-ttu-id="dfb32-124">O método set em tal propriedade deve ter dois argumentos na forma curried, o primeiro deles é uma tupla que contém as chaves e o segundo é o valor a ser definido.</span><span class="sxs-lookup"><span data-stu-id="dfb32-124">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value to set.</span></span>

<span data-ttu-id="dfb32-125">O código a seguir demonstra o uso de uma propriedade indexada com vários valores de índice.</span><span class="sxs-lookup"><span data-stu-id="dfb32-125">The following code demonstrates the use of an indexed property with multiple index values.</span></span>

```fsharp
open System.Collections.Generic

/// Basic implementation of a sparse matrix based on a dictionary
type SparseMatrix() =
    let table = new Dictionary<(int * int), float>()
    member __.Item
        // Because the key is comprised of two values, 'get' has two index values
        with get(key1, key2) = table.[(key1, key2)]

        // 'set' has two index values and a new value to place in the key's position
        and set (key1, key2) value = table.[(key1, key2)] <- value

let sm = new SparseMatrix()
for i in 1..1000 do
    sm.[i, i] <- float i * float i
```

## <a name="see-also"></a><span data-ttu-id="dfb32-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfb32-126">See also</span></span>

- [<span data-ttu-id="dfb32-127">Membros</span><span class="sxs-lookup"><span data-stu-id="dfb32-127">Members</span></span>](index.md)
