---
title: Sintaxe detalhada (F#)
description: 'Saber a diferença entre a sintaxe detalhada e leve em F # linguagem de programação.'
ms.date: 05/16/2016
ms.openlocfilehash: b0bed66b4a76c5ab11e6c9e7aaf695f864e74ca0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="verbose-syntax"></a><span data-ttu-id="dd88b-103">Sintaxe detalhada</span><span class="sxs-lookup"><span data-stu-id="dd88b-103">Verbose Syntax</span></span>

<span data-ttu-id="dd88b-104">Há duas formas de sintaxe disponíveis para muitas construções de linguagem F #: *sintaxe detalhada* e *sintaxe leve*.</span><span class="sxs-lookup"><span data-stu-id="dd88b-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="dd88b-105">A sintaxe detalhada não é mais comumente usada, mas tem a vantagem de ser menos confidencial para recuo.</span><span class="sxs-lookup"><span data-stu-id="dd88b-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="dd88b-106">A sintaxe simples é mais curta e usa o recuo para sinalizar o início e fim do construções, em vez de palavras-chave adicionais, como `begin`, `end`, `in`e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="dd88b-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="dd88b-107">A sintaxe padrão é a sintaxe leve.</span><span class="sxs-lookup"><span data-stu-id="dd88b-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="dd88b-108">Este tópico descreve a sintaxe para construções de linguagem F # quando sintaxe leve não está habilitado.</span><span class="sxs-lookup"><span data-stu-id="dd88b-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="dd88b-109">Sintaxe detalhada está sempre habilitada, portanto, mesmo se você habilitar a sintaxe leve, você ainda pode usar sintaxe detalhada para algumas construções.</span><span class="sxs-lookup"><span data-stu-id="dd88b-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="dd88b-110">Você pode desabilitar a sintaxe simples usando o `#light "off"` diretiva.</span><span class="sxs-lookup"><span data-stu-id="dd88b-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>


## <a name="table-of-constructs"></a><span data-ttu-id="dd88b-111">Tabela de construções</span><span class="sxs-lookup"><span data-stu-id="dd88b-111">Table of Constructs</span></span>
<span data-ttu-id="dd88b-112">A tabela a seguir mostra a sintaxe leve e detalhada para construções de linguagem F # em contextos que não há uma diferença entre as duas formas.</span><span class="sxs-lookup"><span data-stu-id="dd88b-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="dd88b-113">Nessa tabela, ângulo colchetes (&lt;&gt;) coloque elementos de sintaxe fornecida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="dd88b-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="dd88b-114">Consulte a documentação de cada construção de linguagem para obter mais informações sobre a sintaxe usada dentro dessas construções.</span><span class="sxs-lookup"><span data-stu-id="dd88b-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>



<table>
<tr>
<th><span data-ttu-id="dd88b-115">Construção de linguagem</span><span class="sxs-lookup"><span data-stu-id="dd88b-115">Language construct</span></span></th>
<th><span data-ttu-id="dd88b-116">Sintaxe leve</span><span class="sxs-lookup"><span data-stu-id="dd88b-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="dd88b-117">Sintaxe detalhada</span><span class="sxs-lookup"><span data-stu-id="dd88b-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="dd88b-118">expressões compostas</span><span class="sxs-lookup"><span data-stu-id="dd88b-118">compound expressions</span></span>
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


<span data-ttu-id="dd88b-119">aninhada `let` associações</span><span class="sxs-lookup"><span data-stu-id="dd88b-119">nested `let` bindings</span></span>

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
<span data-ttu-id="dd88b-120">bloco de código</span><span class="sxs-lookup"><span data-stu-id="dd88b-120">code block</span></span>
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
<tr><td><span data-ttu-id="dd88b-121">Registro</span><span class="sxs-lookup"><span data-stu-id="dd88b-121">record</span></span>
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
<tr><td><span data-ttu-id="dd88b-122">classe</span><span class="sxs-lookup"><span data-stu-id="dd88b-122">class</span></span>
</td><td><span data-ttu-id="dd88b-123">
```
type <class-name>(<params>) = ... ```

</span><span class="sxs-lookup"><span data-stu-id="dd88b-123">
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
<tr><td><span data-ttu-id="dd88b-124">Estrutura</span><span class="sxs-lookup"><span data-stu-id="dd88b-124">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="dd88b-125">união discriminada</span><span class="sxs-lookup"><span data-stu-id="dd88b-125">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="dd88b-126">interface</span><span class="sxs-lookup"><span data-stu-id="dd88b-126">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="dd88b-127">expressão de objeto</span><span class="sxs-lookup"><span data-stu-id="dd88b-127">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="dd88b-128">implementação de interface</span><span class="sxs-lookup"><span data-stu-id="dd88b-128">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="dd88b-129">extensão de tipo</span><span class="sxs-lookup"><span data-stu-id="dd88b-129">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="dd88b-130">module</span><span class="sxs-lookup"><span data-stu-id="dd88b-130">module</span></span></td><td>

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



## <a name="see-also"></a><span data-ttu-id="dd88b-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd88b-131">See Also</span></span>
[<span data-ttu-id="dd88b-132">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="dd88b-132">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="dd88b-133">Diretivas de Compilador</span><span class="sxs-lookup"><span data-stu-id="dd88b-133">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="dd88b-134">Diretrizes de Formatação de Código</span><span class="sxs-lookup"><span data-stu-id="dd88b-134">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
