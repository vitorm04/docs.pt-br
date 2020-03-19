---
title: Guia de estilo do F#
description: Aprenda os cinco princípios do bom código F# .
ms.date: 12/10/2018
ms.openlocfilehash: 9f47257626e04b09b546de2ae315d48d791678be
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400263"
---
# <a name="f-style-guide"></a>Guia de estilo do F#

Os artigos a seguir descrevem diretrizes para formatar código F# e orientação tópica para características do idioma e como eles devem ser usados.

Esta orientação foi formulada com base no uso de F# em grandes bases de código com um grupo diversificado de programadores. Essa orientação geralmente leva ao uso bem-sucedido do F# e minimiza frustrações quando os requisitos para programas mudam ao longo do tempo.

## <a name="five-principles-of-good-f-code"></a>Cinco princípios do bom código F#

Tenha em mente os seguintes princípios sempre que escrever o código F#, especialmente em sistemas que mudarão com o tempo. Cada peça de orientação em outros artigos provém desses cinco pontos.

1. **O código Bom F# é sucinto, expressivo e composável**

    F# tem muitos recursos que permitem expressar ações em menos linhas de código e reutilizar funcionalidade genérica. A biblioteca principal F# também contém muitos tipos e funções úteis para trabalhar com coleções comuns de dados. Composição de suas próprias funções e aquelas na biblioteca núcleo F# (ou outras bibliotecas) é uma parte da programação f# de rotina. Como regra geral, se você puder expressar uma solução para um problema em menos linhas de código, outros desenvolvedores (ou seu eu futuro) serão apreciadores. Também é altamente recomendável que você use uma biblioteca como fsharp.core, as [vastas bibliotecas .NET](../../../api/index.md) em que f# é executado, ou um pacote de terceiros no [NuGet](https://www.nuget.org/) quando você precisa fazer uma tarefa não trivial.

2. **Código Bom F# é interoperável**

    A interoperação pode tomar várias formas, incluindo o consumo de código em diferentes idiomas. Os limites do seu código com os quais outros chamadores interoperam são peças críticas para acertar, mesmo que os chamadores também estejam em F#. Ao escrever F#, você deve estar sempre pensando em como outro código chamará para o código que você está escrevendo, incluindo se eles o fizerem de outra língua como C#. As [Diretrizes de Design de Componentes F#](component-design-guidelines.md) descrevem a interoperabilidade em detalhes.

3. **Bom código F# faz uso da programação de objetos, não de orientação de objetos**

    F# tem suporte total para programação com objetos em .NET, incluindo [classes,](../language-reference/classes.md) [interfaces,](../language-reference/interfaces.md) [modificadores de acesso,](../language-reference/access-control.md)classes [abstratas,](../language-reference/abstract-classes.md)e assim por diante. Para um código funcional mais complicado, como funções que devem ser de reconhecimento de contexto, os objetos podem facilmente encapsular informações contextuais de maneiras que as funções não podem. Recursos como [parâmetros opcionais](../language-reference/members/methods.md#optional-arguments) e uso cuidadoso de [sobrecarga](../language-reference/members/methods.md#overloaded-methods) podem facilitar o consumo dessa funcionalidade para os chamadores.

4. **Código Bom F# funciona bem sem expor mutação**

    Não é segredo que para escrever código de alto desempenho, você deve usar mutação. É assim que os computadores funcionam, afinal. Esse código é muitas vezes propenso a erros e difícil de acertar. Evite expor mutação aos chamadores. Em vez disso, [construa uma interface funcional que oculta uma implementação baseada em mutação](conventions.md#performance) quando o desempenho é crítico.

5. **Código Bom F# é toolable**

    As ferramentas são inestimáveis para trabalhar em grandes bases de código, e você pode escrever código F# de tal forma que ele possa ser usado de forma mais eficaz com ferramentas de linguagem F#. Um exemplo é garantir que você não o faça demais com um estilo de programação sem pontos, para que valores intermediários possam ser inspecionados com um depurador. Outro exemplo é o uso de comentários de [documentação XML](../language-reference/xml-documentation.md) descrevendo construções de tal forma que dicas de ferramentas em editores podem exibir esses comentários no site de chamada. Pense sempre em como seu código será lido, navegado, depurado e manipulado por outros programadores com suas ferramentas.

## <a name="next-steps"></a>Próximas etapas

As [diretrizes de formatação de código F#](formatting.md) fornecem orientações sobre como formatar código para que seja fácil de ler.

As convenções de [codificação F#](conventions.md) fornecem orientação para expressões de programação F# que ajudarão a manutenção a longo prazo de bases de código F# maiores.

As [diretrizes de design de componentes F#](component-design-guidelines.md) fornecem orientação para a autoria de componentes F#, como bibliotecas.
