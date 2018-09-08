---
title: Sintaxe detalhada (F#)
description: 'Aprenda a diferença entre a sintaxe detalhada e leve na linguagem de programação F #.'
ms.date: 05/16/2016
ms.openlocfilehash: b4f2354738da4692cb444e5e7dd9531d80d26664
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44193153"
---
# <a name="verbose-syntax"></a>Sintaxe detalhada

Há duas formas de sintaxe disponíveis para muitas construções de linguagem F #: *sintaxe detalhada* e *sintaxe leve*. A sintaxe detalhada como normalmente não é usado, mas tem a vantagem de ser menos confidencial para recuo. A sintaxe leve é mais curta e usa o recuo para sinalizar o início e fim de construções, em vez de palavras-chave adicionais como `begin`, `end`, `in`e assim por diante. A sintaxe padrão é a sintaxe leve. Este tópico descreve a sintaxe para construções no F # quando sintaxe leve não está habilitado. Sintaxe detalhada está sempre habilitado, portanto, mesmo se você habilita a sintaxe leve, você ainda pode usar sintaxe detalhada para algumas construções. Você pode desabilitar a sintaxe simples usando o `#light "off"` diretiva.

## <a name="table-of-constructs"></a>Tabela das construções

A tabela a seguir mostra a sintaxe leve e detalhada para construções de linguagem F # em contextos em que há uma diferença entre as duas formas. Nesta tabela, ângulo colchetes (&lt;&gt;) coloque os elementos de sintaxe fornecida pelo usuário. Consulte a documentação para cada constructo de linguagem para obter mais informações sobre a sintaxe usada dentro dessas construções.

<table>
<tr>
<th>Construção de linguagem</th>
<th>Sintaxe leve</th>
<th>Sintaxe detalhada</th>
</tr>
<tr>
<td>
expressões compostas
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


aninhada `let` associações

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
bloco de código
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
<tr><td>Registro
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
<tr><td>classe
</td><td>
```
type <class-name>(<params>) = ... ```

</td><td>

```
type <class-name>(<params>) =
    class
        ...
    end
```
</td>
</tr>
<tr><td>Estrutura</td><td>

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
<tr><td>união discriminada</td><td>

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
<tr><td>interface</td><td>

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
<tr><td>expressão de objeto</td><td>

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
<tr><td>implementação de interface</td><td>

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
<tr><td>extensão de tipo</td><td>

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
<tr><td>module</td><td>

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

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Diretivas de Compilador](compiler-directives.md)
- [Diretrizes de Formatação de Código](code-formatting-guidelines.md)
