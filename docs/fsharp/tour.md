---
title: 'Tour do F #'
description: "Examine alguns dos principais recursos do F # linguagem em que este tour com exemplos de código de programação."
keywords: "o Visual f #, f #, funcional programação .NET, tour"
author: cartermp
ms.author: phcart
ms.date: 02/28/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 49775139-082e-442f-b5a2-dd402399b5d2
ms.openlocfilehash: 7327573a25aa62af28570b4a8662235f3e41a972
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="tour-of-f"></a>Tour do F # #

É a melhor maneira de saber mais sobre F # ler e gravar código F #.  Este artigo atuará como um tour por meio de alguns dos principais recursos da linguagem F # e lhe alguns trechos de código que você pode executar em seu computador.  Para obter informações sobre como configurar um ambiente de desenvolvimento, confira [Introdução](tutorials/getting-started/index.md).

Há dois principais conceitos em F #: tipos e funções.  Este tour concentrar recursos da linguagem que se enquadram nesses dois conceitos.

## <a name="functions-and-modules"></a>Módulos e funções

As partes mais fundamentais de qualquer programa do F # são ***funções*** organizados em ***módulos***.  [Funções](language-reference/functions/index.md) realizar o trabalho em entradas para produzir saídas, e eles estão organizados sob [módulos](language-reference/modules.md), que são a principal maneira de agrupar itens em F #.  Eles são definidos usando o [ `let` associação](language-reference/functions/let-bindings.md), que dê um nome de função e definir seus argumentos.

[!code-fsharp[BasicFunctions](../../samples/snippets/fsharp/tour.fs#L101-L133)]

`let` as associações são também como associar um valor para um nome semelhante a uma variável em outros idiomas.  `let` as associações são ***imutável*** por padrão, que significa que quando um valor ou uma função é associada a um nome, não pode ser alterado no local.  Isso é diferente de variáveis em outros idiomas, que são ***mutável***, que significa que seus valores pode ser alterada em qualquer ponto no tempo.  Se você precisar de uma associação mutável, você pode usar `let mutable ...` sintaxe.

[!code-fsharp[Immutability](../../samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a>Números, valores booleanos e cadeias de caracteres

Como uma linguagem .NET, F # suporta subjacente mesmo [tipos primitivos](language-reference/primitive-types.md) que existe no .NET.

Aqui está como vários tipos numéricos são representados em F #:

[!code-fsharp[Numbers](../../samples/snippets/fsharp/tour.fs#L49-L68)]

É aqui que valores booleanos e executar lógica condicional básica se parece com:

[!code-fsharp[Bools](../../samples/snippets/fsharp/tour.fs#L142-L152)]

E aqui está o basic [cadeia de caracteres](language-reference/strings.md) manipulação se parece com:

[!code-fsharp[Strings](../../samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a>Tuplas

[Tuplas](language-reference/tuples.md) são um grande problema em F #.  Eles são um agrupamento de valores sem nome, mas ordenados, que podem ser tratados como os próprios valores.  Considere-los como valores que são agregados de outros valores.  Elas têm muitos usos, como convenientemente retornar vários valores de uma função ou agrupar valores para algumas conveniência ad-hoc.

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L186-L203)]

A partir do F # 4.1, você também pode criar `struct` tuplas.  Eles também interoperam totalmente com C# 7/Visual Basic 15 tuplas, que também são `struct` tuplas:

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L205-L218)]

É importante observar que porque `struct` tuplas são tipos de valor, não pode ser convertidas implicitamente para fazer referência tuplas, ou vice-versa.  Você deverá converter explicitamente entre uma tupla de referência e struct.

## <a name="pipelines-and-composition"></a>Pipelines e composição

Redirecionar operadores (`|>`, `<|`, `||>`, `<||`, `|||>`, `<|||`) e os operadores de composição (`>>` e `<<`) forem usados extensivamente durante o processamento de dados em F #.  Esses operadores são funções que permitem que você estabeleça "pipelines" das funções de forma flexível.  O exemplo a seguir explica como você pode tirar proveito desses operadores para criar um pipeline funcional simple.

[!code-fsharp[Pipelines](../../samples/snippets/fsharp/tour.fs#L227-L300)]

O exemplo acima feito usar muitos recursos do F #, incluindo funções de processamento de lista, funções de primeira classe, e [aplicativo parcial](language-reference/functions/index.md#partial-application-of-arguments).  Embora uma profunda compreensão de cada um desses conceitos pode ficar um pouco avançada, deve estar claro como facilmente as funções podem ser usadas para processar dados durante a criação de pipelines.

## <a name="lists-arrays-and-sequences"></a>Listas, matrizes e sequências

Listas, matrizes e sequências são três tipos de coleção principal da biblioteca principal F #.

[Lista](language-reference/lists.md) são coleções imutáveis, ordenadas de elementos do mesmo tipo.  São listas vinculadas individualmente, o que significa que eles se destinam para enumeração, mas uma boa opção para acesso aleatório e concatenação se eles forem grandes.  Isso, ao contrário de listas em outros idiomas populares, que normalmente não usam uma lista individualmente vinculada para representar listas.

[!code-fsharp[Lists](../../samples/snippets/fsharp/tour.fs#L309-L359)]

[Matrizes](language-reference/arrays.md) são de tamanho fixo, *mutável* coleções de elementos do mesmo tipo.  Eles oferecem suporte a acesso aleatório rápido de elementos e são mais rápidos de F # lista porque são contíguos apenas blocos de memória.

[!code-fsharp[Arrays](../../samples/snippets/fsharp/tour.fs#L368-L407)]

[Sequências](language-reference/sequences.md) são uma série de lógica de elementos, todos do mesmo tipo.  Essas são um tipo mais geral de listas e matrizes, capazes de ser seu "view" em qualquer série de lógica de elementos.  Eles também destacam porque eles podem ser ***lento***, o que significa que os elementos podem ser computados apenas quando eles são necessários.

[!code-fsharp[Sequences](../../samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a>Funções Recursivas

Coleções ou sequências de elementos de processamento normalmente é feito com [recursão](language-reference/functions/index.md#recursive-functions) em F #.  Embora o F # tem suporte para programação imperativa e loops, recursão é preferencial porque é mais fácil de garantir a correção.

>[!NOTE]
O exemplo a seguir usa a correspondência de padrão por meio de `match` expressão.  Esta construção fundamental é abordada posteriormente neste artigo.

[!code-fsharp[RecursiveFunctions](../../samples/snippets/fsharp/tour.fs#L461-L500)]

F # também tem suporte completo para a otimização de chamada Tail, que é uma maneira de otimizar a chamadas recursivas para que eles são apenas tão rápidos quanto uma construção de loop.

## <a name="record-and-discriminated-union-types"></a>Registro e tipos de união discriminados

Registro de tipos de união dois tipos de dados fundamentais usados no código F # e são geralmente são a melhor maneira de representar dados em um programa em F #.  Embora isso os torna similar a classes em outros idiomas, uma das suas principais diferenças é que eles têm a semântica de igualdade estrutural.  Isso significa que eles são comparáveis "nativo" e igualdade é simples - apenas verifique se uma é igual ao outro.

[Registros](language-reference/records.md) são uma agregação de valores nomeados, com membros opcionais (como métodos).  Se você estiver familiarizado com c# ou Java, em seguida, esses devem ser semelhantes a POCOs ou POJOs - apenas com igualdade estrutural e menos cerimônia.

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L507-L559)]

A partir do F # 4.1, você também pode representar registros como `struct`s.  Isso é feito com o `[<Struct>]` atributo:

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L561-L568)]

[Discriminada uniões (DUs)](language-reference/discriminated-unions.md) são valores que podem ser um número de formulários nomeados ou casos.  Os dados armazenados no tipo podem ser um dos vários valores distintos.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L575-L631)]

Você também pode usar DUs como *único caso discriminada uniões*, para ajudá-lo com o domínio de modelagem em tipos primitivos.  Muitas vezes, cadeias de caracteres e outros tipos primitivos são usados para representar algo e, portanto, recebem um significado específico.  No entanto, usando apenas a primitivo representação dos dados pode resultar em por engano atribuir um valor incorreto!  Que representa cada tipo de informação como uma união distinta de único caso pode impor exatidão neste cenário.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L633-L654)]

Como mostra o exemplo acima, para obter o valor subjacente em um único caso discriminada Union, deve descompactá-lo explicitamente.

Além disso, DUs também oferece suporte definições recursiva, permitindo que você facilmente representar árvores e inerentemente dados recursivos.  Por exemplo, aqui está como você pode representar uma árvore binária de pesquisa com `exists` e `insert` funções.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L656-L683)]

Como permitir DUs representar a estrutura recursiva da árvore no tipo de dados, operando nessa estrutura recursiva é simples e garante a exatidão.  Ele também é compatível com a correspondência de padrões, conforme mostrado abaixo.

Além disso, você pode representar DUs como `struct`s com o `[<Struct>]` atributo:

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L685-L696)]

No entanto, há duas coisas chave para ter em mente ao fazer isso:

1. Uma estrutura DU não pode ser definido de forma recursiva.
2. Uma estrutura DU deve ter nomes exclusivos para cada um dos seus casos.

Falha ao seguir acima resultará em um erro de compilação.

## <a name="pattern-matching"></a>Correspondência padrão

[Correspondência de padrões](language-reference/pattern-matching.md) é o recurso de linguagem F # que permite que a correção para a operação em tipos F #.  Nos exemplos acima, você deve ter notado bastante `match x with ...` sintaxe.  Esta construção permite que o compilador, que possa compreender "forma" dos tipos de dados, para forçar a conta para todos os casos possíveis ao usar um tipo de dados por meio de que é conhecido como correspondência de padrões completa.  Isso é incrivelmente poderoso para correção e pode ser usado inteligentemente para "retire", o que normalmente seria um problema de tempo de execução em tempo de compilação.

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L705-L739)]

Você também pode usar a abreviação `function` construção para correspondência de padrões, que é útil quando você está escrevendo funções que façam usam de [aplicativo parcial](language-reference/functions/index.md#partial-application-of-arguments):

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L741-L759)]

Algo que você pode ter observado é o uso do `_` padrão.  Isso é conhecido como o [padrão de curinga](language-reference/pattern-matching.md#wildcard-pattern), que é uma forma de dizer ", não é importante que algo está".  Embora seja conveniente, você pode ignorar acidentalmente exaustiva correspondência de padrão e poderá se beneficiar das imposições de tempo de compilação, se você não tiver cuidado usando `_`.  Ele é mais adequado quando não se preocupa determinadas partes de um tipo decomposto quando padrão de correspondência ou a cláusula final quando tiverem enumerados todos os casos significativos em uma expressão de correspondência de padrões.

[Padrões ativos](language-reference/active-patterns.md) são outra construção avançada para usar com a correspondência de padrões.  Elas permitem que você particionar os dados de entrada em formulários personalizados, decompondo-los no site de chamada de correspondência de padrão.  Eles podem também ser parametrizados, permitindo, assim, para definir a partição como uma função.  Expandir o exemplo anterior para dar suporte a padrões ativos parecida com esta:

[!code-fsharp[ActivePatterns](../../samples/snippets/fsharp/tour.fs#L761-L783)]

## <a name="optional-types"></a>Tipos opcionais

Um caso especial de tipos de união discriminada é o tipo de opção, que é tão útil que ele faz parte da biblioteca principal F #.

[O tipo de opção](language-reference/options.md) é um tipo que representa um dos dois casos: um valor ou nada em todos os.  Ele é usado em qualquer cenário em que um valor pode ou não pode resultar de uma operação específica.  Isso força a conta para ambos os casos, tornando-o um problema de tempo de compilação em vez de um problema de tempo de execução.  Eles geralmente são usados nas APIs onde `null` é usada para representar "nada" em vez disso, eliminando a necessidade de se preocupar sobre `NullReferenceException` em muitas circunstâncias.

[!code-fsharp[Options](../../samples/snippets/fsharp/tour.fs#L791-L811)]

## <a name="units-of-measure"></a>Unidades de medida

Um recurso exclusivo do sistema de tipo do F # é a capacidade de fornecer contexto para literais numéricos por meio de unidades de medida.

[Unidades de medida](language-reference/units-of-measure.md) permitem que você associe um tipo numérico para uma unidade, por exemplo, medidores, e ter funções de executar o trabalho em unidades em vez de literais numéricos.  Isso permite que o compilador verificar se os tipos de literais numéricos passados fazem sentido em um determinado contexto, eliminando assim a erros de tempo de execução associado a esse tipo de trabalho.

[!code-fsharp[UnitsOfMeasure](../../samples/snippets/fsharp/tour.fs#L818-L839)]

A biblioteca principal F # define vários tipos de unidade de SI e conversões de unidade.  Para saber mais, confira o [Namespace Microsoft.FSharp.Data.UnitSystems.SI](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d).

## <a name="classes-and-interfaces"></a>Classes e Interfaces

F # também oferece suporte para classes do .NET, [Interfaces](language-reference/interfaces.md), [Classes abstratas](language-reference/abstract-classes.md), [herança](language-reference/inheritance.md)e assim por diante.

[Classes de](language-reference/classes.md) são tipos que representam objetos .NET, que pode ter propriedades, métodos e eventos como seu [membros](language-reference/members/index.md).

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L848-L877)]

Definir classes genéricas também é muito simples.

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L884-L905)]

Para implementar uma Interface, você pode usar `interface ... with` sintaxe ou um [expressão de objeto](language-reference/object-expressions.md).

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L912-L931)]

## <a name="which-types-to-use"></a>Quais tipos de uso

A presença de Classes, registros, uniões discriminada e tuplas leva a uma pergunta importante: que você deve usar?  Como a maioria dos tudo na vida, a resposta depende de suas circunstâncias.

Tuplas são ótimas para retornar vários valores de uma função e usar uma agregação ad hoc de valores como um valor em si.

Os registros são um "step up" de tuplas, ter chamado rótulos e suporte para membros opcionais.  Eles são ótimos para uma representação de cerimônia de baixa de dados em trânsito por meio de seu programa.  Como eles têm igualdade estrutural, eles são fáceis de usar com a comparação.

Uniões discriminadas têm muitos usos, mas o benefício principal é poder utilizá-las em conjunto com a correspondência de padrão para levar em conta todas as possíveis "formas" que pode ter uma data.  

Classes são ótimas para um grande número de motivos, como quando você precisa que representam informações e também vincular essas informações para a funcionalidade.  Como regra geral, quando você tem funcionalidade que conceitualmente estiver associada a alguns dados, usando Classes e os princípios de programação Oriented é uma grande vantagem.  Classes também são o tipo de dados preferencial ao interagir com c# e Visual Basic, como essas linguagens usam classes para quase tudo.

## <a name="next-steps"></a>Próximas etapas

Agora que você viu alguns dos principais recursos do idioma, você estará pronto para escrever seu primeiro programas F #!  Check-out [Introdução](tutorials/getting-started/index.md) para aprender a configurar seu ambiente de desenvolvimento e escrever um código.

As próximas etapas para aprender mais podem ser como desejar, mas é recomendável [funciona como valores de primeira classe](introduction-to-functional-programming/functions-as-first-class-values.md) <!--[Introduction to Functional Programming in F#](introduction-to-functional-programming/index.md)--> obter familiarizado com os principais conceitos de programação funcional.  Esses serão essenciais na criação de programas eficientes em F #.

Além disso, confira o [referência da linguagem F #](language-reference/index.md) para ver uma coleção abrangente de conteúdo conceitual em F #.
