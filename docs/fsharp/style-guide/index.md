---
title: 'Guia de estilo do F #'
description: 'Aprenda os cinco princípios de BOM código F #.'
ms.date: 05/14/2018
ms.openlocfilehash: 6d8c1336ca991040a8f6e13290d209cb3b70054d
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="f-style-guide"></a>Guia de estilo do F #

Os artigos a seguir descrevem as diretrizes de formatação de código F # e orientação de um tópico de interesse para recursos do idioma e como eles devem ser usados.

Este guia foi formulado com base no uso da linguagem F # em grandes bases de código com um grupo diverso de programadores. Este guia geralmente leva para uso bem-sucedido do F # e minimiza frustrações quando requisitos para programas alterarem ao longo do tempo.

## <a name="five-principles-of-good-f-code"></a>Cinco princípios de BOM código F #

Você deve ter os seguintes princípios em mente que sempre que você escrever código F #, especialmente em sistemas que irá alterar ao longo do tempo. Cada parte da orientação mais artigos deriva esses cinco pontos.

1. **BOM código F # é sucinta e expressivas**

    F # tem muitos recursos que permitem que você expressam ações em menos linhas de código e reutilizar a funcionalidade genérica. A biblioteca principal F # também contém vários tipos úteis e funções para trabalhar com coleções comuns de dados. Como regra geral, se você pode expressar uma solução para um problema em menos linhas de código, outros desenvolvedores (ou seu self futuras) será apreciativo. É também recomendável que você use uma biblioteca como FSharp. Core, o [grandes bibliotecas do .NET](https://docs.microsoft.com/dotnet/api/) que F # é executado, ou um pacote de terceiros em [NuGet](https://www.nuget.org/) quando você precisa executar uma tarefa não trivial.

2. **BOM código F # é interoperável**

    Interoperação pode levar várias formas, incluindo o código em idiomas diferentes de consumo. Os limites de seu código que outros chamadores interoperam com são partes essenciais de acertar. Ao escrever F #, você deve sempre ser pensando sobre como outro código chamará o código que você está escrevendo, incluindo se eles fazem isso de outra linguagem como c#. O [diretrizes de Design do componente de F #](component-design-guidelines.md) descrevem interoperabilidade em detalhes.

3. **BOM código F # torna o uso de programação do objeto, não do objeto orientação**

    F # tem total suporte para programação com objetos no .NET, incluindo [classes](../language-reference/classes.md), [interfaces](../language-reference/interfaces.md), [modificadores de acesso](../language-reference/access-control.md), [declassesabstratas](../language-reference/abstract-classes.md), e assim por diante. Para o código funcional mais complicado, como as funções que deve estar ciente ao contexto, objetos podem encapsular facilmente informações contextuais de maneiras que não é possível funções. Recursos como [parâmetros opcionais](../language-reference/members/methods.md#optional-arguments) e [sobrecarga](../language-reference/members/methods.md#overloaded-methods) também ajudam a consumo dessa funcionalidade para chamadores.

4. **Executa código F # bom bem sem expor mutação**

    Não é um segredo que para escrever código de alto desempenho, você deve usar mutação. É como computadores de trabalho, depois que todos os. Esse código é geralmente propensas a erros e difícil de acertar. Evite a exposição de mutação para chamadores. Busca de uma interface funcional em uma implementação baseada em mutação.

5. **BOM código F # é editável**

    Ferramentas são imprescindíveis para trabalhar em grandes bases de código, você pode escrever código F #, de modo que ele pode ser usado com mais eficiência com ferramentas de linguagem F #. Um exemplo é verificar se que você não exagerar com um estilo livre de ponto de programação, para que os valores intermediários podem ser inspecionados com um depurador. Outro exemplo é o uso [comentários de documentação XML](../language-reference/xml-documentation.md) descrevendo construções de modo que as dicas de ferramenta em editores podem exibir esses comentários no site de chamada. Sempre pense em como seu código será lido, navegar, depurado e manipulado por outros programadores com suas ferramentas.

## <a name="next-steps"></a>Próximas etapas

O [código F # diretrizes de formatação](formatting.md) fornecem orientação sobre como formatar o código para que seja fácil de ler.

O [convenções de codificação do F #](conventions.md) fornecem orientação para ajudar a manutenção de longo prazo de maior F # linguagens de programação do F # bases de código.

O [diretrizes de design do componente F #](component-design-guidelines.md) fornecem diretrizes para criação de F # componentes, como bibliotecas.
