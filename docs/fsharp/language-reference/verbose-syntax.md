---
title: Sintaxe detalhada (F#)
description: 'Aprenda a diferença entre a sintaxe detalhada e leve na linguagem de programação F #.'
ms.date: 05/16/2016
ms.openlocfilehash: e697c6fe619df7ffe12f7d4e2a234a5a5cb401ff
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50196759"
---
# <a name="verbose-syntax"></a><span data-ttu-id="4d36d-103">Sintaxe detalhada</span><span class="sxs-lookup"><span data-stu-id="4d36d-103">Verbose Syntax</span></span>

<span data-ttu-id="4d36d-104">Há duas formas de sintaxe disponíveis para muitas construções de linguagem F #: *sintaxe detalhada* e *sintaxe leve*.</span><span class="sxs-lookup"><span data-stu-id="4d36d-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="4d36d-105">A sintaxe detalhada como normalmente não é usado, mas tem a vantagem de ser menos confidencial para recuo.</span><span class="sxs-lookup"><span data-stu-id="4d36d-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="4d36d-106">A sintaxe leve é mais curta e usa o recuo para sinalizar o início e fim de construções, em vez de palavras-chave adicionais como `begin`, `end`, `in`e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="4d36d-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="4d36d-107">A sintaxe padrão é a sintaxe leve.</span><span class="sxs-lookup"><span data-stu-id="4d36d-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="4d36d-108">Este tópico descreve a sintaxe para construções no F # quando sintaxe leve não está habilitado.</span><span class="sxs-lookup"><span data-stu-id="4d36d-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="4d36d-109">Sintaxe detalhada está sempre habilitado, portanto, mesmo se você habilita a sintaxe leve, você ainda pode usar sintaxe detalhada para algumas construções.</span><span class="sxs-lookup"><span data-stu-id="4d36d-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="4d36d-110">Você pode desabilitar a sintaxe simples usando o `#light "off"` diretiva.</span><span class="sxs-lookup"><span data-stu-id="4d36d-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>

## <a name="table-of-constructs"></a><span data-ttu-id="4d36d-111">Tabela das construções</span><span class="sxs-lookup"><span data-stu-id="4d36d-111">Table of Constructs</span></span>

<span data-ttu-id="4d36d-112">A tabela a seguir mostra a sintaxe leve e detalhada para construções de linguagem F # em contextos em que há uma diferença entre as duas formas.</span><span class="sxs-lookup"><span data-stu-id="4d36d-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="4d36d-113">Nesta tabela, ângulo colchetes (&lt;&gt;) coloque os elementos de sintaxe fornecida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="4d36d-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="4d36d-114">Consulte a documentação para cada constructo de linguagem para obter mais informações sobre a sintaxe usada dentro dessas construções.</span><span class="sxs-lookup"><span data-stu-id="4d36d-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>

<table>
<tr>
<th><span data-ttu-id="4d36d-115">Construção de linguagem</span><span class="sxs-lookup"><span data-stu-id="4d36d-115">Language construct</span></span></th>
<th><span data-ttu-id="4d36d-116">Sintaxe leve</span><span class="sxs-lookup"><span data-stu-id="4d36d-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="4d36d-117">Sintaxe detalhada</span><span class="sxs-lookup"><span data-stu-id="4d36d-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="4d36d-118">expressões compostas</span><span class="sxs-lookup"><span data-stu-id="4d36d-118">compound expressions</span></span>
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

<span data-ttu-id="4d36d-119">aninhada `let` associações</span><span class="sxs-lookup"><span data-stu-id="4d36d-119">nested `let` bindings</span></span>

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
<span data-ttu-id="4d36d-120">bloco de código</span><span class="sxs-lookup"><span data-stu-id="4d36d-120">code block</span></span>
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

```
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
<tr><td><span data-ttu-id="4d36d-121">Registro</span><span class="sxs-lookup"><span data-stu-id="4d36d-121">record</span></span>
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
<tr><td><span data-ttu-id="4d36d-122">classe</span><span class="sxs-lookup"><span data-stu-id="4d36d-122">class</span></span>
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
<tr><td><span data-ttu-id="4d36d-123">Estrutura</span><span class="sxs-lookup"><span data-stu-id="4d36d-123">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="4d36d-124">união discriminada</span><span class="sxs-lookup"><span data-stu-id="4d36d-124">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="4d36d-125">interface</span><span class="sxs-lookup"><span data-stu-id="4d36d-125">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="4d36d-126">expressão de objeto</span><span class="sxs-lookup"><span data-stu-id="4d36d-126">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="4d36d-127">implementação de interface</span><span class="sxs-lookup"><span data-stu-id="4d36d-127">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="4d36d-128">extensão de tipo</span><span class="sxs-lookup"><span data-stu-id="4d36d-128">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="4d36d-129">module</span><span class="sxs-lookup"><span data-stu-id="4d36d-129">module</span></span></td><td>

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

## <a name="see-also"></a><span data-ttu-id="4d36d-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d36d-130">See also</span></span>

- [<span data-ttu-id="4d36d-131">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="4d36d-131">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="4d36d-132">Diretivas de Compilador</span><span class="sxs-lookup"><span data-stu-id="4d36d-132">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="4d36d-133">Diretrizes de Formatação de Código</span><span class="sxs-lookup"><span data-stu-id="4d36d-133">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
