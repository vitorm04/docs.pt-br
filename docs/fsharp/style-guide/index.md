---
title: Guia de estilo do F#
description: Aprenda os princípios de cinco de código F# BOM.
ms.date: 05/14/2018
ms.openlocfilehash: 1d0f4e2a946f0cc91f376ba624f847549a830bc7
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "34235899"
---
# <a name="f-style-guide"></a>Guia de estilo do F#

Os artigos a seguir descrevem as diretrizes para formatação de código F# e tópicas orientação para recursos da linguagem e como eles devem ser usados.

Este guia foi formulado com base no uso do F# em grandes bases de código com um grupo diverso de programadores. Neste guia geralmente leva a uso bem-sucedido do F# e minimiza as frustrações quando os requisitos para programas mudam ao longo do tempo.

## <a name="five-principles-of-good-f-code"></a>Cinco princípios do bom código de F#

Você deve ter os seguintes princípios em mente que sempre que você escrever código em F#, especialmente em sistemas que irá alterar ao longo do tempo. Cada parte da orientação nos próximos artigos deriva essas cinco pontos.

1. **Código F# BOM é sucintos e expressivos**

    F# tem muitos recursos que permitem que você expressar as ações em menos linhas de código e reutilizar a funcionalidade genérica. A biblioteca principal F# também contém vários tipos úteis e funções para trabalhar com coleções comuns de dados. Como regra geral, se você puder expressar uma solução para um problema em menos linhas de código, outros desenvolvedores (ou seu futuro self) será apreciativo. É também é altamente recomendável que você use uma biblioteca como FSharp. Core, o [vastas bibliotecas do .NET](https://docs.microsoft.com/dotnet/api/) que F# é executado, ou um pacote de produtos de terceiros na [NuGet](https://www.nuget.org/) quando você precisa executar uma tarefa não trivial.

2. **Código F# BOM é interoperável**

    Interoperação pode levar várias formas, incluindo o consumo de código em linguagens diferentes. Os limites do que outros chamadores interoperam com código são partes essenciais para acertar. Ao escrever em F#, você deve sempre estar pensando sobre como outro código chamará o código que você está escrevendo, incluindo se elas fazem isso de outra linguagem como c#. O [diretrizes de Design do componente de F#](component-design-guidelines.md) descrevem a interoperabilidade em detalhes.

3. **Código F# BOM faz uso de programação de objeto, não do objeto orientação**

    F# tem suporte completo para a programação com objetos no .NET, incluindo [classes](../language-reference/classes.md), [interfaces](../language-reference/interfaces.md), [modificadores de acesso](../language-reference/access-control.md), [declassesabstratas](../language-reference/abstract-classes.md)e assim por diante. Para o código funcional mais complicado, como as funções que devem ser sensíveis ao contexto, objetos facilmente podem encapsular as informações contextuais de maneira que funções não podem. Recursos como [parâmetros opcionais](../language-reference/members/methods.md#optional-arguments) e o uso cuidadoso de [sobrecarga](../language-reference/members/methods.md#overloaded-methods) pode facilitar o consumo dessa funcionalidade para chamadores.

4. **Código F# boa executa bem sem expor a mutação**

    Não é segredo que, para escrever código de alto desempenho, você deve usar mutação. É como os computadores trabalham, afinal de contas. Esse código costuma ser difícil de acertar e propensas a erro. Evite a exposição de mutação aos chamadores. Em vez disso, [criar uma interface funcional que oculta uma implementação baseada em mutação](conventions.md#performance) quando o desempenho é crítico.

5. **Código F# BOM é compatível com ferramentas**

    As ferramentas são imprescindíveis para trabalhar em grandes bases de código, e você pode escrever código F#, de modo que ele pode ser usado com mais eficiência com ferramentas de linguagem F#. Um exemplo é verificar se que você não exagere com um estilo livre de ponto de programação, para que os valores intermediários podem ser inspecionados com um depurador. Outro exemplo é o uso [comentários da documentação XML](../language-reference/xml-documentation.md) descrever construções, de modo que as dicas de ferramenta nos editores podem exibir esses comentários no site de chamada. Sempre pense sobre como seu código será ser ler, navegar, depurado e manipulado por outros programadores com suas ferramentas.

## <a name="next-steps"></a>Próximas etapas

O [código do F# diretrizes de formatação](formatting.md) fornecem orientação sobre como formatar o código para que seja fácil de ler.

O [convenções de codificação do F#](conventions.md) fornecem orientação para linguagens que ajudarão a manutenção de longo prazo do F# maiores de programação F# bases de código.

O [diretrizes de design do componente F#](component-design-guidelines.md) fornecem diretrizes para criação de F# componentes, como bibliotecas.
