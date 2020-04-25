---
title: expressão switch-referência C#
description: Saiba como usar a expressão de comutador C# para correspondência de padrões e outras introspecção de dados
ms.date: 03/19/2020
ms.openlocfilehash: f53cbe873c841271f64496e4e5ff1f11750c7b8a
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140660"
---
# <a name="switch-expression-c-reference"></a>expressão switch (referência C#)

Este artigo aborda a `switch` expressão, introduzida em C# 8,0. Para obter informações sobre `switch` a instrução, consulte o artigo sobre a [ `switch` instrução](../keywords/switch.md) na seção de [instruções](../keywords/index.md) .

## <a name="basic-example"></a>Exemplo básico

A `switch` expressão fornece `switch`semântica semelhante em um contexto de expressão. Ele fornece uma sintaxe concisa quando os braços de switch produzem um valor. O exemplo a seguir mostra a estrutura de uma expressão switch. Ele traduz valores de uma `enum` representação de direções visuais em um mapa online para a direção Cardeal correspondente:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetBasicStructure":::

O exemplo anterior mostra os elementos básicos de uma expressão switch:

- A *expressão de intervalo*: o exemplo anterior usa a `direction` variável como a expressão de intervalo.
- Os *braços de expressão switch*: cada ARM de expressão switch contém um *padrão*, uma *proteção de caso*opcional, o `=>` token e uma *expressão*.

O resultado da *expressão switch* é o valor da expressão do primeiro *ARM de expressão switch* cujo *padrão* corresponde à *expressão Range* e cujo *Case Guard*, se presente, é avaliado como `true`. A *expressão* à direita do `=>` token não pode ser uma instrução de expressão.

Os *braços de expressão switch* são avaliados em ordem de texto. O compilador emite um erro quando um *ARM de expressão de comutador* inferior não pode ser escolhido porque um *ARM de expressão de comutador* superior corresponde a todos os seus valores.

## <a name="patterns-and-case-guards"></a>Padrões e proteções de caso

Muitos padrões têm suporte em braços de expressão de switch. O exemplo anterior usou um *padrão de valor*. Um *padrão de valor* compara a expressão de intervalo com um valor. Esse valor deve ser uma constante de tempo de compilação. O *padrão de tipo* compara a expressão de intervalo com um tipo conhecido. O exemplo a seguir recupera o terceiro elemento de uma sequência. Ele usa métodos diferentes com base no tipo da sequência:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetTypePattern":::

Os padrões podem ser recursivos, onde um padrão testa um tipo e, se esse tipo corresponder, o padrão corresponde a um ou mais valores de propriedade na expressão de intervalo. Você pode usar padrões recursivos para estender o exemplo anterior. Você adiciona braços de expressão de switch para matrizes com menos de três elementos. Padrões recursivos são mostrados no exemplo a seguir:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetRecursivePattern":::

Padrões recursivos podem examinar as propriedades da expressão de intervalo, mas não podem executar código arbitrário. Você pode usar um *protetor de caso*, especificado em `when` uma cláusula, para fornecer verificações semelhantes para outros tipos de sequência:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetGuardCase":::

Por fim, você pode adicionar `_` o padrão e `null` o padrão para capturar argumentos que não são processados por nenhum outro ARM de expressão de switch. Isso torna a expressão de comutador *exaustiva*, o que significa que qualquer valor possível da expressão de intervalo é manipulado. O exemplo a seguir adiciona esses braços de expressão:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetExhaustive":::

O exemplo anterior adiciona um `null` padrão e altera o `IEnumerable<T>` padrão de tipo para um `_` padrão. O `null` padrão fornece uma verificação nula como um ARM de expressão switch. A expressão para esse ARM gera um <xref:System.ArgumentNullException>. O `_` padrão corresponde a todas as entradas que não corresponderam aos braços anteriores. Ele deve vir após a `null` verificação, ou ele corresponderá `null` a entradas.

Você pode ler mais na proposta de especificação da linguagem C# para obter [padrões recursivos](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression).

## <a name="see-also"></a>Veja também

- [Referência do C#](../index.md)
- [Operadores do C#](index.md)
- [Correspondência de padrões](../../pattern-matching.md)
