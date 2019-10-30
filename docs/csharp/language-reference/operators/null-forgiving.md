---
title: '! operador (NULL-tolerante)- C# referência'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 21bbf8e1253641317750b911e052ee5ff0a0d063
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036167"
---
# <a name="-null-forgiving-operator-c-reference"></a>! (operador NULL-tolerante) (C# referência)

Disponível em C# 8,0 e posterior, o operador sufixo unário `!` é o operador NULL-tolerante. Em um [contexto de anotação anulável](../../nullable-references.md#nullable-annotation-context)habilitado, você usa o operador NULL-tolerante para declarar que a expressão `x` de um tipo de referência não é `null`: `x!`. O prefixo unário `!` é o [operador lógico de negação](boolean-logical-operators.md#logical-negation-operator-).

O operador NULL-tolerante não tem nenhum efeito no tempo de execução. Ele afeta apenas a análise de fluxo estático do compilador, alterando o estado nulo da expressão. Em tempo de execução, a expressão `x!` é avaliada como o resultado da expressão subjacente `x`.

Para obter mais informações sobre o recurso de tipos de referência anulável, consulte [tipos de referência anuláveis](../../nullable-references.md).

## <a name="examples"></a>Exemplos

Um dos casos de uso do operador NULL-tolerante está no teste da lógica de validação de argumento. Por exemplo, considere a seguinte classe:

[!code-csharp[Person class](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#PersonClass)]

Usando a [estrutura de teste MSTest](../../../core/testing/unit-testing-with-mstest.md), você pode criar o seguinte teste para a lógica de validação no construtor:

[!code-csharp[Person test](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#TestPerson)]

Sem o operador NULL-tolerante, o compilador gera o seguinte aviso para o código anterior: `Warning CS8625: Cannot convert null literal to non-nullable reference type`. Usando o operador NULL-tolerante, você informa ao compilador que a passagem de `null` é esperada e não deve ser avisada sobre.

Você também pode usar o operador NULL-tolerante quando sabe definitivamente que uma expressão não pode ser `null`, mas que o compilador não gerencia para reconhecê-la. No exemplo a seguir, se o método `IsValid` retornar `true`, seu argumento não será `null` e você poderá desreferenciá-lo com segurança:

[!code-csharp[Use null-forgiving operator](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseNullForgiving)]

Sem o operador NULL-tolerante, o compilador gera o seguinte aviso para o código `p.Name`: `Warning CS8602: Dereference of a possibly null reference`.

Se você puder modificar o método `IsValid`, poderá usar o atributo [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) para informar ao compilador que um argumento do método `IsValid` não pode ser `null` quando o método retornar `true`:

[!code-csharp[Use an attribute](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseAttribute)]

No exemplo anterior, você não precisa usar o operador NULL-tolerante porque o compilador tem informações suficientes para descobrir que `p` não pode ser `null` dentro da instrução `if`. Para obter mais informações sobre os atributos que permitem fornecer informações adicionais sobre o estado nulo de uma variável, consulte [Atualizar APIs com atributos para definir expectativas nulas](../../nullable-attributes.md).

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, consulte [a seção operador NULL-tolerante](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) do [rascunho da especificação de tipos de referência anulável](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Operadores do C#](index.md)
- [Tutorial: design com tipos de referência anuláveis](../../tutorials/nullable-reference-types.md)
