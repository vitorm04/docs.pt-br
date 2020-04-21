---
title: '! Operador (inodentrada nula) - Referência C#'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: a8b47e83ce9e999ea2afe94db0a21725abc2d327
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738565"
---
# <a name="-null-forgiving-operator-c-reference"></a>! Operador (inodção nula) (referência C#)

Disponível em C# 8.0 e posterior, o operador postfix não-ary `!` é o operador de perdão nulo. Em um contexto de [anotação anulada](../../nullable-references.md#nullable-annotation-context)habilitado, você usa o `x` operador que perdoa nulo para declarar que a expressão de um tipo de referência não `null`é: `x!`. O operador `!` de prefixo não ário é o [operador de negação lógico.](boolean-logical-operators.md#logical-negation-operator-)

O operador de perdoar nulos não tem efeito no tempo de execução. Afeta apenas a análise estática do fluxo do compilador alterando o estado nulo da expressão. No tempo de `x!` execução, a expressão avalia `x`o resultado da expressão subjacente .

Para obter mais informações sobre o recurso de tipos de referência anulados, consulte [tipos de referência anulados](../builtin-types/nullable-reference-types.md).

## <a name="examples"></a>Exemplos

Um dos casos de uso do operador que perdoa nulos é testar a lógica de validação de argumentos. Por exemplo, considere a seguinte classe:

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

Usando a [estrutura de teste MSTest,](../../../core/testing/unit-testing-with-mstest.md)você pode criar o seguinte teste para a lógica de validação no construtor:

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

Sem o operador que perdoa nulos, o compilador `Warning CS8625: Cannot convert null literal to non-nullable reference type`gera o seguinte aviso para o código anterior: . Ao usar o operador de perdoar nulos, você `null` informa ao compilador que a passagem é esperada e não deve ser avisada.

Você também pode usar o operador que perdoa nulos quando você definitivamente sabe que uma expressão não pode ser, `null` mas o compilador não consegue reconhecer isso. No exemplo a seguir, se o `IsValid` método retornar, `true`seu argumento não `null` é e você pode desreferencia-lo com segurança:

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

Sem o operador que perdoa nulos, o `p.Name` compilador gera o seguinte aviso para o código: `Warning CS8602: Dereference of a possibly null reference`.

Se você puder `IsValid` modificar o método, você pode usar o atributo [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) para informar ao compilador que um argumento do `IsValid` método não pode ser `null` quando o método retorna: `true`

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

No exemplo anterior, você não precisa usar o operador que perdoa nulos porque `p` o `null` compilador `if` tem informações suficientes para descobrir que não pode estar dentro da declaração. Para obter mais informações sobre os atributos que permitem fornecer informações adicionais sobre o estado nulo de uma variável, consulte [Atualizar APIs com atributos para definir expectativas nulas](../../nullable-attributes.md).

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, consulte A seção [operadora de perdão nulo](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) da [minuta da especificação de tipos de referência anuladas](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Operadores do C#](index.md)
- [Tutorial: Design com tipos de referência anulados](../../tutorials/nullable-reference-types.md)
