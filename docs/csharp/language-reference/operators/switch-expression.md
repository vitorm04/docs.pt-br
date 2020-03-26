---
title: expressão do interruptor - referência C#
description: Aprenda a usar a expressão do switch C# para correspondência de padrões e outras introspecções de dados
ms.date: 03/19/2020
ms.openlocfilehash: 9e609bcea0f92f492b5f9b07840e47f75c1b71e4
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249784"
---
# <a name="switch-expression-c-reference"></a>expressão do interruptor (referência C#)

Este artigo `switch` abrange a expressão, introduzida em C# 8.0. Para obter `switch` informações sobre a declaração, consulte o artigo sobre a [ `switch` declaração](../keywords/switch.md) na seção [de declarações.](../keywords/index.md)

## <a name="basic-example"></a>Exemplo básico

A `switch` expressão `switch`prevê semântica semelhante a um contexto de expressão. Fornece uma sintaxe concisa quando os braços de interruptor produzem um valor. O exemplo a seguir mostra a estrutura de uma expressão de switch. Ele traduz valores `enum` de uma direção visual representativa em um mapa on-line para a direção cardeal correspondente:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetBasicStructure":::

A amostra anterior mostra os elementos básicos de uma expressão de switch:

- A *expressão de intervalo*: `direction` O exemplo anterior usa a variável como expressão de intervalo.
- Braços *de expressão do interruptor*: Cada braço de expressão do interruptor contém um *padrão,* um protetor de *caixa*opcional, o `=>` token e uma *expressão*.

O resultado da expressão do *interruptor* é o valor da expressão do primeiro braço de expressão do *interruptor* cujo *padrão* corresponde à expressão *de faixa* e cuja guarda de *causa,* se presente, avalia a `true`. A *expressão* à direita `=>` do token não pode ser uma declaração de expressão.

Os *braços de expressão do interruptor* são avaliados na ordem de texto. O compilador emite um erro quando um braço de expressão de *interruptor* inferior não pode ser escolhido porque um braço de expressão de *interruptor* mais alto corresponde a todos os seus valores.

## <a name="patterns-and-case-guards"></a>Padrões e guardas de caso

Muitos padrões são suportados em braços de expressão de interruptor. O exemplo anterior usou um *padrão de valor*. Um *padrão de valor* compara a expressão de intervalo a um valor. Esse valor deve ser uma constante de tempo de compilação. O *padrão de tipo* compara a expressão de intervalo a um tipo conhecido. O exemplo a seguir recupera o terceiro elemento de uma seqüência. Ele usa diferentes métodos baseados no tipo da seqüência:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetTypePattern":::

Padrões podem ser recursivos, onde um padrão testa um tipo, e se esse tipo corresponder, o padrão corresponde a um ou mais valores de propriedade na expressão de intervalo. Você pode usar padrões recursivos para estender o exemplo anterior. Você adiciona braços de expressão de interruptor para matrizes que tenham menos de 3 elementos. Padrões recursivos são mostrados no seguinte exemplo:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetRecursivePattern":::

Padrões recursivos podem examinar propriedades da expressão de intervalo, mas não podem executar código arbitrário. Você pode usar um protetor de `when` *caso,* especificado em uma cláusula, para fornecer verificações semelhantes para outros tipos de seqüência:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetGuardCase":::

Finalmente, você pode `_` adicionar `null` o padrão e o padrão para captar argumentos que não são processados por qualquer outro braço de expressão do switch. Isso torna a expressão do interruptor *exaustiva,* o que significa que qualquer possível valor da expressão de intervalo é manuseado. O exemplo a seguir adiciona os braços de expressão:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetExhaustive":::

O exemplo anterior `null` adiciona um `IEnumerable<T>` padrão e `_` altera o padrão de tipo para um padrão. O `null` padrão fornece uma verificação nula como um braço de expressão do interruptor. A expressão para esse <xref:System.ArgumentNullException>braço lança um . O `_` padrão corresponde a todas as entradas que não foram combinadas com armas anteriores. Deve vir depois `null` do cheque, `null` ou corresponderia às entradas.

Você pode ler mais na proposta de especificação da linguagem C# para [padrões recursivos](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression).

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Operadores do C#](index.md)
- [Correspondência de padrões](../../pattern-matching.md)
