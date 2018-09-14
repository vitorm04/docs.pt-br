---
title: Registros (F#)
description: 'Saiba como o F # registros representam agregações simples de valores nomeados, opcionalmente com membros.'
ms.date: 05/16/2016
ms.openlocfilehash: 6103d96b6b80a9e2ed168755958dbe800f7fa862
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45569587"
---
# <a name="records"></a><span data-ttu-id="cd30d-103">Registros</span><span class="sxs-lookup"><span data-stu-id="cd30d-103">Records</span></span>

<span data-ttu-id="cd30d-104">Registros representam agregações simples de valores nomeados, opcionalmente com membros.</span><span class="sxs-lookup"><span data-stu-id="cd30d-104">Records represent simple aggregates of named values, optionally with members.</span></span>  <span data-ttu-id="cd30d-105">Começando com o F # 4.1, eles podem ser structs ou tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="cd30d-105">Starting with F# 4.1, they can either be structs or reference types.</span></span>  <span data-ttu-id="cd30d-106">Eles são tipos de referência por padrão.</span><span class="sxs-lookup"><span data-stu-id="cd30d-106">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="cd30d-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd30d-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename =
    { [ mutable ] label1 : type1;
      [ mutable ] label2 : type2;
      ... }
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="cd30d-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="cd30d-108">Remarks</span></span>

<span data-ttu-id="cd30d-109">Na sintaxe anterior, *typename* é o nome do tipo de registro, *label1* e *label2* são nomes de valores, conhecidos como *rótulos*, e *type1* e *type2* são os tipos desses valores.</span><span class="sxs-lookup"><span data-stu-id="cd30d-109">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="cd30d-110">*lista de membros* é a lista opcional de membros para o tipo.</span><span class="sxs-lookup"><span data-stu-id="cd30d-110">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="cd30d-111">Você pode usar o `[<Struct>]` atributo para criar um registro de struct em vez de um registro que é um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="cd30d-111">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="cd30d-112">A seguir estão alguns exemplos.</span><span class="sxs-lookup"><span data-stu-id="cd30d-112">Following are some examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="cd30d-113">Quando cada rótulo está em uma linha separada, o ponto e vírgula é opcional.</span><span class="sxs-lookup"><span data-stu-id="cd30d-113">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="cd30d-114">Você pode definir valores em expressões, conhecidas como *gravar expressões*.</span><span class="sxs-lookup"><span data-stu-id="cd30d-114">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="cd30d-115">O compilador infere o tipo dos rótulos usados (se os rótulos são suficientemente diferentes de outros tipos de registro).</span><span class="sxs-lookup"><span data-stu-id="cd30d-115">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="cd30d-116">Chaves ({}) coloque a expressão de registro.</span><span class="sxs-lookup"><span data-stu-id="cd30d-116">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="cd30d-117">O código a seguir mostra uma expressão de registro que inicializa um registro com três elementos de flutuante com rótulos `x`, `y` e `z`.</span><span class="sxs-lookup"><span data-stu-id="cd30d-117">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="cd30d-118">Não use a forma abreviada se pode haver outro tipo que também tem os mesmos rótulos.</span><span class="sxs-lookup"><span data-stu-id="cd30d-118">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="cd30d-119">Os rótulos do tipo declarado mais recentemente têm precedência sobre aquelas do tipo declarado anteriormente, portanto, no exemplo anterior, `mypoint3D` será inferida para ser `Point3D`.</span><span class="sxs-lookup"><span data-stu-id="cd30d-119">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="cd30d-120">Você pode especificar explicitamente o tipo de registro, como no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="cd30d-120">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="cd30d-121">Métodos podem ser definidos para tipos de registro, como acontece com tipos de classe.</span><span class="sxs-lookup"><span data-stu-id="cd30d-121">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="cd30d-122">Criação de registros usando expressões de registro</span><span class="sxs-lookup"><span data-stu-id="cd30d-122">Creating Records by Using Record Expressions</span></span>

<span data-ttu-id="cd30d-123">Você pode inicializar os registros usando os rótulos que são definidos no registro.</span><span class="sxs-lookup"><span data-stu-id="cd30d-123">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="cd30d-124">Uma expressão que faz isso é conhecida como um *registre expressão*.</span><span class="sxs-lookup"><span data-stu-id="cd30d-124">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="cd30d-125">Use chaves para coloque a expressão de registro e o ponto e vírgula como delimitador.</span><span class="sxs-lookup"><span data-stu-id="cd30d-125">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="cd30d-126">O exemplo a seguir mostra como criar um registro.</span><span class="sxs-lookup"><span data-stu-id="cd30d-126">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="cd30d-127">A ponto e vírgula após o último campo na expressão do registro e na definição de tipo é opcional, independentemente se os campos são tudo em uma linha.</span><span class="sxs-lookup"><span data-stu-id="cd30d-127">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="cd30d-128">Quando você cria um registro, você deve fornecer valores para cada campo.</span><span class="sxs-lookup"><span data-stu-id="cd30d-128">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="cd30d-129">Você não pode referenciar os valores dos outros campos na expressão de inicialização para qualquer campo.</span><span class="sxs-lookup"><span data-stu-id="cd30d-129">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="cd30d-130">No código a seguir, o tipo de `myRecord2` é inferido dos nomes dos campos.</span><span class="sxs-lookup"><span data-stu-id="cd30d-130">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="cd30d-131">Opcionalmente, você pode especificar explicitamente o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="cd30d-131">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="cd30d-132">Outra forma de construção de registro pode ser útil quando você tem que copiar um registro existente e, possivelmente, alterar alguns dos valores de campo.</span><span class="sxs-lookup"><span data-stu-id="cd30d-132">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="cd30d-133">A linha de código a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="cd30d-133">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="cd30d-134">Essa forma da expressão de registro é chamada de *copiar e atualizar registro expressão*.</span><span class="sxs-lookup"><span data-stu-id="cd30d-134">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="cd30d-135">Registros são imutáveis por padrão. No entanto, você pode criar facilmente os registros modificados usando uma expressão de copiar e atualizar.</span><span class="sxs-lookup"><span data-stu-id="cd30d-135">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="cd30d-136">Você também pode especificar explicitamente um campo mutável.</span><span class="sxs-lookup"><span data-stu-id="cd30d-136">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="cd30d-137">Não use o atributo DefaultValue com campos de registro.</span><span class="sxs-lookup"><span data-stu-id="cd30d-137">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="cd30d-138">Uma abordagem melhor é definir instâncias padrão dos registros com campos que são inicializados para valores padrão e, em seguida, usar uma cópia e atualizar o registro de expressão para definir todos os campos que são diferentes dos valores padrão.</span><span class="sxs-lookup"><span data-stu-id="cd30d-138">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
    { Field1 : int
      Field2 : int }

let defaultRecord1 = { Field1 = 0; Field2 = 0 }
let defaultRecord2 = { Field1 = 1; Field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with Field2 = 42 }
```

## <a name="pattern-matching-with-records"></a><span data-ttu-id="cd30d-139">Correspondência de padrões com registros</span><span class="sxs-lookup"><span data-stu-id="cd30d-139">Pattern Matching with Records</span></span>

<span data-ttu-id="cd30d-140">Registros podem ser usados com correspondência de padrões.</span><span class="sxs-lookup"><span data-stu-id="cd30d-140">Records can be used with pattern matching.</span></span> <span data-ttu-id="cd30d-141">Você pode especificar explicitamente o alguns campos e fornecer variáveis para os outros campos que serão atribuídos quando ocorrer uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="cd30d-141">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="cd30d-142">O exemplo de código a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="cd30d-142">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="cd30d-143">A saída desse código é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="cd30d-143">The output of this code is as follows.</span></span>

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="cd30d-144">Diferenças entre Classes e registros</span><span class="sxs-lookup"><span data-stu-id="cd30d-144">Differences Between Records and Classes</span></span>

<span data-ttu-id="cd30d-145">Campos de registro são diferentes das classes em que elas são expostas como propriedades automaticamente e eles são usados na criação e cópia de registros.</span><span class="sxs-lookup"><span data-stu-id="cd30d-145">Record fields differ from classes in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="cd30d-146">Construção de registro também é diferente da construção de classe.</span><span class="sxs-lookup"><span data-stu-id="cd30d-146">Record construction also differs from class construction.</span></span> <span data-ttu-id="cd30d-147">Em um tipo de registro, você não pode definir um construtor.</span><span class="sxs-lookup"><span data-stu-id="cd30d-147">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="cd30d-148">Em vez disso, a sintaxe de construção descrita neste tópico se aplica.</span><span class="sxs-lookup"><span data-stu-id="cd30d-148">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="cd30d-149">Classes não têm nenhuma relação direta entre os parâmetros do construtor, campos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="cd30d-149">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="cd30d-150">Como os tipos de união e estrutura, os registros têm semântica de igualdade estrutural.</span><span class="sxs-lookup"><span data-stu-id="cd30d-150">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="cd30d-151">As classes têm referência semântica de igualdade.</span><span class="sxs-lookup"><span data-stu-id="cd30d-151">Classes have reference equality semantics.</span></span> <span data-ttu-id="cd30d-152">O código de exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="cd30d-152">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="cd30d-153">A saída desse código é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cd30d-153">The output of this code is as follows:</span></span>

```
The records are equal.
```

<span data-ttu-id="cd30d-154">Se você escrever o mesmo código com classes, os objetos de duas classe seriam desiguais porque os dois valores seriam representam dois objetos no heap e somente os endereços devem ser comparados (a menos que o tipo de classe substitui o `System.Object.Equals` método).</span><span class="sxs-lookup"><span data-stu-id="cd30d-154">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="cd30d-155">Se você precisa referenciar igualdade para registros, adicione o atributo `[<ReferenceEquality>]` acima do registro.</span><span class="sxs-lookup"><span data-stu-id="cd30d-155">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd30d-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd30d-156">See also</span></span>

- [<span data-ttu-id="cd30d-157">Tipos F#</span><span class="sxs-lookup"><span data-stu-id="cd30d-157">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="cd30d-158">Classes</span><span class="sxs-lookup"><span data-stu-id="cd30d-158">Classes</span></span>](classes.md)
- [<span data-ttu-id="cd30d-159">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="cd30d-159">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="cd30d-160">Igualdade de referência</span><span class="sxs-lookup"><span data-stu-id="cd30d-160">Reference-Equality</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)
- [<span data-ttu-id="cd30d-161">Correspondência Padrão</span><span class="sxs-lookup"><span data-stu-id="cd30d-161">Pattern Matching</span></span>](pattern-matching.md)
