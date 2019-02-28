---
title: Tour do F#
description: Examine alguns dos principais recursos da linguagem em que este tour com exemplos de código de programação F#.
ms.date: 11/06/2018
ms.openlocfilehash: d741f7066517ad9bc004e2a89ba0d85a1d4c424d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968290"
---
# <a name="tour-of-f"></a>Tour do F\#

É a melhor maneira de saber mais sobre o F# ler e gravar o código F#. Este artigo atuará como um tour por alguns dos principais recursos da linguagem F# e lhe dar alguns trechos de código que pode ser executado em seu computador. Para saber mais sobre como configurar um ambiente de desenvolvimento, fazer check-out [Introdução ao](tutorials/getting-started/index.md).

Há dois conceitos principais em F#: tipos e funções.  Este tour será enfatizar os recursos da linguagem que se enquadram nesses dois conceitos.

## <a name="executing-the-code-online"></a>A execução do código online

Se você não tiver F# instalado em seu computador, você pode executar todas as amostras online com o [Fable REPL](https://fable.io/repl/). Fable é um dialeto do F# que é executado diretamente no seu navegador. Para exibir os exemplos que execute no REPL, fazer check-out **amostras > Saiba mais > Tour F#**  na barra de menu à esquerda do REPL Fable

## <a name="functions-and-modules"></a>Módulos e funções

São as partes mais fundamentais de qualquer programa em F# ***funções*** organizados em ***módulos***.  [Funções](language-reference/functions/index.md) realizar o trabalho em entradas para produzir saídas, e eles estão organizados sob [módulos](language-reference/modules.md), que são a principal maneira de agrupar as coisas em F#.  Eles são definidos usando o [ `let` associação](language-reference/functions/let-bindings.md), que dê um nome de função e definir seus argumentos.

[!code-fsharp[BasicFunctions](../../samples/snippets/fsharp/tour.fs#L101-L133)]

`let` associações são também como associar um valor para um nome semelhante a uma variável em outros idiomas.  `let` associações são ***imutável*** por padrão, que significa que depois que um valor ou uma função é associada a um nome, ele não pode ser alterado no local.  Isso é diferente de variáveis em outros idiomas, que são ***mutável***, que significa que seus valores pode ser alterada em qualquer ponto no tempo.  Se você precisar de uma associação mutável, você pode usar `let mutable ...` sintaxe.

[!code-fsharp[Immutability](../../samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a>Números, boolianos e cadeias de caracteres

Como uma linguagem .NET, F# oferece suporte à mesma subjacente [tipos primitivos](language-reference/primitive-types.md) que existem no .NET.

Aqui está como vários tipos numéricos são representados em F#:

[!code-fsharp[Numbers](../../samples/snippets/fsharp/tour.fs#L49-L68)]

Aqui está a quais valores booleanos e executar lógica condicional básica é semelhante a:

[!code-fsharp[Bools](../../samples/snippets/fsharp/tour.fs#L142-L152)]

E aqui está o que basic [cadeia de caracteres](language-reference/strings.md) manipulação se parece com:

[!code-fsharp[Strings](../../samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a>Tuplas

[As tuplas](language-reference/tuples.md) são muito importante em F#.  Eles são um agrupamento de valores sem nome, mas ordenados, que podem ser tratados como valores em si.  Pense neles como valores que são agregados dos outros valores.  Elas têm muitos usos, como convenientemente retornar vários valores de uma função ou agrupamento de valores para conveniência ad-hoc.

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L186-L203)]

A partir do F# 4.1, você também pode criar `struct` tuplas.  Eles também interoperam totalmente com C# 7/Visual Basic 15 tuplas, que também são `struct` tuplas:

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L205-L218)]

É importante observar que porque `struct` tuplas são tipos de valor, não pode ser convertidos implicitamente para referenciar as tuplas, ou vice-versa.  Você deve explicitamente converter entre uma tupla de referência e struct.

## <a name="pipelines-and-composition"></a>Pipelines e composição

Redirecionar operadores como `|>` são usadas amplamente durante o processamento de dados em F#. Esses operadores são funções que permitem que você estabeleça "pipelines" das funções de maneira flexível. O exemplo a seguir explica como você pode tirar proveito desses operadores para criar um pipeline funcional simples:

[!code-fsharp[Pipelines](../../samples/snippets/fsharp/tour.fs#L227-L282)]

O exemplo anterior feito uso de muitos recursos do F#, incluindo funções de processamento de lista, funções de primeira classe, e [aplicação parcial](language-reference/functions/index.md#partial-application-of-arguments). Embora uma compreensão profunda de cada um desses conceitos pode se tornar um pouco avançada, deve estar claro como facilmente as funções podem ser usadas para processar dados durante a criação de pipelines.

## <a name="lists-arrays-and-sequences"></a>Listas, matrizes e sequências

Listas, matrizes e sequências são três tipos de coleção principal na biblioteca de núcleo do F#.

[Lista](language-reference/lists.md) são imutáveis, ordenadas, coleções de elementos do mesmo tipo.  Eles são listas vinculadas individualmente, o que significa que eles servem para enumeração, mas uma boa opção para acesso aleatório e concatenação, se eles forem grandes.  Isso em contraste com listas em outras linguagens populares, que normalmente não usam uma lista individualmente vinculada para representar as listas.

[!code-fsharp[Lists](../../samples/snippets/fsharp/tour.fs#L309-L359)]

[Matrizes](language-reference/arrays.md) são de tamanho fixo *mutável* coleções de elementos do mesmo tipo.  Eles oferecem suporte ao acesso aleatório rápido de elementos e são mais rápidos do que listas do F# porque eles são contíguos apenas blocos de memória.

[!code-fsharp[Arrays](../../samples/snippets/fsharp/tour.fs#L368-L407)]

[Sequências de](language-reference/sequences.md) são uma série de lógica de elementos, todos do mesmo tipo.  Esses são um tipo mais geral de listas e matrizes, capazes de ser seu "exibição" em qualquer série lógica de elementos.  Eles também se destacam porque eles podem ser ***lento***, o que significa que elementos podem ser computados apenas quando eles forem necessários.

[!code-fsharp[Sequences](../../samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a>Funções Recursivas

Processamento de coleções ou sequências de elementos normalmente é feito com [recursão](language-reference/functions/index.md#recursive-functions) em F#.  Embora o F# tem suporte para loops e programação imperativa, a recursão é preferencial porque é mais fácil de garantir a correção.

> [!NOTE]
> O exemplo a seguir usa a correspondência de padrões por meio de `match` expressão.  Essa construção fundamental é abordada mais adiante neste artigo.

[!code-fsharp[RecursiveFunctions](../../samples/snippets/fsharp/tour.fs#L461-L500)]

F# também tem suporte completo para a otimização de chamada Tail, que é uma maneira de otimizar chamadas recursivas, para que eles são simplesmente tão rápidos quanto um constructo de loop.

## <a name="record-and-discriminated-union-types"></a>Registro e os tipos de união discriminados

Registro e tipos de união são dois tipos de dados fundamental usados no código F# e geralmente são a melhor maneira de representar dados em um programa em F#.  Embora isso os torna semelhante às classes em outras linguagens, uma das suas principais diferenças é que eles têm a semântica de igualdade estrutural.  Isso significa que eles são "nativo" comparáveis e igualdade é simples – basta verificar se uma é igual ao outro.

[Registros](language-reference/records.md) são uma agregação de valores nomeados, com membros opcionais (como os métodos).  Se você estiver familiarizado com c# ou Java, em seguida, esses devem se sentir semelhantes a POCOs ou POJOs - apenas com relação à igualdade estrutural e menos cerimônia.

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L507-L559)]

A partir do F# 4.1, você também pode representar os registros como `struct`s.  Isso é feito com o `[<Struct>]` atributo:

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L561-L568)]

[(DUs) de uniões discriminadas](language-reference/discriminated-unions.md) são valores que poderia ser um número de casos ou de formulários nomeados.  Dados armazenados no tipo podem ser um dos vários valores distintos.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L575-L631)]

Você também pode usar DUs como *uniões discriminadas de caso único*, para ajudá-lo ao longo de tipos primitivos de modelagem de domínio.  Muitas vezes, cadeias de caracteres e outros tipos primitivos são usados para representar algo e, portanto, terá um significado específico.  No entanto, usar apenas a primitiva representação dos dados pode resultar em, por engano, atribuir um valor incorreto!  Que representa cada tipo de informação como uma união distinta de caso único pode impor a exatidão nesse cenário.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L633-L654)]

Como demonstra o exemplo acima, para obter o valor subjacente em um único caso união discriminada, você deve explicitamente desencapsulá-lo.

Além disso, DUs também dão suporte a definições recursivas, permitindo que você facilmente representar árvores e inerentemente dados recursivos.  Por exemplo, aqui está como você pode representar uma árvore de pesquisa binária com `exists` e `insert` funções.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L656-L683)]

Como DUs permitem a você representar a estrutura recursiva da árvore no tipo de dados, operando sobre essa estrutura recursiva é simples e garante a exatidão.  Ele também é compatível com correspondência de padrões, conforme mostrado abaixo.

Além disso, você pode representar DUs como `struct`s com o `[<Struct>]` atributo:

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L685-L696)]

No entanto, há duas coisas principais para ter em mente ao fazer isso:

1. Uma DU struct não pode ser definido de forma recursiva.
2. Um struct DU deve ter nomes exclusivos para cada um dos seus casos.

Falha em seguir acima resultará em um erro de compilação.

## <a name="pattern-matching"></a>Correspondência padrão

[Correspondência de padrão](language-reference/pattern-matching.md) é o recurso da linguagem F# que permite que a correção para operar em tipos de F#.  Nos exemplos acima, você deve ter notado um pouco de `match x with ...` sintaxe.  Essa construção permite que o compilador, que possa entender a "forma" tipos de dados, para forçar a conta para todos os casos possíveis ao usar um tipo de dados por meio do que é conhecido como correspondência completa.  Isso é incrivelmente poderoso para exatidão e pode ser usado de maneira inteligente para "sobem" o que normalmente seria uma questão de tempo de execução em tempo de compilação.

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L705-L742)]

Você também pode usar a forma abreviada `function` constructo para correspondência de padrões, que é útil quando você estiver escrevendo usam funções que tornam [aplicativo parcial](language-reference/functions/index.md#partial-application-of-arguments):

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L744-L762)]

Algo que talvez você tenha notado é que o uso do `_` padrão.  Isso é conhecido como o [padrão de curinga](language-reference/pattern-matching.md#wildcard-pattern), que é uma maneira de dizer que "Não me preocupo com o que é algo".  Embora seja conveniente, você pode ignorar acidentalmente correspondência completa e poderá se beneficiar das imposições de tempo de compilação, se você não tiver cuidado usando `_`.  Ele é melhor usado quando não se preocupa determinadas partes de um tipo decomposto ao padrão de correspondência ou a cláusula final quando você tiver enumerada de todos os casos significativos em uma expressão de correspondência.

[Padrões ativos](language-reference/active-patterns.md) são outra construção avançada para usar com correspondência de padrões.  Eles permitem que você particione os dados de entrada em formulários personalizados, decompô-los no site de chamada de correspondência de padrão.  Eles também podem ser parametrizados, permitindo, portanto, para definir a partição como uma função.  Expandir o exemplo anterior para dar suporte a padrões ativos é semelhante a:

[!code-fsharp[ActivePatterns](../../samples/snippets/fsharp/tour.fs#L764-L786)]

## <a name="optional-types"></a>Tipos opcionais

Um caso especial de tipos de união discriminada é o tipo de opção, que é tão útil que é uma parte da biblioteca principal F#.

[O tipo de opção](language-reference/options.md) é um tipo que representa um dos dois casos: um valor ou nada em todas.  Ele é usado em qualquer cenário em que um valor pode ou não pode resultar de uma determinada operação.  Em seguida, isso força você levar em conta para ambos os casos, tornando-o uma preocupação de tempo de compilação em vez de um problema de tempo de execução.  Eles geralmente são usados nas APIs em que `null` é usado para representar "nada" em vez disso, eliminando a necessidade de se preocupar sobre `NullReferenceException` em muitas circunstâncias.

[!code-fsharp[Options](../../samples/snippets/fsharp/tour.fs#L789-L814)]

## <a name="units-of-measure"></a>Unidades de medida

Um recurso exclusivo do sistema de tipos do F# é a capacidade de fornecer contexto para literais numéricos por meio de unidades de medida.

[Unidades de medida](language-reference/units-of-measure.md) permitem que você associe um tipo numérico para uma unidade, como metros, e ter funções de realizar o trabalho em unidades, em vez de literais numéricos.  Isso permite que o compilador verificar se os tipos de literais numéricos passados no sentido em um determinado contexto, eliminando assim a erros de tempo de execução associado a esse tipo de trabalho.

[!code-fsharp[UnitsOfMeasure](../../samples/snippets/fsharp/tour.fs#L817-L842)]

A biblioteca de F# Core define muitos tipos de unidade de SI e conversões de unidade.  Para saber mais, confira a [Namespace Microsoft.FSharp.Data.UnitSystems.SI](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d).

## <a name="classes-and-interfaces"></a>Classes e Interfaces

F# também tem suporte completo para classes do .NET [Interfaces](language-reference/interfaces.md), [Classes abstratas](language-reference/abstract-classes.md), [herança](language-reference/inheritance.md)e assim por diante.

[As classes](language-reference/classes.md) são tipos que representam objetos .NET, que pode ter propriedades, métodos e eventos como seus [membros](language-reference/members/index.md).

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L845-L880)]

Definir classes genéricas também é muito simples.

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L883-L908)]

Para implementar uma Interface, você pode usar `interface ... with` sintaxe ou um [expressão de objeto](language-reference/object-expressions.md).

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L911-L934)]

## <a name="which-types-to-use"></a>Quais tipos de uso

A presença de Classes, registros, uniões discriminadas e tuplas leva a uma pergunta importante: que você deve usar?  Como tudo na vida, a resposta depende de suas circunstâncias.

As tuplas são ótimas para retornar vários valores de uma função e usando uma agregação de ad hoc de valores como um valor em si.

Os registros são um "passo" de tuplas, ter chamado rótulos e suporte para membros opcionais.  Eles são ótimos para uma representação informal de dados em trânsito por meio de seu programa.  Porque eles têm igualdade estrutural, eles são fáceis de usar com a comparação.

As uniões discriminadas têm muitos usos, mas o benefício principal é poder utilizá-las em conjunto com a correspondência de padrão para levar em conta todas as possíveis "formas" que uma data pode ter.  

As classes são ótimas para um grande número de motivos, como quando for necessário representar informações e também vincular essas informações à funcionalidade.  Como regra geral, quando você tem funcionalidade que conceitualmente está associada a alguns dados, usando Classes e os princípios da programação orientada a objeto é uma grande vantagem.  As classes também são o tipo de dados preferencial ao interoperar com c# e Visual Basic, como esses idiomas usam classes para quase tudo.

## <a name="next-steps"></a>Próximas etapas

Agora que você viu alguns dos principais recursos da linguagem, você deve estar pronto para gravar seus programas em F# primeiro!  Fazer check-out [guia de Introdução](tutorials/getting-started/index.md) para aprender a configurar seu ambiente de desenvolvimento e escrever algum código.

As próximas etapas para aprender mais podem ser que você quiser, mas recomendamos [Introdução à programação funcional no F# ](introduction-to-functional-programming/index.md) para que fique à vontade com os principais conceitos de programação funcional.  Eles estarão essenciais na criação de programas robustos em F#.

Além disso, confira a [referência da linguagem F#](language-reference/index.md) para ver um conjunto abrangente de conteúdo conceitual em F#.
