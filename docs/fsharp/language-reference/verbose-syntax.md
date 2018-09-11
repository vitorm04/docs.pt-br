---
title: Sintaxe detalhada (F#)
description: 'Aprenda a diferença entre a sintaxe detalhada e leve na linguagem de programação F #.'
ms.date: 05/16/2016
ms.openlocfilehash: b4f2354738da4692cb444e5e7dd9531d80d26664
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44367935"
---
# <a name="verbose-syntax"></a><span data-ttu-id="542b1-103">Sintaxe detalhada</span><span class="sxs-lookup"><span data-stu-id="542b1-103">Verbose Syntax</span></span>

<span data-ttu-id="542b1-104">Há duas formas de sintaxe disponíveis para muitas construções de linguagem F #: *sintaxe detalhada* e *sintaxe leve*.</span><span class="sxs-lookup"><span data-stu-id="542b1-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="542b1-105">A sintaxe detalhada como normalmente não é usado, mas tem a vantagem de ser menos confidencial para recuo.</span><span class="sxs-lookup"><span data-stu-id="542b1-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="542b1-106">A sintaxe leve é mais curta e usa o recuo para sinalizar o início e fim de construções, em vez de palavras-chave adicionais como `begin`, `end`, `in`e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="542b1-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="542b1-107">A sintaxe padrão é a sintaxe leve.</span><span class="sxs-lookup"><span data-stu-id="542b1-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="542b1-108">Este tópico descreve a sintaxe para construções no F # quando sintaxe leve não está habilitado.</span><span class="sxs-lookup"><span data-stu-id="542b1-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="542b1-109">Sintaxe detalhada está sempre habilitado, portanto, mesmo se você habilita a sintaxe leve, você ainda pode usar sintaxe detalhada para algumas construções.</span><span class="sxs-lookup"><span data-stu-id="542b1-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="542b1-110">Você pode desabilitar a sintaxe simples usando o `#light "off"` diretiva.</span><span class="sxs-lookup"><span data-stu-id="542b1-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>

## <a name="table-of-constructs"></a><span data-ttu-id="542b1-111">Tabela das construções</span><span class="sxs-lookup"><span data-stu-id="542b1-111">Table of Constructs</span></span>

<span data-ttu-id="542b1-112">A tabela a seguir mostra a sintaxe leve e detalhada para construções de linguagem F # em contextos em que há uma diferença entre as duas formas.</span><span class="sxs-lookup"><span data-stu-id="542b1-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="542b1-113">Nesta tabela, ângulo colchetes (&lt;&gt;) coloque os elementos de sintaxe fornecida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="542b1-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="542b1-114">Consulte a documentação para cada constructo de linguagem para obter mais informações sobre a sintaxe usada dentro dessas construções.</span><span class="sxs-lookup"><span data-stu-id="542b1-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>

<table>
<tr>
<th><span data-ttu-id="542b1-115">Construção de linguagem</span><span class="sxs-lookup"><span data-stu-id="542b1-115">Language construct</span></span></th>
<th><span data-ttu-id="542b1-116">Sintaxe leve</span><span class="sxs-lookup"><span data-stu-id="542b1-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="542b1-117">Sintaxe detalhada</span><span class="sxs-lookup"><span data-stu-id="542b1-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="542b1-118">expressões compostas</span><span class="sxs-lookup"><span data-stu-id="542b1-118">compound expressions</span></span>
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


<span data-ttu-id="542b1-119">aninhada `let` associações</span><span class="sxs-lookup"><span data-stu-id="542b1-119">nested `let` bindings</span></span>

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
<span data-ttu-id="542b1-120">bloco de código</span><span class="sxs-lookup"><span data-stu-id="542b1-120">code block</span></span>
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
<tr><td><span data-ttu-id="542b1-121">Registro</span><span class="sxs-lookup"><span data-stu-id="542b1-121">record</span></span>
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
<tr><td><span data-ttu-id="542b1-122">classe</span><span class="sxs-lookup"><span data-stu-id="542b1-122">class</span></span>
</td><td><span data-ttu-id="542b1-123">
```
type <class-name>(<params>) = ... ```

</span><span class="sxs-lookup"><span data-stu-id="542b1-123">
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
<tr><td><span data-ttu-id="542b1-124">Estrutura</span><span class="sxs-lookup"><span data-stu-id="542b1-124">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="542b1-125">união discriminada</span><span class="sxs-lookup"><span data-stu-id="542b1-125">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="542b1-126">interface</span><span class="sxs-lookup"><span data-stu-id="542b1-126">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="542b1-127">expressão de objeto</span><span class="sxs-lookup"><span data-stu-id="542b1-127">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="542b1-128">implementação de interface</span><span class="sxs-lookup"><span data-stu-id="542b1-128">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="542b1-129">extensão de tipo</span><span class="sxs-lookup"><span data-stu-id="542b1-129">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="542b1-130">module</span><span class="sxs-lookup"><span data-stu-id="542b1-130">module</span></span></td><td>

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

## <a name="see-also"></a><span data-ttu-id="542b1-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="542b1-131">See also</span></span>

- [<span data-ttu-id="542b1-132">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="542b1-132">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="542b1-133">Diretivas de Compilador</span><span class="sxs-lookup"><span data-stu-id="542b1-133">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="542b1-134">Diretrizes de Formatação de Código</span><span class="sxs-lookup"><span data-stu-id="542b1-134">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
