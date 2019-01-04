---
title: F#Guia de estilo
description: Aprenda os princípios de cinco bom F# código.
ms.date: 12/10/2018
ms.openlocfilehash: 9f47257626e04b09b546de2ae315d48d791678be
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54030263"
---
# <a name="f-style-guide"></a>F#Guia de estilo

Os artigos a seguir descrevem as diretrizes de formatação F# código e tópicas orientação para recursos da linguagem e como eles devem ser usados.

Este guia foi formulado com base no uso de F# em grandes bases de código com um grupo diverso de programadores. Neste guia geralmente leva ao uso bem-sucedido do F# e minimiza as frustrações quando os requisitos para programas mudam ao longo do tempo.

## <a name="five-principles-of-good-f-code"></a>Cinco princípios bom F# código

Tenha os seguintes princípios em mente que sempre que você escrever F# código, especialmente em sistemas que irá alterar ao longo do tempo. Cada parte da orientação nos próximos artigos deriva essas cinco pontos.

1. **BOM F# código está sucinta, expressiva e passível de composição**

    F#tem muitos recursos que permitem que você expressar as ações em menos linhas de código e reutilizar a funcionalidade genérica. O F# biblioteca principal também contém vários tipos úteis e funções para trabalhar com coleções comuns de dados. Composição de suas próprias funções e aqueles no F# biblioteca principal (ou outras bibliotecas) é uma parte da rotina de expressões idiomática F# de programação. Como regra geral, se você puder expressar uma solução para um problema em menos linhas de código, outros desenvolvedores (ou seu futuro self) será apreciativo. É também é altamente recomendável que você use uma biblioteca como FSharp. Core, o [vastas bibliotecas do .NET](../../../api/index.md) que F# for executado, ou um pacote de produtos de terceiros no [NuGet](https://www.nuget.org/) quando você precisa executar uma tarefa não trivial.

2. **BOM F# código é interoperável**

    Interoperação pode levar várias formas, incluindo o consumo de código em linguagens diferentes. Os limites do que outros chamadores interoperam com código são partes essenciais para acertar, mesmo que os chamadores também estejam no F#. Ao escrever F#, você sempre deve estar pensando sobre como outro código chamará o código que você está escrevendo, incluindo se elas fazem isso de outra linguagem como C#. O [ F# diretrizes de Design do componente](component-design-guidelines.md) descrevem a interoperabilidade em detalhes.

3. **BOM F# código faz uso de programação de objeto, não do objeto orientação**

    F#tem suporte completo para a programação com objetos no .NET, incluindo [classes](../language-reference/classes.md), [interfaces](../language-reference/interfaces.md), [modificadores de acesso](../language-reference/access-control.md), [declassesabstratas](../language-reference/abstract-classes.md)e assim por diante. Para o código funcional mais complicado, como as funções que devem ser sensíveis ao contexto, objetos facilmente podem encapsular as informações contextuais de maneira que funções não podem. Recursos como [parâmetros opcionais](../language-reference/members/methods.md#optional-arguments) e o uso cuidadoso de [sobrecarga](../language-reference/members/methods.md#overloaded-methods) pode facilitar o consumo dessa funcionalidade para chamadores.

4. **BOM F# código executa bem sem expor a mutação**

    Não é segredo que, para escrever código de alto desempenho, você deve usar mutação. É como os computadores trabalham, afinal de contas. Esse código costuma ser difícil de acertar e propensas a erro. Evite a exposição de mutação aos chamadores. Em vez disso, [criar uma interface funcional que oculta uma implementação baseada em mutação](conventions.md#performance) quando o desempenho é crítico.

5. **BOM F# código é compatível com ferramentas**

    As ferramentas são inestimáveis para trabalhar em grandes bases de código, e você pode escrever F# de código, de modo que ele pode ser usado com mais eficiência com F# ferramentas de linguagem. Um exemplo é verificar se que você não exagere com um estilo livre de ponto de programação, para que os valores intermediários podem ser inspecionados com um depurador. Outro exemplo é o uso [comentários da documentação XML](../language-reference/xml-documentation.md) descrever construções, de modo que as dicas de ferramenta nos editores podem exibir esses comentários no site de chamada. Sempre pense sobre como seu código será ser ler, navegar, depurado e manipulado por outros programadores com suas ferramentas.

## <a name="next-steps"></a>Próximas etapas

O [ F# diretrizes de formatação de código](formatting.md) fornecem orientação sobre como formatar o código para que seja fácil de ler.

O [ F# convenções de codificação](conventions.md) fornecem orientação para F# que ajudarão a manutenção de longo prazo de maior linguagens de programação F# bases de código.

O [ F# diretrizes de design do componente](component-design-guidelines.md) fornecem diretrizes para criação de F# componentes, como bibliotecas.
