---
title: "Células de referência (F#)"
description: "Saiba como células de referência do F # são locais de armazenamento permitem criar valores mutáveis com semântica de referência."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 09a0b221-ea21-45c4-bae8-5e4a339750c4
ms.openlocfilehash: c7470c9a36cf2cd24dd89ceffcf6e90c6dc4d2dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="reference-cells"></a><span data-ttu-id="8446b-104">Células de referência</span><span class="sxs-lookup"><span data-stu-id="8446b-104">Reference Cells</span></span>

<span data-ttu-id="8446b-105">*Fazer referência a células* são locais de armazenamento permitem criar valores mutáveis com semântica de referência.</span><span class="sxs-lookup"><span data-stu-id="8446b-105">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="8446b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8446b-106">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="8446b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8446b-107">Remarks</span></span>
<span data-ttu-id="8446b-108">Você usa o operador `ref` antes de um valor para criar uma nova célula de referência que encapsule o valor.</span><span class="sxs-lookup"><span data-stu-id="8446b-108">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="8446b-109">Em seguida, é possível alterar o valor subjacente porque ele é mutável.</span><span class="sxs-lookup"><span data-stu-id="8446b-109">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="8446b-110">Uma célula de referência mantém um valor real. Não é apenas um endereço.</span><span class="sxs-lookup"><span data-stu-id="8446b-110">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="8446b-111">Ao criar uma célula de referência usando o operador `ref`, você cria uma cópia do valor subjacente como um valor mutável encapsulado.</span><span class="sxs-lookup"><span data-stu-id="8446b-111">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="8446b-112">Você pode desreferenciar uma célula de referência usando o operador `!` (bang).</span><span class="sxs-lookup"><span data-stu-id="8446b-112">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="8446b-113">O exemplo de código a seguir ilustra a declaração e o uso das células de referência.</span><span class="sxs-lookup"><span data-stu-id="8446b-113">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="8446b-114">A saída é `50`.</span><span class="sxs-lookup"><span data-stu-id="8446b-114">The output is `50`.</span></span>

<span data-ttu-id="8446b-115">As células de referência são instâncias do tipo de registro genérico `Ref`, declarado da maneira a seguir.</span><span class="sxs-lookup"><span data-stu-id="8446b-115">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="8446b-116">O tipo `'a ref` é um sinônimo de `Ref<'a>`.</span><span class="sxs-lookup"><span data-stu-id="8446b-116">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="8446b-117">O compilador e o IntelliSense no IDE exibem o primeiro para esse tipo, mas a definição subjacente é do último.</span><span class="sxs-lookup"><span data-stu-id="8446b-117">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="8446b-118">O operador `ref` cria uma nova célula de referência.</span><span class="sxs-lookup"><span data-stu-id="8446b-118">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="8446b-119">O código a seguir é a declaração do operador `ref`.</span><span class="sxs-lookup"><span data-stu-id="8446b-119">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="8446b-120">A tabela a seguir mostra os recursos disponíveis na célula de referência.</span><span class="sxs-lookup"><span data-stu-id="8446b-120">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="8446b-121">Operador, membro ou campo</span><span class="sxs-lookup"><span data-stu-id="8446b-121">Operator, member, or field</span></span>|<span data-ttu-id="8446b-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="8446b-122">Description</span></span>|<span data-ttu-id="8446b-123">Tipo</span><span class="sxs-lookup"><span data-stu-id="8446b-123">Type</span></span>|<span data-ttu-id="8446b-124">Definição</span><span class="sxs-lookup"><span data-stu-id="8446b-124">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="8446b-125">`!` (operador de desreferência)</span><span class="sxs-lookup"><span data-stu-id="8446b-125">`!` (dereference operator)</span></span>|<span data-ttu-id="8446b-126">Retorna o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="8446b-126">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="8446b-127">`:=` (operador de atribuição)</span><span class="sxs-lookup"><span data-stu-id="8446b-127">`:=` (assignment operator)</span></span>|<span data-ttu-id="8446b-128">Altera o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="8446b-128">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="8446b-129">`ref` (operador)</span><span class="sxs-lookup"><span data-stu-id="8446b-129">`ref` (operator)</span></span>|<span data-ttu-id="8446b-130">Encapsula um valor em uma nova célula de referência.</span><span class="sxs-lookup"><span data-stu-id="8446b-130">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="8446b-131">`Value` (propriedade)</span><span class="sxs-lookup"><span data-stu-id="8446b-131">`Value` (property)</span></span>|<span data-ttu-id="8446b-132">Obtém ou define o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="8446b-132">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="8446b-133">`contents` (campo de registro)</span><span class="sxs-lookup"><span data-stu-id="8446b-133">`contents` (record field)</span></span>|<span data-ttu-id="8446b-134">Obtém ou define o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="8446b-134">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|
<span data-ttu-id="8446b-135">Existem várias maneiras de acessar o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="8446b-135">There are several ways to access the underlying value.</span></span> <span data-ttu-id="8446b-136">O valor retornado pelo operador de desreferência (`!`) não é um valor atribuível.</span><span class="sxs-lookup"><span data-stu-id="8446b-136">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="8446b-137">Portanto, se estiver modificando o valor subjacente, você deverá usar o operador de atribuição (`:=`) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="8446b-137">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="8446b-138">A propriedade `Value` e o campo `contents` são valores atribuíveis.</span><span class="sxs-lookup"><span data-stu-id="8446b-138">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="8446b-139">Portanto, é possível usá-los para acessar ou alterar o valor subjacente, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8446b-139">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="8446b-140">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="8446b-140">The output is as follows.</span></span>

```
10
10
11
12
```

<span data-ttu-id="8446b-141">O campo `contents` é fornecido para compatibilidade com outras versões do ML e produzirá um aviso durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="8446b-141">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="8446b-142">Para desabilitar o aviso, use a opção do compilador `--mlcompatibility`.</span><span class="sxs-lookup"><span data-stu-id="8446b-142">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="8446b-143">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="8446b-143">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="8446b-144">O código a seguir ilustra o uso das células de referência na passagem de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8446b-144">The following code illustrates the use of reference cells in parameter passing.</span></span> <span data-ttu-id="8446b-145">O tipo de Incrementor tem um método de incremento que aceita um parâmetro que inclui o tipo de parâmetro byref.</span><span class="sxs-lookup"><span data-stu-id="8446b-145">The Incrementor type has a method Increment that takes a parameter that includes byref in the parameter type.</span></span> <span data-ttu-id="8446b-146">O tipo de parâmetro byref indica que os chamadores deverá passar uma célula de referência ou o endereço de uma variável típico do tipo especificado, esse int. caso O código restante ilustra como chamar incremento com ambos os tipos de argumentos e mostra o uso do operador ref em uma variável para criar uma célula de referência (ref myDelta1).</span><span class="sxs-lookup"><span data-stu-id="8446b-146">The byref in the parameter type indicates that callers must pass a reference cell or the address of a typical variable of the specified type, in this case int. The remaining code illustrates how to call Increment with both of these types of arguments, and shows the use of the ref operator on a variable to create a reference cell (ref myDelta1).</span></span> <span data-ttu-id="8446b-147">Em seguida, ele mostra o uso do operador address-of (&amp;) para gerar um argumento apropriado.</span><span class="sxs-lookup"><span data-stu-id="8446b-147">It then shows the use of the address-of operator (&amp;) to generate an appropriate argument.</span></span> <span data-ttu-id="8446b-148">Por fim, o método de incremento é chamado novamente por meio de uma célula de referência que é declarada usando uma associação let.</span><span class="sxs-lookup"><span data-stu-id="8446b-148">Finally, the Increment method is called again by using a reference cell that is declared by using a let binding.</span></span> <span data-ttu-id="8446b-149">A linha final do código demonstra o uso de!</span><span class="sxs-lookup"><span data-stu-id="8446b-149">The final line of code demonstrates the use of the !</span></span> <span data-ttu-id="8446b-150">operador para cancelar a célula de referência para impressão.</span><span class="sxs-lookup"><span data-stu-id="8446b-150">operator to dereference the reference cell for printing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

<span data-ttu-id="8446b-151">Para obter mais informações sobre como passar por referência, consulte [parâmetros e argumentos](parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="8446b-151">For more information about how to pass by reference, see [Parameters and Arguments](parameters-and-arguments.md).</span></span>

>[!NOTE]
<span data-ttu-id="8446b-152">Os programadores c# devem saber que ref funciona de forma diferente em F # do que no c#.</span><span class="sxs-lookup"><span data-stu-id="8446b-152">C# programmers should know that ref works differently in F# than it does in C#.</span></span> <span data-ttu-id="8446b-153">Por exemplo, o uso de ref quando você passar um argumento não tem o mesmo efeito em F # como faz em c#.</span><span class="sxs-lookup"><span data-stu-id="8446b-153">For example, the use of ref when you pass an argument does not have the same effect in F# as it does in C#.</span></span>

## <a name="consuming-c-ref-returns"></a><span data-ttu-id="8446b-154">Consumindo c# `ref` retorna</span><span class="sxs-lookup"><span data-stu-id="8446b-154">Consuming C# `ref` returns</span></span>

<span data-ttu-id="8446b-155">A partir do F # 4.1, você pode consumir `ref` retorna gerado em c#.</span><span class="sxs-lookup"><span data-stu-id="8446b-155">Starting with F# 4.1, you can consume `ref` returns generated in C#.</span></span>  <span data-ttu-id="8446b-156">O resultado de tal chamada é um `byref<_>` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="8446b-156">The result of such a call is a `byref<_>` pointer.</span></span>

<span data-ttu-id="8446b-157">O seguinte método em c#:</span><span class="sxs-lookup"><span data-stu-id="8446b-157">The following C# method:</span></span>

```csharp
namespace RefReturns
{
    public static class RefClass
    {
        public static ref int Find(int val, int[] vals)
        {
            for (int i = 0; i < vals.Length; i++)
            {
                if (vals[i] == val)
                {
                    return ref numbers[i]; // Returns the location, not the value
                }
            }

            throw new IndexOutOfRangeException($"{nameof(number)} not found");
        }
    }
}
```

<span data-ttu-id="8446b-158">Pode ser transparente chamado por F # com nenhuma sintaxe especial:</span><span class="sxs-lookup"><span data-stu-id="8446b-158">Can be transparently called by F# with no special syntax:</span></span>

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

<span data-ttu-id="8446b-159">Também é possível declarar funções que poderiam levar um `ref` retornar como entrada, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8446b-159">You can also declare functions which could take a `ref` return as input, for example:</span></span>

```fsharp
let f (x: byref<int>) = &x
```

<span data-ttu-id="8446b-160">Atualmente, não há nenhuma maneira de gerar um `ref` retorno em F #, que pode ser consumido em c#.</span><span class="sxs-lookup"><span data-stu-id="8446b-160">There is currently no way to generate a `ref` return in F# which could be consumed in C#.</span></span>

## <a name="see-also"></a><span data-ttu-id="8446b-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8446b-161">See Also</span></span>
[<span data-ttu-id="8446b-162">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="8446b-162">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="8446b-163">Parâmetros e Argumentos</span><span class="sxs-lookup"><span data-stu-id="8446b-163">Parameters and Arguments</span></span>](parameters-and-arguments.md)

[<span data-ttu-id="8446b-164">Referência de Símbolos e Operadores</span><span class="sxs-lookup"><span data-stu-id="8446b-164">Symbol and Operator Reference</span></span>](symbol-and-operator-reference/index.md)
