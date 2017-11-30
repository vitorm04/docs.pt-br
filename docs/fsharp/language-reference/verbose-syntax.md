---
title: Sintaxe detalhada (F#)
description: "Saber a diferença entre a sintaxe detalhada e leve em F # linguagem de programação."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0a6792b3-b312-4453-a025-21d9760eee5d
ms.openlocfilehash: 2cef359a879897825733a3186be97b38896f5953
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="verbose-syntax"></a><span data-ttu-id="c7afc-104">Sintaxe detalhada</span><span class="sxs-lookup"><span data-stu-id="c7afc-104">Verbose Syntax</span></span>

<span data-ttu-id="c7afc-105">Há duas formas de sintaxe disponíveis para muitas construções de linguagem F #: *sintaxe detalhada* e *sintaxe leve*.</span><span class="sxs-lookup"><span data-stu-id="c7afc-105">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="c7afc-106">A sintaxe detalhada não é mais comumente usada, mas tem a vantagem de ser menos confidencial para recuo.</span><span class="sxs-lookup"><span data-stu-id="c7afc-106">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="c7afc-107">A sintaxe simples é mais curta e usa o recuo para sinalizar o início e fim do construções, em vez de palavras-chave adicionais, como `begin`, `end`, `in`e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="c7afc-107">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="c7afc-108">A sintaxe padrão é a sintaxe leve.</span><span class="sxs-lookup"><span data-stu-id="c7afc-108">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="c7afc-109">Este tópico descreve a sintaxe para construções de linguagem F # quando sintaxe leve não está habilitado.</span><span class="sxs-lookup"><span data-stu-id="c7afc-109">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="c7afc-110">Sintaxe detalhada está sempre habilitada, portanto, mesmo se você habilitar a sintaxe leve, você ainda pode usar sintaxe detalhada para algumas construções.</span><span class="sxs-lookup"><span data-stu-id="c7afc-110">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="c7afc-111">Você pode desabilitar a sintaxe simples usando o `#light "off"` diretiva.</span><span class="sxs-lookup"><span data-stu-id="c7afc-111">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>


## <a name="table-of-constructs"></a><span data-ttu-id="c7afc-112">Tabela de construções</span><span class="sxs-lookup"><span data-stu-id="c7afc-112">Table of Constructs</span></span>
<span data-ttu-id="c7afc-113">A tabela a seguir mostra a sintaxe leve e detalhada para construções de linguagem F # em contextos que não há uma diferença entre as duas formas.</span><span class="sxs-lookup"><span data-stu-id="c7afc-113">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="c7afc-114">Nessa tabela, ângulo colchetes (&lt;&gt;) coloque elementos de sintaxe fornecida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="c7afc-114">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="c7afc-115">Consulte a documentação de cada construção de linguagem para obter mais informações sobre a sintaxe usada dentro dessas construções.</span><span class="sxs-lookup"><span data-stu-id="c7afc-115">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>



<table>
<tr>
<th><span data-ttu-id="c7afc-116">Construção de linguagem</span><span class="sxs-lookup"><span data-stu-id="c7afc-116">Language construct</span></span></th>
<th><span data-ttu-id="c7afc-117">Sintaxe leve</span><span class="sxs-lookup"><span data-stu-id="c7afc-117">Lightweight syntax</span></span></th>
<th><span data-ttu-id="c7afc-118">Sintaxe detalhada</span><span class="sxs-lookup"><span data-stu-id="c7afc-118">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="c7afc-119">expressões compostas</span><span class="sxs-lookup"><span data-stu-id="c7afc-119">compound expressions</span></span>
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


<span data-ttu-id="c7afc-120">aninhada `let` associações</span><span class="sxs-lookup"><span data-stu-id="c7afc-120">nested `let` bindings</span></span>

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
<span data-ttu-id="c7afc-121">bloco de código</span><span class="sxs-lookup"><span data-stu-id="c7afc-121">code block</span></span>
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
<tr><td><span data-ttu-id="c7afc-122">Registro</span><span class="sxs-lookup"><span data-stu-id="c7afc-122">record</span></span>
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
<tr><td><span data-ttu-id="c7afc-123">classe</span><span class="sxs-lookup"><span data-stu-id="c7afc-123">class</span></span>
</td><td><span data-ttu-id="c7afc-124">
```
type <class-name>(<params>) = ... ```

</span><span class="sxs-lookup"><span data-stu-id="c7afc-124">
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
<tr><td><span data-ttu-id="c7afc-125">Estrutura</span><span class="sxs-lookup"><span data-stu-id="c7afc-125">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="c7afc-126">união discriminada</span><span class="sxs-lookup"><span data-stu-id="c7afc-126">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="c7afc-127">interface</span><span class="sxs-lookup"><span data-stu-id="c7afc-127">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="c7afc-128">expressão de objeto</span><span class="sxs-lookup"><span data-stu-id="c7afc-128">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="c7afc-129">implementação de interface</span><span class="sxs-lookup"><span data-stu-id="c7afc-129">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="c7afc-130">extensão de tipo</span><span class="sxs-lookup"><span data-stu-id="c7afc-130">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="c7afc-131">module</span><span class="sxs-lookup"><span data-stu-id="c7afc-131">module</span></span></td><td>

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



## <a name="see-also"></a><span data-ttu-id="c7afc-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7afc-132">See Also</span></span>
[<span data-ttu-id="c7afc-133">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="c7afc-133">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="c7afc-134">Diretivas de Compilador</span><span class="sxs-lookup"><span data-stu-id="c7afc-134">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="c7afc-135">Diretrizes de Formatação de Código</span><span class="sxs-lookup"><span data-stu-id="c7afc-135">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
