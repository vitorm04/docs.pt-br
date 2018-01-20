---
title: Registros (F#)
description: "Saiba como registros de F # representam agregações simples de valores nomeados, opcionalmente com membros."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3a3701ea-4308-4fa1-9b5c-b955c470f17a
ms.openlocfilehash: 478ab74ad32cc6e53daffd1bd6229729149d2a1e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="records"></a><span data-ttu-id="c18d7-104">Registros</span><span class="sxs-lookup"><span data-stu-id="c18d7-104">Records</span></span>

<span data-ttu-id="c18d7-105">Registros representam agregações simples de valores nomeados, opcionalmente com membros.</span><span class="sxs-lookup"><span data-stu-id="c18d7-105">Records represent simple aggregates of named values, optionally with members.</span></span>  <span data-ttu-id="c18d7-106">A partir do F # 4.1, eles podem ser tipos de estruturas ou referência.</span><span class="sxs-lookup"><span data-stu-id="c18d7-106">Starting with F# 4.1, they can either be structs or reference types.</span></span>  <span data-ttu-id="c18d7-107">Eles são tipos de referência por padrão.</span><span class="sxs-lookup"><span data-stu-id="c18d7-107">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="c18d7-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c18d7-108">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename = {
    [ mutable ] label1 : type1;
    [ mutable ] label2 : type2;
    ...
}
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="c18d7-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c18d7-109">Remarks</span></span>
<span data-ttu-id="c18d7-110">Na sintaxe anterior, *typename* é o nome do tipo de registro *label1* e *label2* são nomes de valores, conhecidos como *rótulos*, e *type1* e *type2* são os tipos desses valores.</span><span class="sxs-lookup"><span data-stu-id="c18d7-110">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="c18d7-111">*lista de membros* é a lista opcional de membros para o tipo.</span><span class="sxs-lookup"><span data-stu-id="c18d7-111">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="c18d7-112">Você pode usar o `[<Struct>]` atributo para criar um registro de struct, em vez de um registro que é um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="c18d7-112">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="c18d7-113">A seguir estão alguns exemplos.</span><span class="sxs-lookup"><span data-stu-id="c18d7-113">Following are some examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="c18d7-114">Quando cada rótulo em uma linha separada, o ponto e vírgula é opcional.</span><span class="sxs-lookup"><span data-stu-id="c18d7-114">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="c18d7-115">Você pode definir valores em expressões, conhecidas como *gravar expressões*.</span><span class="sxs-lookup"><span data-stu-id="c18d7-115">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="c18d7-116">O compilador infere o tipo dos rótulos usada (se os rótulos são suficientemente diferentes daquelas de outros tipos de registro).</span><span class="sxs-lookup"><span data-stu-id="c18d7-116">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="c18d7-117">Chaves ({}) coloque a expressão de registro.</span><span class="sxs-lookup"><span data-stu-id="c18d7-117">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="c18d7-118">O código a seguir mostra uma expressão de registro que inicia um registro com três elementos de float com rótulos `x`, `y` e `z`.</span><span class="sxs-lookup"><span data-stu-id="c18d7-118">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="c18d7-119">Não use a forma abreviada se pode haver outro tipo que também tem os mesmos rótulos.</span><span class="sxs-lookup"><span data-stu-id="c18d7-119">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="c18d7-120">Os rótulos do tipo declarado mais recentemente têm precedência sobre as do tipo declarado anteriormente, portanto, no exemplo anterior, `mypoint3D` é inferido para ser `Point3D`.</span><span class="sxs-lookup"><span data-stu-id="c18d7-120">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="c18d7-121">Você pode especificar explicitamente o tipo de registro, como no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c18d7-121">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="c18d7-122">Métodos podem ser definidos para os tipos de registro como tipos de classe.</span><span class="sxs-lookup"><span data-stu-id="c18d7-122">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="c18d7-123">Criar registros usando expressões de registro</span><span class="sxs-lookup"><span data-stu-id="c18d7-123">Creating Records by Using Record Expressions</span></span>
<span data-ttu-id="c18d7-124">Você pode inicializar registros usando os rótulos que são definidos no registro.</span><span class="sxs-lookup"><span data-stu-id="c18d7-124">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="c18d7-125">Uma expressão que faz isso é conhecida como um *registro expressão*.</span><span class="sxs-lookup"><span data-stu-id="c18d7-125">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="c18d7-126">Use chaves para colocar a expressão de registro e usar o ponto e vírgula como delimitador.</span><span class="sxs-lookup"><span data-stu-id="c18d7-126">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="c18d7-127">O exemplo a seguir mostra como criar um registro.</span><span class="sxs-lookup"><span data-stu-id="c18d7-127">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="c18d7-128">A ponto e vírgula após o último campo na expressão do registro e na definição de tipo é opcional, independentemente se os campos estão todas em uma linha.</span><span class="sxs-lookup"><span data-stu-id="c18d7-128">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="c18d7-129">Quando você cria um registro, você deve fornecer valores para cada campo.</span><span class="sxs-lookup"><span data-stu-id="c18d7-129">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="c18d7-130">Você não pode consultar os valores dos outros campos na expressão de inicialização para qualquer campo.</span><span class="sxs-lookup"><span data-stu-id="c18d7-130">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="c18d7-131">No código a seguir, o tipo de `myRecord2` é inferido dos nomes dos campos.</span><span class="sxs-lookup"><span data-stu-id="c18d7-131">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="c18d7-132">Opcionalmente, você pode especificar o nome do tipo explicitamente.</span><span class="sxs-lookup"><span data-stu-id="c18d7-132">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="c18d7-133">Outra forma de construção de registro pode ser útil quando você precisa copiar um registro existente e possivelmente alterar alguns dos valores de campo.</span><span class="sxs-lookup"><span data-stu-id="c18d7-133">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="c18d7-134">A linha de código a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="c18d7-134">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="c18d7-135">Essa forma de expressão de registro é chamada de *copiar e atualizar registro expressão*.</span><span class="sxs-lookup"><span data-stu-id="c18d7-135">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="c18d7-136">Registros são imutáveis por padrão. No entanto, você pode criar facilmente os registros modificados usando uma expressão de copiar e atualizar.</span><span class="sxs-lookup"><span data-stu-id="c18d7-136">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="c18d7-137">Você também pode especificar explicitamente um campo mutável.</span><span class="sxs-lookup"><span data-stu-id="c18d7-137">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="c18d7-138">Não use o atributo DefaultValue com campos de registro.</span><span class="sxs-lookup"><span data-stu-id="c18d7-138">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="c18d7-139">Uma abordagem melhor é definir instâncias padrão dos registros com campos que são inicializados com valores padrão e, em seguida, usar uma cópia e atualizar o registro de expressão para definir todos os campos que são diferentes dos valores padrão.</span><span class="sxs-lookup"><span data-stu-id="c18d7-139">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
{
    field1 : int
    field2 : int
}

let defaultRecord1 = { field1 = 0; field2 = 0 }
let defaultRecord2 = { field1 = 1; field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with field2 = 42 }
```

## <a name="pattern-matching-with-records"></a><span data-ttu-id="c18d7-140">Correspondência de padrão com registros</span><span class="sxs-lookup"><span data-stu-id="c18d7-140">Pattern Matching with Records</span></span>
<span data-ttu-id="c18d7-141">Registros podem ser usados com a correspondência de padrões.</span><span class="sxs-lookup"><span data-stu-id="c18d7-141">Records can be used with pattern matching.</span></span> <span data-ttu-id="c18d7-142">Você pode especificar explicitamente o alguns campos e fornecer variáveis para outros campos que serão atribuídos quando ocorre uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="c18d7-142">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="c18d7-143">O exemplo de código a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="c18d7-143">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="c18d7-144">A saída desse código é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="c18d7-144">The output of this code is as follows.</span></span>

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="c18d7-145">Diferenças entre Classes e registros</span><span class="sxs-lookup"><span data-stu-id="c18d7-145">Differences Between Records and Classes</span></span>
<span data-ttu-id="c18d7-146">Campos de registro diferem das classes automaticamente, eles são expostos como propriedades, e são usadas na criação e cópia de registros.</span><span class="sxs-lookup"><span data-stu-id="c18d7-146">Record fields differ from classes in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="c18d7-147">Construção de registro também é diferente da construção de classe.</span><span class="sxs-lookup"><span data-stu-id="c18d7-147">Record construction also differs from class construction.</span></span> <span data-ttu-id="c18d7-148">Em um tipo de registro, você não pode definir um construtor.</span><span class="sxs-lookup"><span data-stu-id="c18d7-148">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="c18d7-149">Em vez disso, a sintaxe de construção descrita neste tópico se aplica.</span><span class="sxs-lookup"><span data-stu-id="c18d7-149">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="c18d7-150">Classes não têm nenhuma relação direta entre os parâmetros do construtor, campos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="c18d7-150">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="c18d7-151">Como tipos de união e estrutura de registros tem semântica de igualdade estrutural.</span><span class="sxs-lookup"><span data-stu-id="c18d7-151">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="c18d7-152">As classes têm referência semântica de igualdade.</span><span class="sxs-lookup"><span data-stu-id="c18d7-152">Classes have reference equality semantics.</span></span> <span data-ttu-id="c18d7-153">O exemplo de código a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="c18d7-153">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="c18d7-154">Se você escrever o mesmo código com classes, os objetos de dois classe seria diferentes porque os dois valores representa dois objetos no heap e somente os endereços seriam comparados (a menos que o tipo de classe substitui o `System.Object.Equals` método).</span><span class="sxs-lookup"><span data-stu-id="c18d7-154">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="c18d7-155">Se precisar fazer referência a igualdade de registros, adicione o atributo `[<ReferenceEquality>]` acima do registro.</span><span class="sxs-lookup"><span data-stu-id="c18d7-155">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="c18d7-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c18d7-156">See Also</span></span>
[<span data-ttu-id="c18d7-157">Tipos F#</span><span class="sxs-lookup"><span data-stu-id="c18d7-157">F# Types</span></span>](fsharp-types.md)

[<span data-ttu-id="c18d7-158">Classes</span><span class="sxs-lookup"><span data-stu-id="c18d7-158">Classes</span></span>](classes.md)

[<span data-ttu-id="c18d7-159">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="c18d7-159">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="c18d7-160">Reference-Equality</span><span class="sxs-lookup"><span data-stu-id="c18d7-160">Reference-Equality</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)

[<span data-ttu-id="c18d7-161">Correspondência Padrão</span><span class="sxs-lookup"><span data-stu-id="c18d7-161">Pattern Matching</span></span>](pattern-matching.md)
