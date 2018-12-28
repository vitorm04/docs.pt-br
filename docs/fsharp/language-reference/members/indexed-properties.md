---
title: Propriedades indexadas
description: Saiba mais sobre as propriedades indexadas no F#, que permitem acesso de matriz aos dados ordenados.
ms.date: 10/17/2018
ms.openlocfilehash: 3817290505339803814e981cd5408cd4df6bd283
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611770"
---
# <a name="indexed-properties"></a><span data-ttu-id="a0129-103">Propriedades indexadas</span><span class="sxs-lookup"><span data-stu-id="a0129-103">Indexed Properties</span></span>

<span data-ttu-id="a0129-104">Ao definir uma classe que abstrai sobre dados ordenados, às vezes, pode ser útil fornecer acesso indexado para dados sem expor a implementação subjacente.</span><span class="sxs-lookup"><span data-stu-id="a0129-104">When defining a class that abstracts over ordered data, it can sometimes be helpful to provide indexed access to that data without exposing the underlying implementation.</span></span> <span data-ttu-id="a0129-105">Isso é feito com o `Index` membro.</span><span class="sxs-lookup"><span data-stu-id="a0129-105">This is done with the `Index` member.</span></span>

## <a name="syntax"></a><span data-ttu-id="a0129-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0129-106">Syntax</span></span>

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.Index
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property with get only
member self-identifier.Index
    with get(index-values) =
        get-member-body

// Indexed property that has set only.
member self-identifier.Index
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a><span data-ttu-id="a0129-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a0129-107">Remarks</span></span>

<span data-ttu-id="a0129-108">As formas de sintaxe anterior mostram como definir as propriedades indexadas com as duas uma `get` e uma `set` método, ter um `get` somente, no método ou tem um `set` somente no método.</span><span class="sxs-lookup"><span data-stu-id="a0129-108">The forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="a0129-109">Você também pode combinar dois a sintaxe mostrada para somente get e a sintaxe mostrada para apenas o conjunto e produzir uma propriedade que tem get e set.</span><span class="sxs-lookup"><span data-stu-id="a0129-109">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="a0129-110">Este último formulário permite que você coloque os modificadores de acessibilidade diferente e atributos em get e métodos definidos.</span><span class="sxs-lookup"><span data-stu-id="a0129-110">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="a0129-111">Usando o nome `Item`, o compilador trata a propriedade como uma propriedade indexada padrão.</span><span class="sxs-lookup"><span data-stu-id="a0129-111">By using the name `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="a0129-112">Um *propriedade default indexada* é uma propriedade que você pode acessar usando a sintaxe de matriz na instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="a0129-112">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="a0129-113">Por exemplo, se `o` é um objeto do tipo que define essa propriedade, a sintaxe `o.[index]` é usado para acessar a propriedade.</span><span class="sxs-lookup"><span data-stu-id="a0129-113">For example, if `o` is an object of the type that defines this property, the syntax `o.[index]` is used to access the property.</span></span>

<span data-ttu-id="a0129-114">A sintaxe para acessar uma propriedade indexada de não-padrão é fornecer o nome da propriedade e o índice entre parênteses, assim como um membro regular.</span><span class="sxs-lookup"><span data-stu-id="a0129-114">The syntax for accessing a non-default indexed property is to provide the name of the property and the index in parentheses, just like a regular member.</span></span> <span data-ttu-id="a0129-115">Por exemplo, se a propriedade em `o` é chamado `Ordinal`, você escreve `o.Ordinal(index)` para acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="a0129-115">For example, if the property on `o` is called `Ordinal`, you write `o.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="a0129-116">Independentemente de qual formulário usar, você sempre deve usar o formulário na forma curried para o método set em uma propriedade indexada.</span><span class="sxs-lookup"><span data-stu-id="a0129-116">Regardless of which form you use, you should always use the curried form for the set method on an indexed property.</span></span> <span data-ttu-id="a0129-117">Para obter informações sobre funções via currying, consulte [funções](../functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="a0129-117">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="a0129-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a0129-118">Example</span></span>

<span data-ttu-id="a0129-119">O exemplo de código a seguir ilustra a definição e uso do padrão e propriedades indexadas de não-padrão obter e definir métodos.</span><span class="sxs-lookup"><span data-stu-id="a0129-119">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="a0129-120">Saída</span><span class="sxs-lookup"><span data-stu-id="a0129-120">Output</span></span>

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a><span data-ttu-id="a0129-121">Propriedades indexadas com diversas variáveis de índice</span><span class="sxs-lookup"><span data-stu-id="a0129-121">Indexed Properties with Multiple Index Variables</span></span>

<span data-ttu-id="a0129-122">Propriedades indexadas podem ter mais de uma variável de índice.</span><span class="sxs-lookup"><span data-stu-id="a0129-122">Indexed properties can have more than one index variable.</span></span> <span data-ttu-id="a0129-123">Nesse caso, as variáveis são separadas por vírgulas quando a propriedade é usada.</span><span class="sxs-lookup"><span data-stu-id="a0129-123">In that case, the variables are separated by commas when the property is used.</span></span> <span data-ttu-id="a0129-124">O método set em tal propriedade deve ter dois argumentos na forma curried, o primeiro deles é uma tupla que contém as chaves e o segundo é o valor que está sendo definido.</span><span class="sxs-lookup"><span data-stu-id="a0129-124">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value being set.</span></span>

<span data-ttu-id="a0129-125">O código a seguir demonstra o uso de uma propriedade indexada com diversas variáveis de índice.</span><span class="sxs-lookup"><span data-stu-id="a0129-125">The following code demonstrates the use of an indexed property with multiple index variables.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]

## <a name="see-also"></a><span data-ttu-id="a0129-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0129-126">See also</span></span>

- [<span data-ttu-id="a0129-127">Membros</span><span class="sxs-lookup"><span data-stu-id="a0129-127">Members</span></span>](index.md)