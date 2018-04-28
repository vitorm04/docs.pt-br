---
title: Sintaxe detalhada (F#)
description: 'Saber a diferença entre a sintaxe detalhada e leve em F # linguagem de programação.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: fd040a66a789bc6717fd14e6a9f28274c9e3542b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="verbose-syntax"></a><span data-ttu-id="75256-103">Sintaxe detalhada</span><span class="sxs-lookup"><span data-stu-id="75256-103">Verbose Syntax</span></span>

<span data-ttu-id="75256-104">Há duas formas de sintaxe disponíveis para muitas construções de linguagem F #: *sintaxe detalhada* e *sintaxe leve*.</span><span class="sxs-lookup"><span data-stu-id="75256-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="75256-105">A sintaxe detalhada não é mais comumente usada, mas tem a vantagem de ser menos confidencial para recuo.</span><span class="sxs-lookup"><span data-stu-id="75256-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="75256-106">A sintaxe simples é mais curta e usa o recuo para sinalizar o início e fim do construções, em vez de palavras-chave adicionais, como `begin`, `end`, `in`e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="75256-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="75256-107">A sintaxe padrão é a sintaxe leve.</span><span class="sxs-lookup"><span data-stu-id="75256-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="75256-108">Este tópico descreve a sintaxe para construções de linguagem F # quando sintaxe leve não está habilitado.</span><span class="sxs-lookup"><span data-stu-id="75256-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="75256-109">Sintaxe detalhada está sempre habilitada, portanto, mesmo se você habilitar a sintaxe leve, você ainda pode usar sintaxe detalhada para algumas construções.</span><span class="sxs-lookup"><span data-stu-id="75256-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="75256-110">Você pode desabilitar a sintaxe simples usando o `#light "off"` diretiva.</span><span class="sxs-lookup"><span data-stu-id="75256-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>


## <a name="table-of-constructs"></a><span data-ttu-id="75256-111">Tabela de construções</span><span class="sxs-lookup"><span data-stu-id="75256-111">Table of Constructs</span></span>
<span data-ttu-id="75256-112">A tabela a seguir mostra a sintaxe leve e detalhada para construções de linguagem F # em contextos que não há uma diferença entre as duas formas.</span><span class="sxs-lookup"><span data-stu-id="75256-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="75256-113">Nessa tabela, ângulo colchetes (&lt;&gt;) coloque elementos de sintaxe fornecida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="75256-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="75256-114">Consulte a documentação de cada construção de linguagem para obter mais informações sobre a sintaxe usada dentro dessas construções.</span><span class="sxs-lookup"><span data-stu-id="75256-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>



<table>
<tr>
<th><span data-ttu-id="75256-115">Construção de linguagem</span><span class="sxs-lookup"><span data-stu-id="75256-115">Language construct</span></span></th>
<th><span data-ttu-id="75256-116">Sintaxe leve</span><span class="sxs-lookup"><span data-stu-id="75256-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="75256-117">Sintaxe detalhada</span><span class="sxs-lookup"><span data-stu-id="75256-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="75256-118">expressões compostas</span><span class="sxs-lookup"><span data-stu-id="75256-118">compound expressions</span></span>
</td>
<td>

```xml
<expression1>
<expression2>
```
</td><td>

```
<expression1>; <expression2>
```

</td>
</tr>
<tr><td>


<span data-ttu-id="75256-119">aninhada `let` associações</span><span class="sxs-lookup"><span data-stu-id="75256-119">nested `let` bindings</span></span>

</td><td>
```
let f x =
    let a = 1
    let b = 2
    x + a + b
```

</td><td>

```
let f x =
    let a = 1 in
    let b = 2 in
    x + a + b
```

</td>
</tr>
<tr><td>
<span data-ttu-id="75256-120">bloco de código</span><span class="sxs-lookup"><span data-stu-id="75256-120">code block</span></span>
</td><td>

```
(
    <expression1>
    <expression2>
)
```

</td><td>

```
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

```
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

```
while <condition> do
    ...
```

</td><td>

```
while <condition> do
    ...
done
```

</td>
</tr>
<tr><td>
`for...in`
</td><td>

```
for var in start .. finish do
    ...
```

</td><td>

```
for var in start .. finish do
    ...
done
```

</td>
</tr>
<tr><td>
`do`
</td><td>

```
do
    ...
```

</td><td>

```
do
    ...
in
```

</td>
</tr>
<tr><td><span data-ttu-id="75256-121">Registro</span><span class="sxs-lookup"><span data-stu-id="75256-121">record</span></span>
</td><td>

```
type <record-name> =
    {
        <field-declarations>
    }
    <value-or-member-definitions>
```

</td><td>

```
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
<tr><td><span data-ttu-id="75256-122">classe</span><span class="sxs-lookup"><span data-stu-id="75256-122">class</span></span>
</td><td><span data-ttu-id="75256-123">
```
type <class-name>(<params>) = ... ```

</span><span class="sxs-lookup"><span data-stu-id="75256-123">
```
type <class-name>(<params>) = ... ```

</span></span></td><td>

```
type <class-name>(<params>) =
    class
        ...
    end
```
</td>
</tr>
<tr><td><span data-ttu-id="75256-124">Estrutura</span><span class="sxs-lookup"><span data-stu-id="75256-124">structure</span></span></td><td>

```
[<StructAttribute>]
type <structure-name> =
    ...
```
</td><td>

```
type <structure-name> =
    struct
        ...
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="75256-125">união discriminada</span><span class="sxs-lookup"><span data-stu-id="75256-125">discriminated union</span></span></td><td>

```
type <union-name> =
    | ...
    | ...
    ...
    <value-or-member definitions>
```
</td><td>

```
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
<tr><td><span data-ttu-id="75256-126">interface</span><span class="sxs-lookup"><span data-stu-id="75256-126">interface</span></span></td><td>

```
type <interface-name> =
    ...
```
</td><td>

```
type <interface-name> =
    interface
        ...
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="75256-127">expressão de objeto</span><span class="sxs-lookup"><span data-stu-id="75256-127">object expression</span></span></td><td>

```
{ new <type-name>
    with
        <value-or-member-definitions>
        <interface-implementations>
}
```

</td><td>

```
{ new <type-name>
    with
        <value-or-member-definitions>
    end
    <interface-implementations>
}
```

</td>
</tr>
<tr><td><span data-ttu-id="75256-128">implementação de interface</span><span class="sxs-lookup"><span data-stu-id="75256-128">interface implementation</span></span></td><td>

```
interface <interface-name>
    with
        <value-or-member-definitions>
```

</td><td>

```
interface <interface-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="75256-129">extensão de tipo</span><span class="sxs-lookup"><span data-stu-id="75256-129">type extension</span></span></td><td>

```
type <type-name>
    with
        <value-or-member-definitions>
```

</td><td>

```
type <type-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="75256-130">module</span><span class="sxs-lookup"><span data-stu-id="75256-130">module</span></span></td><td>

```
module <module-name> =
    ...
```

</td><td>

```
module <module-name> =
    begin
        ...
    end
```

</td>
</tr>
</table>



## <a name="see-also"></a><span data-ttu-id="75256-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75256-131">See Also</span></span>
[<span data-ttu-id="75256-132">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="75256-132">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="75256-133">Diretivas de Compilador</span><span class="sxs-lookup"><span data-stu-id="75256-133">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="75256-134">Diretrizes de Formatação de Código</span><span class="sxs-lookup"><span data-stu-id="75256-134">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
