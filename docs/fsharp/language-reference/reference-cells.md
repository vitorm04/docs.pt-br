---
title: Células de referência (F#)
description: 'Saiba como células de referência em F # são locais de armazenamento que permitem criar valores mutáveis com semântica de referência.'
ms.date: 05/16/2016
ms.openlocfilehash: e2e1a91c62fd76e4992bc5ae11bb672766850718
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079290"
---
# <a name="reference-cells"></a><span data-ttu-id="37cc1-103">Células de referência</span><span class="sxs-lookup"><span data-stu-id="37cc1-103">Reference Cells</span></span>

<span data-ttu-id="37cc1-104">*Células de referência* são locais de armazenamento que permitem criar valores mutáveis com semântica de referência.</span><span class="sxs-lookup"><span data-stu-id="37cc1-104">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="37cc1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37cc1-105">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="37cc1-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="37cc1-106">Remarks</span></span>

<span data-ttu-id="37cc1-107">Você usa o operador `ref` antes de um valor para criar uma nova célula de referência que encapsule o valor.</span><span class="sxs-lookup"><span data-stu-id="37cc1-107">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="37cc1-108">Em seguida, é possível alterar o valor subjacente porque ele é mutável.</span><span class="sxs-lookup"><span data-stu-id="37cc1-108">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="37cc1-109">Uma célula de referência mantém um valor real. Não é apenas um endereço.</span><span class="sxs-lookup"><span data-stu-id="37cc1-109">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="37cc1-110">Ao criar uma célula de referência usando o operador `ref`, você cria uma cópia do valor subjacente como um valor mutável encapsulado.</span><span class="sxs-lookup"><span data-stu-id="37cc1-110">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="37cc1-111">Você pode desreferenciar uma célula de referência usando o operador `!` (bang).</span><span class="sxs-lookup"><span data-stu-id="37cc1-111">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="37cc1-112">O exemplo de código a seguir ilustra a declaração e o uso das células de referência.</span><span class="sxs-lookup"><span data-stu-id="37cc1-112">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="37cc1-113">A saída é `50`.</span><span class="sxs-lookup"><span data-stu-id="37cc1-113">The output is `50`.</span></span>

<span data-ttu-id="37cc1-114">As células de referência são instâncias do tipo de registro genérico `Ref`, declarado da maneira a seguir.</span><span class="sxs-lookup"><span data-stu-id="37cc1-114">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="37cc1-115">O tipo `'a ref` é um sinônimo de `Ref<'a>`.</span><span class="sxs-lookup"><span data-stu-id="37cc1-115">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="37cc1-116">O compilador e o IntelliSense no IDE exibem o primeiro para esse tipo, mas a definição subjacente é do último.</span><span class="sxs-lookup"><span data-stu-id="37cc1-116">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="37cc1-117">O operador `ref` cria uma nova célula de referência.</span><span class="sxs-lookup"><span data-stu-id="37cc1-117">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="37cc1-118">O código a seguir é a declaração do operador `ref`.</span><span class="sxs-lookup"><span data-stu-id="37cc1-118">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="37cc1-119">A tabela a seguir mostra os recursos disponíveis na célula de referência.</span><span class="sxs-lookup"><span data-stu-id="37cc1-119">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="37cc1-120">Operador, membro ou campo</span><span class="sxs-lookup"><span data-stu-id="37cc1-120">Operator, member, or field</span></span>|<span data-ttu-id="37cc1-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="37cc1-121">Description</span></span>|<span data-ttu-id="37cc1-122">Tipo</span><span class="sxs-lookup"><span data-stu-id="37cc1-122">Type</span></span>|<span data-ttu-id="37cc1-123">Definição</span><span class="sxs-lookup"><span data-stu-id="37cc1-123">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="37cc1-124">`!` (operador de desreferência)</span><span class="sxs-lookup"><span data-stu-id="37cc1-124">`!` (dereference operator)</span></span>|<span data-ttu-id="37cc1-125">Retorna o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="37cc1-125">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="37cc1-126">`:=` (operador de atribuição)</span><span class="sxs-lookup"><span data-stu-id="37cc1-126">`:=` (assignment operator)</span></span>|<span data-ttu-id="37cc1-127">Altera o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="37cc1-127">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="37cc1-128">`ref` (operador)</span><span class="sxs-lookup"><span data-stu-id="37cc1-128">`ref` (operator)</span></span>|<span data-ttu-id="37cc1-129">Encapsula um valor em uma nova célula de referência.</span><span class="sxs-lookup"><span data-stu-id="37cc1-129">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="37cc1-130">`Value` (propriedade)</span><span class="sxs-lookup"><span data-stu-id="37cc1-130">`Value` (property)</span></span>|<span data-ttu-id="37cc1-131">Obtém ou define o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="37cc1-131">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="37cc1-132">`contents` (campo de registro)</span><span class="sxs-lookup"><span data-stu-id="37cc1-132">`contents` (record field)</span></span>|<span data-ttu-id="37cc1-133">Obtém ou define o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="37cc1-133">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|
<span data-ttu-id="37cc1-134">Existem várias maneiras de acessar o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="37cc1-134">There are several ways to access the underlying value.</span></span> <span data-ttu-id="37cc1-135">O valor retornado pelo operador de desreferência (`!`) não é um valor atribuível.</span><span class="sxs-lookup"><span data-stu-id="37cc1-135">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="37cc1-136">Portanto, se estiver modificando o valor subjacente, você deverá usar o operador de atribuição (`:=`) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="37cc1-136">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="37cc1-137">A propriedade `Value` e o campo `contents` são valores atribuíveis.</span><span class="sxs-lookup"><span data-stu-id="37cc1-137">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="37cc1-138">Portanto, é possível usá-los para acessar ou alterar o valor subjacente, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="37cc1-138">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="37cc1-139">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="37cc1-139">The output is as follows.</span></span>

```
10
10
11
12
```

<span data-ttu-id="37cc1-140">O campo `contents` é fornecido para compatibilidade com outras versões do ML e produzirá um aviso durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="37cc1-140">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="37cc1-141">Para desabilitar o aviso, use a opção do compilador `--mlcompatibility`.</span><span class="sxs-lookup"><span data-stu-id="37cc1-141">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="37cc1-142">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="37cc1-142">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="37cc1-143">Programadores de c# devem saber que `ref` em c# não é a mesma coisa que `ref` em F #.</span><span class="sxs-lookup"><span data-stu-id="37cc1-143">C# programmers should know that `ref` in C# is not the same thing as `ref` in F#.</span></span> <span data-ttu-id="37cc1-144">As construções equivalentes em F # são [byrefs](byrefs.md), que são um conceito diferente das células de referência.</span><span class="sxs-lookup"><span data-stu-id="37cc1-144">The equivalent constructs in F# are [byrefs](byrefs.md), which are a different concept from reference cells.</span></span>

<span data-ttu-id="37cc1-145">Valores marcados como `mutable`pode ser elevada automaticamente a `'a ref` se capturados por um fechamento; veja [valores](values/index.md).</span><span class="sxs-lookup"><span data-stu-id="37cc1-145">Values marked as `mutable`may be automatically promoted to `'a ref` if captured by a closure; see [Values](values/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="37cc1-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37cc1-146">See also</span></span>

- [<span data-ttu-id="37cc1-147">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="37cc1-147">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="37cc1-148">Parâmetros e Argumentos</span><span class="sxs-lookup"><span data-stu-id="37cc1-148">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="37cc1-149">Referência de Símbolos e Operadores</span><span class="sxs-lookup"><span data-stu-id="37cc1-149">Symbol and Operator Reference</span></span>](symbol-and-operator-reference/index.md)
- [<span data-ttu-id="37cc1-150">Valores</span><span class="sxs-lookup"><span data-stu-id="37cc1-150">Values</span></span>](values/index.md)
