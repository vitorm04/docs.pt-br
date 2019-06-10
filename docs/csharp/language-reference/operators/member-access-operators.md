---
title: Operadores de acesso a membro – referência de C#
description: Aprenda sobre operadores de C# que você pode usar para acessar membros de tipo.
ms.date: 05/09/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
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
ms.openlocfilehash: de0715a2ac946fa47f0d83ac8569595e622f0b97
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758086"
---
# <a name="member-access-operators-c-reference"></a>Operadores de acesso a membro (Referência de C#)

Quando você acessa um membro de tipo, você pode usar os seguintes operadores:

- [`.` (acesso a membro)](#member-access-operator-): para acessar um membro de um namespace ou um tipo
- [`[]` (acesso a um indexador ou elemento de matriz)](#indexer-operator-): para acessar um elemento de matriz ou um indexador de tipo
- [`?.` e `?[]` (operadores condicionais nulos)](#null-conditional-operators--and-): para executar uma operação de acesso a membro ou elemento somente se um operando for não nulo
- [`()` (invocação)](#invocation-operator-): chamar um método acessado ou invocar um delegado

## <a name="member-access-operator-"></a>Operador de acesso a membro.

Use o token `.` para acessar um membro de um namespace ou um tipo, como demonstram os exemplos a seguir:

- Use `.` para acessar um namespace aninhado dentro de um namespace, como mostra o exemplo a seguir de uma [diretiva `using`](../keywords/using-directive.md):

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- Use `.` para formar um *nome qualificado* para acessar um tipo dentro de um namespace, como mostra o código a seguir:

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  Use uma [diretiva `using`](../keywords/using-directive.md) para tornar o uso de nomes qualificados opcional.

- Use `.` para acessar [membros de tipo](../../programming-guide/classes-and-structs/index.md#members), estático e não-estático, como mostra o código a seguir:

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

Você também pode usar `.` para acessar um [método de extensão](../../programming-guide/classes-and-structs/extension-methods.md).

## <a name="indexer-operator-"></a>Operador de indexador []

Os colchetes, `[]`, normalmente são usados para acesso de elemento de matriz, indexador ou ponteiro.

### <a name="array-access"></a>Acesso de matriz

O exemplo a seguir demonstra como acessar elementos de matriz:

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

Se um índice de matriz estiver fora dos limites da dimensão correspondente de uma matriz, uma <xref:System.IndexOutOfRangeException> será gerada.

Como mostra o exemplo anterior, você também usar colchetes quando declara um tipo de matriz ou instancia uma instância de matriz.

Para obter mais informações sobre matrizes, confira [Matrizes](../../programming-guide/arrays/index.md).

### <a name="indexer-access"></a>Acesso de indexador

O exemplo a seguir usa o tipo <xref:System.Collections.Generic.Dictionary%602> do .NET para demonstrar o acesso de indexador:

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

Os indexadores permitem indexar instâncias de um tipo definido pelo usuário de maneira semelhante à indexação de matriz. Ao contrário dos índices da matriz, que precisam ser um inteiro, os argumentos do indexador podem ser declarados como qualquer tipo.

Para obter mais informações sobre indexadores, confira [Indexadores](../../programming-guide/indexers/index.md).

### <a name="other-usages-of-"></a>Outros usos de []

Para saber mais sobre o acesso a elemento de ponteiro, confira a seção [Operador de acesso a elemento de ponteiro []](pointer-related-operators.md#pointer-element-access-operator-) do artigo [Operadores relacionados a ponteiro](pointer-related-operators.md).

Os colchetes também são usados para especificar [atributos](../../programming-guide/concepts/attributes/index.md):

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Operadores condicionais nulos ?. e ?[]

Disponível no C# 6 e versões posteriores, um operador nulo condicional aplicará a seu operando uma operação de acesso a membro, `?.`, ou de acesso a elemento, `?[]`, somente se o operando for avaliado como não nulo. Se o operando for avaliado como `null`, o resultado da aplicação do operador será `null`. O operador de acesso do membro condicional nulo `?.` também é conhecido como o operador Elvis.

Os operadores condicionais nulos estão entrando em curto-circuito. Ou seja, se uma operação em uma cadeia de membro operações condicionais de acesso a membro ou elemento retornar `null`, o restante da cadeia não será executado. No exemplo a seguir, `B` não será avaliado se `A` for avaliado como `null` e `C` não será avaliado se `A` ou `B` for avaliado como `null`:

```csharp
A?.B?.Do(C);
A?.B?[C];
```

O exemplo a seguir demonstra o uso dos operadores `?.` e `?[]`:

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

O exemplo anterior também mostra o uso do [operador de coalescência nula](null-coalescing-operator.md). Você pode usar o operador de coalescência nula para fornecer uma expressão alternativa a avaliar caso o resultado da operação condicional nula seja `null`.

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

## <a name="invocation-operator-"></a>Operador de invocação ()

Use parênteses, `()`, para chamar um [método](../../programming-guide/classes-and-structs/methods.md) ou invocar um [delegado](../../programming-guide/delegates/index.md).

O exemplo a seguir demonstra como chamar um método (com ou sem argumentos) e invocar um delegado:

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

Você também pode usar parênteses ao invocar um [construtor](../../programming-guide/classes-and-structs/constructors.md) com um operador [`new`](../keywords/new-operator.md).

### <a name="other-usages-of-"></a>Outros usos de ()

Você também pode usar parênteses para especificar a ordem na qual as operações em uma expressão são avaliada. Para obter mais informações, confira a seção [Adicionando parênteses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) o artigo [Operadores](../../programming-guide/statements-expressions-operators/operators.md). Para obter a lista de operadores ordenada pelo nível de precedência, confira [Operadores do C#](index.md).

[Expressões de conversão](invocation-operator.md#cast-expression), que invocam um operador de conversão, também usam parênteses.

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Os operadores `.` e `()` não podem ser sobrecarregados. O operador `[]` também é considerado um operador não sobrecarregável. Use [indexadores](../../programming-guide/indexers/index.md) para permitir a indexação com tipos definidos pelo usuário.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Acesso de membros](~/_csharplang/spec/expressions.md#member-access)
- [Acesso a elemento](~/_csharplang/spec/expressions.md#element-access)
- [Operador condicional nulo](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Expressões de invocação](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [?? (operador de união nula)](null-coalescing-operator.md)
