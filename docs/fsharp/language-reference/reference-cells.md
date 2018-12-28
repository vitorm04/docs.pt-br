---
title: Células de referência
description: Saiba como F# células de referência são locais de armazenamento que permitem criar valores mutáveis com semântica de referência.
ms.date: 05/16/2016
ms.openlocfilehash: e4fcd3cf1abcf5f5e3b4d5439c9215b79ff8dbcd
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612758"
---
# <a name="reference-cells"></a><span data-ttu-id="d8df5-103">Células de referência</span><span class="sxs-lookup"><span data-stu-id="d8df5-103">Reference Cells</span></span>

<span data-ttu-id="d8df5-104">*Células de referência* são locais de armazenamento que permitem criar valores mutáveis com semântica de referência.</span><span class="sxs-lookup"><span data-stu-id="d8df5-104">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="d8df5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8df5-105">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="d8df5-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="d8df5-106">Remarks</span></span>

<span data-ttu-id="d8df5-107">Você usa o operador `ref` antes de um valor para criar uma nova célula de referência que encapsule o valor.</span><span class="sxs-lookup"><span data-stu-id="d8df5-107">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="d8df5-108">Em seguida, é possível alterar o valor subjacente porque ele é mutável.</span><span class="sxs-lookup"><span data-stu-id="d8df5-108">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="d8df5-109">Uma célula de referência mantém um valor real. Não é apenas um endereço.</span><span class="sxs-lookup"><span data-stu-id="d8df5-109">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="d8df5-110">Ao criar uma célula de referência usando o operador `ref`, você cria uma cópia do valor subjacente como um valor mutável encapsulado.</span><span class="sxs-lookup"><span data-stu-id="d8df5-110">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="d8df5-111">Você pode desreferenciar uma célula de referência usando o operador `!` (bang).</span><span class="sxs-lookup"><span data-stu-id="d8df5-111">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="d8df5-112">O exemplo de código a seguir ilustra a declaração e o uso das células de referência.</span><span class="sxs-lookup"><span data-stu-id="d8df5-112">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="d8df5-113">A saída é `50`.</span><span class="sxs-lookup"><span data-stu-id="d8df5-113">The output is `50`.</span></span>

<span data-ttu-id="d8df5-114">As células de referência são instâncias do tipo de registro genérico `Ref`, declarado da maneira a seguir.</span><span class="sxs-lookup"><span data-stu-id="d8df5-114">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="d8df5-115">O tipo `'a ref` é um sinônimo de `Ref<'a>`.</span><span class="sxs-lookup"><span data-stu-id="d8df5-115">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="d8df5-116">O compilador e o IntelliSense no IDE exibem o primeiro para esse tipo, mas a definição subjacente é do último.</span><span class="sxs-lookup"><span data-stu-id="d8df5-116">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="d8df5-117">O operador `ref` cria uma nova célula de referência.</span><span class="sxs-lookup"><span data-stu-id="d8df5-117">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="d8df5-118">O código a seguir é a declaração do operador `ref`.</span><span class="sxs-lookup"><span data-stu-id="d8df5-118">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="d8df5-119">A tabela a seguir mostra os recursos disponíveis na célula de referência.</span><span class="sxs-lookup"><span data-stu-id="d8df5-119">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="d8df5-120">Operador, membro ou campo</span><span class="sxs-lookup"><span data-stu-id="d8df5-120">Operator, member, or field</span></span>|<span data-ttu-id="d8df5-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8df5-121">Description</span></span>|<span data-ttu-id="d8df5-122">Tipo</span><span class="sxs-lookup"><span data-stu-id="d8df5-122">Type</span></span>|<span data-ttu-id="d8df5-123">Definição</span><span class="sxs-lookup"><span data-stu-id="d8df5-123">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="d8df5-124">`!` (operador de desreferência)</span><span class="sxs-lookup"><span data-stu-id="d8df5-124">`!` (dereference operator)</span></span>|<span data-ttu-id="d8df5-125">Retorna o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="d8df5-125">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="d8df5-126">`:=` (operador de atribuição)</span><span class="sxs-lookup"><span data-stu-id="d8df5-126">`:=` (assignment operator)</span></span>|<span data-ttu-id="d8df5-127">Altera o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="d8df5-127">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="d8df5-128">`ref` (operador)</span><span class="sxs-lookup"><span data-stu-id="d8df5-128">`ref` (operator)</span></span>|<span data-ttu-id="d8df5-129">Encapsula um valor em uma nova célula de referência.</span><span class="sxs-lookup"><span data-stu-id="d8df5-129">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="d8df5-130">`Value` (propriedade)</span><span class="sxs-lookup"><span data-stu-id="d8df5-130">`Value` (property)</span></span>|<span data-ttu-id="d8df5-131">Obtém ou define o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="d8df5-131">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="d8df5-132">`contents` (campo de registro)</span><span class="sxs-lookup"><span data-stu-id="d8df5-132">`contents` (record field)</span></span>|<span data-ttu-id="d8df5-133">Obtém ou define o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="d8df5-133">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|

<span data-ttu-id="d8df5-134">Existem várias maneiras de acessar o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="d8df5-134">There are several ways to access the underlying value.</span></span> <span data-ttu-id="d8df5-135">O valor retornado pelo operador de desreferência (`!`) não é um valor atribuível.</span><span class="sxs-lookup"><span data-stu-id="d8df5-135">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="d8df5-136">Portanto, se estiver modificando o valor subjacente, você deverá usar o operador de atribuição (`:=`) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="d8df5-136">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="d8df5-137">A propriedade `Value` e o campo `contents` são valores atribuíveis.</span><span class="sxs-lookup"><span data-stu-id="d8df5-137">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="d8df5-138">Portanto, é possível usá-los para acessar ou alterar o valor subjacente, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="d8df5-138">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="d8df5-139">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="d8df5-139">The output is as follows.</span></span>

```
10
10
11
12
```

<span data-ttu-id="d8df5-140">O campo `contents` é fornecido para compatibilidade com outras versões do ML e produzirá um aviso durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="d8df5-140">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="d8df5-141">Para desabilitar o aviso, use a opção do compilador `--mlcompatibility`.</span><span class="sxs-lookup"><span data-stu-id="d8df5-141">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="d8df5-142">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="d8df5-142">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="d8df5-143">C#os programadores devem saber que `ref` em C# não é a mesma coisa que `ref` em F#.</span><span class="sxs-lookup"><span data-stu-id="d8df5-143">C# programmers should know that `ref` in C# is not the same thing as `ref` in F#.</span></span> <span data-ttu-id="d8df5-144">O equivalente construções em F# são [byrefs](byrefs.md), que são um conceito diferente das células de referência.</span><span class="sxs-lookup"><span data-stu-id="d8df5-144">The equivalent constructs in F# are [byrefs](byrefs.md), which are a different concept from reference cells.</span></span>

<span data-ttu-id="d8df5-145">Valores marcados como `mutable`pode ser elevada automaticamente a `'a ref` se capturados por um fechamento; veja [valores](values/index.md).</span><span class="sxs-lookup"><span data-stu-id="d8df5-145">Values marked as `mutable`may be automatically promoted to `'a ref` if captured by a closure; see [Values](values/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d8df5-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8df5-146">See also</span></span>

- [<span data-ttu-id="d8df5-147">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="d8df5-147">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="d8df5-148">Parâmetros e Argumentos</span><span class="sxs-lookup"><span data-stu-id="d8df5-148">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="d8df5-149">Referência de Símbolos e Operadores</span><span class="sxs-lookup"><span data-stu-id="d8df5-149">Symbol and Operator Reference</span></span>](symbol-and-operator-reference/index.md)
- [<span data-ttu-id="d8df5-150">Valores</span><span class="sxs-lookup"><span data-stu-id="d8df5-150">Values</span></span>](values/index.md)
