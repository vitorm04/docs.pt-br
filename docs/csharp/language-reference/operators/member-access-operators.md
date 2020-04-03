---
title: Operadores e expressões de acesso a membros - referência C#
description: Aprenda sobre operadores de C# que você pode usar para acessar membros de tipo.
ms.date: 03/31/2020
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
- ^_CSharpKeyword
- .._CSharpKeyword
helpviewer_keywords:
- member access operators [C#]
- member access operator [C#]
- dot operator [C#]
- . operator [C#]
- subscript operator [C#]
- square brackets [] operator [C#]
- indexer operator [C#]
- '[] operator [C#]'
- null-conditional operators [C#]
- Elvis operator [C#]
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
- ^ operator [C#]
- index from end operator [C#]
- hat operator [C#]
- .. operator [C#]
- range operator [C#]
ms.openlocfilehash: a132e527deadcffb4826c1965987fc09da470a09
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635312"
---
# <a name="member-access-operators-and-expressions-c-reference"></a>Operadores e expressões de acesso a membros (referência C#)

Você pode usar os seguintes operadores e expressões quando acessar um membro do tipo:

- (acesso ao membro): para acessar um membro de um namespace ou um tipo [ `.` ](#member-access-expression-)
- [(acesso a elemento de matriz ou indexador) : para acessar um elemento de matriz ou um indexador de tipo `[]` ](#indexer-operator-)
- [e `?[]` (operadores condicionais nulos) : realizar uma operação de acesso a membros ou elementos somente se um operand não for `?.` ](#null-conditional-operators--and-)nulo
- (invocação) : chamar um método acessado ou invocar um delegado [ `()` ](#invocation-expression-)
- [(índice a partir do fim): para indicar que a posição do elemento é do final de uma seqüência `^` ](#index-from-end-operator-)
- (intervalo) : para especificar uma gama de índices que você pode usar para obter uma gama de elementos de seqüência [ `..` ](#range-operator-)

## <a name="member-access-expression-"></a>Expressão de acesso ao membro .

Use o token `.` para acessar um membro de um namespace ou um tipo, como demonstram os exemplos a seguir:

- Use `.` para acessar um namespace aninhado dentro de um namespace, como mostra o exemplo a seguir de uma [ `using` diretiva:](../keywords/using-directive.md)

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- Use `.` para formar um *nome qualificado* para acessar um tipo dentro de um namespace, como mostra o código a seguir:

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  Use [ `using` ](../keywords/using-directive.md) uma diretiva para tornar opcional o uso de nomes qualificados.

- Use `.` para acessar [membros de tipo](../../programming-guide/classes-and-structs/index.md#members), estático e não-estático, como mostra o código a seguir:

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

Você também pode usar `.` para acessar um [método de extensão](../../programming-guide/classes-and-structs/extension-methods.md).

## <a name="indexer-operator-"></a>Operador de indexador []

Os colchetes, `[]`, normalmente são usados para acesso de elemento de matriz, indexador ou ponteiro.

### <a name="array-access"></a>Acesso de matriz

O exemplo a seguir demonstra como acessar elementos de matriz:

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

Se um índice de matriz estiver fora dos limites da dimensão correspondente de uma matriz, uma <xref:System.IndexOutOfRangeException> será gerada.

Como mostra o exemplo anterior, você também usar colchetes quando declara um tipo de matriz ou instancia uma instância de matriz.

Para obter mais informações sobre matrizes, confira [Matrizes](../../programming-guide/arrays/index.md).

### <a name="indexer-access"></a>Acesso de indexador

O exemplo a seguir <xref:System.Collections.Generic.Dictionary%602> usa o tipo .NET para demonstrar o acesso ao indexador:

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

Os indexadores permitem indexar instâncias de um tipo definido pelo usuário de maneira semelhante à indexação de matriz. Ao contrário dos índices de matriz, que devem ser inteiros, os parâmetros do indexador podem ser declarados de qualquer tipo.

Para obter mais informações sobre indexadores, confira [Indexadores](../../programming-guide/indexers/index.md).

### <a name="other-usages-of-"></a>Outros usos de []

Para saber mais sobre o acesso a elemento de ponteiro, confira a seção [Operador de acesso a elemento de ponteiro []](pointer-related-operators.md#pointer-element-access-operator-) do artigo [Operadores relacionados a ponteiro](pointer-related-operators.md).

Os colchetes também são usados para especificar [atributos](../../programming-guide/concepts/attributes/index.md):

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Operadores condicionais nulos ?. e ?[]

Disponível em C# 6 e posterior, um operador condicionado a `?[]`membros aplica um acesso a [membros](#member-access-expression-), `?.`ou acesso a [elementos](#indexer-operator-), operação ao seu operativo e somente se esse operand avaliar a não-nulo; caso contrário, `null`ele retorna . Isto é

- Se `a` avaliar `null`, o `a?.x` resultado `a?[x]` `null`de ou é .
- Se `a` avalia-se para não nulo, o resultado `a?.x` ou `a.x` `a[x]` `a?[x]` é o mesmo que o resultado ou, respectivamente.

  > [!NOTE]
  > Se `a.x` `a[x]` ou lançar `a?.x` uma `a?[x]` exceção, ou lançar `a`a mesma exceção para não-nulo . Por exemplo, `a` se for uma instância `x` de matriz não `a` `a?[x]` nula <xref:System.IndexOutOfRangeException>e estiver fora dos limites de , lançaria um .

Os operadores condicionais nulos estão entrando em curto-circuito. Ou seja, se uma operação em uma cadeia de membro operações condicionais de acesso a membro ou elemento retornar `null`, o restante da cadeia não será executado. No exemplo a seguir, `B` não será avaliado se `A` for avaliado como `null` e `C` não será avaliado se `A` ou `B` for avaliado como `null`:

```csharp
A?.B?.Do(C);
A?.B?[C];
```

O exemplo a seguir demonstra o uso dos operadores `?.` e `?[]`:

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

O exemplo anterior também usa o [operador `??` de coalizão nula](null-coalescing-operator.md) para especificar uma expressão alternativa `null`para avaliar caso o resultado de uma operação condicionada seja .

Se `a.x` `a[x]` ou é de um tipo `T` `a?.x` de `a?[x]` valor não anulado, ou é do [tipo](../builtin-types/nullable-value-types.md) `T?`de valor nulo correspondente . Se você precisar de `T`uma expressão do tipo, `??` aplique o operador de coalizão nula a uma expressão condicionada nula, como mostra o exemplo a seguir:

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

No exemplo anterior, se você não `??` usar `numbers?.Length < 2` o `false` operador, avalia quando `numbers` é `null`.

O operador de acesso do membro condicional nulo `?.` também é conhecido como o operador Elvis.

### <a name="thread-safe-delegate-invocation"></a>Invocação de delegado thread-safe

Use o operador `?.` para verificar se um delegado é não nulo e chame-o de uma forma thread-safe (por exemplo, quando você [aciona um evento](../../../standard/events/how-to-raise-and-consume-events.md)), conforme mostrado no código a seguir:

```csharp
PropertyChanged?.Invoke(…)
```

Esse código é equivalente ao código a seguir que você usaria no C# 5 ou anterior:

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-expression-"></a>Expressão de invocação ()

Use parênteses, `()`, para chamar um [método](../../programming-guide/classes-and-structs/methods.md) ou invocar um [delegado](../../programming-guide/delegates/index.md).

O exemplo a seguir demonstra como chamar um método (com ou sem argumentos) e invocar um delegado:

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

Você também pode usar parênteses ao invocar um [construtor](../../programming-guide/classes-and-structs/constructors.md) com o operador [`new`](new-operator.md).

### <a name="other-usages-of-"></a>Outros usos de ()

Você também pode usar parênteses para ajustar a ordem na qual as operações em uma expressão são avaliadas. Para saber mais, confira [Operadores C#](index.md).

[Expressões de conversão](type-testing-and-cast.md#cast-operator-), que executam conversões de tipo explícitas, também usam parênteses.

## <a name="index-from-end-operator-"></a>Índice do operador final ^

Disponível em C# 8.0 `^` e posteriormente, o operador indica a posição do elemento a partir do final de uma seqüência. Para uma seqüência de `length`comprimento, `length - n` `^n` aponta para o elemento com deslocamento desde o início de uma seqüência. Por exemplo, `^1` aponta para o último `^length` elemento de uma seqüência e aponta para o primeiro elemento de uma seqüência.

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

Como o exemplo anterior `^e` mostra, <xref:System.Index?displayProperty=nameWithType> a expressão é do tipo. Em `^e`expressão, o `e` resultado deve ser `int`implicitamente conversível para .

Você também pode `^` usar o operador com o [operador de alcance](#range-operator-) para criar uma série de índices. Para obter mais informações, consulte [Índices e faixas](../../tutorials/ranges-indexes.md).

## <a name="range-operator-"></a>Operador de alcance ..

Disponível em C# 8.0 `..` e posterior, o operador especifica o início e o fim de uma série de índices como seus operadores. O operand esquerdo é um começo *inclusivo* de uma faixa. O operand direito é um fim *exclusivo* de um alcance. Qualquer um dos operands pode ser um índice desde o início ou a partir do final de uma seqüência, como o exemplo a seguir mostra:

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

Como o exemplo anterior `a..b` mostra, <xref:System.Range?displayProperty=nameWithType> a expressão é do tipo. Em `a..b`expressão, os `a` `b` resultados e devem `int` ser <xref:System.Index>implicitamente conversíveis para ou .

Você pode omitir qualquer um dos `..` operands do operador para obter um intervalo aberto:

- `a..` equivale a `a..^0`
- `..b` equivale a `0..b`
- `..` equivale a `0..^0`

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

Para obter mais informações, consulte [Índices e faixas](../../tutorials/ranges-indexes.md).

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Os `.` `()` `..` operadores `^`não podem ser sobrecarregados. O operador `[]` também é considerado um operador não sobrecarregável. Use [indexadores](../../programming-guide/indexers/index.md) para permitir a indexação com tipos definidos pelo usuário.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Acesso ao membro](~/_csharplang/spec/expressions.md#member-access)
- [Acesso a elemento](~/_csharplang/spec/expressions.md#element-access)
- [Operador condicional nulo](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Expressões de invocação](~/_csharplang/spec/expressions.md#invocation-expressions)

Para obter mais informações sobre índices e faixas, consulte a [nota de proposta do recurso](~/_csharplang/proposals/csharp-8.0/ranges.md).

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Operadores do C#](index.md)
- [?? (operador de união nula)](null-coalescing-operator.md)
- [Operador ::](namespace-alias-qualifier.md)
