---
title: Sintaxe detalhada
description: Aprenda a diferença entre a sintaxe detalhada e leve na F# linguagem de programação.
ms.date: 05/16/2016
ms.openlocfilehash: d2459da60bba5d88bd23615c8bf09ba64f7c22c4
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214043"
---
# <a name="verbose-syntax"></a><span data-ttu-id="a1f3d-103">Sintaxe detalhada</span><span class="sxs-lookup"><span data-stu-id="a1f3d-103">Verbose Syntax</span></span>

<span data-ttu-id="a1f3d-104">Há duas formas de sintaxe disponíveis para muitas construções na F# linguagem: *sintaxe detalhada* e *sintaxe leve*.</span><span class="sxs-lookup"><span data-stu-id="a1f3d-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="a1f3d-105">A sintaxe detalhada não é normalmente usada, mas tem a vantagem de ser menos sensível ao recuo.</span><span class="sxs-lookup"><span data-stu-id="a1f3d-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="a1f3d-106">A sintaxe leve é mais curta e usa recuo para sinalizar o início e o fim de construções, em vez de palavras-chave adicionais `begin`como `end`, `in`, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="a1f3d-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="a1f3d-107">A sintaxe padrão é a sintaxe leve.</span><span class="sxs-lookup"><span data-stu-id="a1f3d-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="a1f3d-108">Este tópico descreve a sintaxe para F# construções quando a sintaxe leve não está habilitada.</span><span class="sxs-lookup"><span data-stu-id="a1f3d-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="a1f3d-109">A sintaxe detalhada é sempre habilitada, portanto, mesmo que você habilite a sintaxe leve, você ainda pode usar a sintaxe detalhada para algumas construções.</span><span class="sxs-lookup"><span data-stu-id="a1f3d-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="a1f3d-110">Você pode desabilitar a sintaxe leve usando a `#light "off"` diretiva.</span><span class="sxs-lookup"><span data-stu-id="a1f3d-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>

## <a name="table-of-constructs"></a><span data-ttu-id="a1f3d-111">Tabela de construções</span><span class="sxs-lookup"><span data-stu-id="a1f3d-111">Table of Constructs</span></span>

<span data-ttu-id="a1f3d-112">A tabela a seguir mostra a sintaxe leve e detalhada F# para construções de linguagem em contextos em que há uma diferença entre as duas formas.</span><span class="sxs-lookup"><span data-stu-id="a1f3d-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="a1f3d-113">Nesta tabela, colchetes angulares (&lt;&gt;) incluem elementos de sintaxe fornecidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="a1f3d-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="a1f3d-114">Consulte a documentação de cada construção de linguagem para obter informações mais detalhadas sobre a sintaxe usada dentro dessas construções.</span><span class="sxs-lookup"><span data-stu-id="a1f3d-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>

<table>
<tr>
<th><span data-ttu-id="a1f3d-115">Construção de linguagem</span><span class="sxs-lookup"><span data-stu-id="a1f3d-115">Language construct</span></span></th>
<th><span data-ttu-id="a1f3d-116">Sintaxe leve</span><span class="sxs-lookup"><span data-stu-id="a1f3d-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="a1f3d-117">Sintaxe detalhada</span><span class="sxs-lookup"><span data-stu-id="a1f3d-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="a1f3d-118">expressões compostas</span><span class="sxs-lookup"><span data-stu-id="a1f3d-118">compound expressions</span></span>
</td>
<td>

```xml
<expression1>
<expression2>
```

</td><td>

```fsharp
<expression1>; <expression2>
```

</td>
</tr>
<tr><td>

<span data-ttu-id="a1f3d-119">associações `let` aninhadas</span><span class="sxs-lookup"><span data-stu-id="a1f3d-119">nested `let` bindings</span></span>

</td><td>

```fsharp
let f x =
    let a = 1
    let b = 2
    x + a + b
```

</td><td>

```fsharp
let f x =
    let a = 1 in
    let b = 2 in
    x + a + b
```

</td>
</tr>
<tr><td>
<span data-ttu-id="a1f3d-120">bloco de código</span><span class="sxs-lookup"><span data-stu-id="a1f3d-120">code block</span></span>
</td><td>

```fsharp
(
    <expression1>
    <expression2>
)
```

</td><td>

```fsharp
begin
    <expression1>;
    <expression2>;
end
```

</td>
</tr>
<tr><td>
`for...do`
</td><td>

```fsharp
for counter = start to finish do
    ...
```

</td><td>

```fsharp
for counter = start to finish do
    ...
done
```

</td>
</tr>
<tr><td>
`while...do`
</td><td>

```fsharp
while <condition> do
    ...
```

</td><td>

```fsharp
while <condition> do
    ...
done
```

</td>
</tr>
<tr><td>
`for...in`
</td><td>

```fsharp
for var in start .. finish do
    ...
```

</td><td>

```fsharp
for var in start .. finish do
    ...
done
```

</td>
</tr>
<tr><td>
`do`
</td><td>

```fsharp
do
    ...
```

</td><td>

```fsharp
do
    ...
in
```

</td>
</tr>
<tr><td><span data-ttu-id="a1f3d-121">gravável</span><span class="sxs-lookup"><span data-stu-id="a1f3d-121">record</span></span>
</td><td>

```fsharp
type <record-name> =
    {
        <field-declarations>
    }
    <value-or-member-definitions>
```

</td><td>

```fsharp
type <record-name> =
    {
        <field-declarations>
    }
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="a1f3d-122">classe</span><span class="sxs-lookup"><span data-stu-id="a1f3d-122">class</span></span>
</td><td>

```fsharp
type <class-name>(<params>) =
    ...
```

</td><td>

```fsharp
type <class-name>(<params>) =
    class
        ...
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="a1f3d-123">Estrutura</span><span class="sxs-lookup"><span data-stu-id="a1f3d-123">structure</span></span></td><td>

```fsharp
[<StructAttribute>]
type <structure-name> =
    ...
```

</td><td>

```fsharp
type <structure-name> =
    struct
        ...
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="a1f3d-124">união discriminada</span><span class="sxs-lookup"><span data-stu-id="a1f3d-124">discriminated union</span></span></td><td>

```fsharp
type <union-name> =
    | ...
    | ...
    ...
    <value-or-member definitions>
```

</td><td>

```fsharp
type <union-name> =
    | ...
    | ...
    ...
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="a1f3d-125">interface</span><span class="sxs-lookup"><span data-stu-id="a1f3d-125">interface</span></span></td><td>

```fsharp
type <interface-name> =
    ...
```

</td><td>

```fsharp
type <interface-name> =
    interface
        ...
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="a1f3d-126">expressão de objeto</span><span class="sxs-lookup"><span data-stu-id="a1f3d-126">object expression</span></span></td><td>

```fsharp
{ new <type-name>
    with
        <value-or-member-definitions>
        <interface-implementations>
}
```

</td><td>

```fsharp
{ new <type-name>
    with
        <value-or-member-definitions>
    end
    <interface-implementations>
}
```

</td>
</tr>
<tr><td><span data-ttu-id="a1f3d-127">implementação de interface</span><span class="sxs-lookup"><span data-stu-id="a1f3d-127">interface implementation</span></span></td><td>

```fsharp
interface <interface-name>
    with
        <value-or-member-definitions>
```

</td><td>

```fsharp
interface <interface-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="a1f3d-128">extensão de tipo</span><span class="sxs-lookup"><span data-stu-id="a1f3d-128">type extension</span></span></td><td>

```fsharp
type <type-name>
    with
        <value-or-member-definitions>
```

</td><td>

```fsharp
type <type-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="a1f3d-129">module</span><span class="sxs-lookup"><span data-stu-id="a1f3d-129">module</span></span></td><td>

```fsharp
module <module-name> =
    ...
```

</td><td>

```fsharp
module <module-name> =
    begin
        ...
    end
```

</td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="a1f3d-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1f3d-130">See also</span></span>

- [<span data-ttu-id="a1f3d-131">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="a1f3d-131">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="a1f3d-132">Diretivas de Compilador</span><span class="sxs-lookup"><span data-stu-id="a1f3d-132">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="a1f3d-133">Diretrizes de Formatação de Código</span><span class="sxs-lookup"><span data-stu-id="a1f3d-133">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
