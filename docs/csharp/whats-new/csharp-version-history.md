---
title: O histórico da linguagem C# – Guia do C#
description: Qual era a aparência da linguagem nas primeiras versões e como ela evoluiu desde então?
author: erikdietrich
ms.date: 09/20/2017
ms.openlocfilehash: 3e3bf98d1435b237b2941758b8ed245baa970237
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207528"
---
# <a name="the-history-of-c"></a>O histórico da linguagem C# #

Qual era a aparência da linguagem nas primeiras versões? E como ela evoluiu com o passar dos anos?

## <a name="c-version-10"></a>C# versão 1.0

Ao olhar para o passado, a C# versão 1.0 parecia muito com o Java. Como [parte de suas metas de design declaradas para ECMA](http://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html), ela buscava ser uma "linguagem simples, moderna, de uso geral e orientada a objeto".  No momento, parece que o Java alcançou essas metas de design iniciais.

Mas agora, se examinar novamente a C# 1.0, você poderá se sentir um pouco confuso. Ela não tinha os recursos internos assíncronos nem algumas das funcionalidades úteis relacionadas a genéricos que costumam estar presentes. Na verdade, ela não tinha nada relacionado a genéricos.  E a [LINQ](../linq/index.md)? Ainda não estava disponível. Essas adições levariam anos para serem lançadas.

A versão 1.0 do C# parecia ter poucos recursos, em comparação com os dias de hoje. Você teria que escrever código um tanto detalhado. Mas, ainda assim, você poderia iniciar em algum lugar. A versão 1.0 do C# era uma alternativa viável ao Java na plataforma Windows.

Os principais recursos do C# 1.0 incluíam:

- [Classes](../programming-guide/classes-and-structs/classes.md)
- [Estruturas](../programming-guide/classes-and-structs/structs.md)
- [Interfaces](../programming-guide/interfaces/index.md)
- [Eventos](../events-overview.md)
- [Propriedades](../properties.md)
- [Delegados](../delegates-overview.md)
- [Expressões](../programming-guide/statements-expressions-operators/expressions.md)
- [Instruções](../programming-guide/statements-expressions-operators/statements.md)
- [Atributos](../programming-guide/concepts/attributes/index.md)
- Literais

## <a name="c-version-20"></a>C# versão 2.0

Neste momento, as coisas começam a ficar interessantes. Vamos dar uma olhada em alguns recursos principais do C# 2.0, lançado em 2005, junto com o Visual Studio 2005:

- [Genéricos](../programming-guide/generics/index.md)
- [Tipos parciais](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [Métodos anônimos](../programming-guide/statements-expressions-operators/anonymous-methods.md)
- [Tipos que permitem valor nulo](../programming-guide/nullable-types/index.md)
- [Iteradores](../programming-guide/concepts/iterators.md)
- [Covariância e contravariância](../programming-guide/concepts/covariance-contravariance/index.md)

Outros recursos do C# 2.0 adicionaram funcionalidades a recursos existentes:

- Acessibilidade separada getter/setter
- Conversões de grupo de método (delegados)
- Classes estáticas
- Inferência de delegado

Embora C# possa ter começado como uma linguagem OO (orientada a objeto) genérica, a versão 2.0 do C# tratou de mudar isso rapidamente. Depois de se acostumarem com a ideia da linguagem OO, os desenvolvedores começaram a sofrer com vários pontos problemáticos graves. E tentaram resolver os problemas de maneira significativa.

Com genéricos, tipos e métodos, é possível operar em um tipo arbitrário e, ao mesmo tempo, manter a segurança de tipos. Por exemplo, ter um <xref:System.Collections.Generic.List%601> permite que você tenha `List<string>` ou `List<int>` e execute operações fortemente tipadas nessas cadeias de caracteres ou inteiros enquanto itera neles. Usar genéricos é melhor que criar `ListInt` que deriva de `ArrayList` ou converter de `Object` para cada operação.

A versão 2.0 do C# trouxe iteradores. Em resumo, o iteradores permitem que você examine todos os itens em um `List` (ou outros tipos Enumeráveis) com um loop `foreach`. Ter iteradores como uma parte importante da linguagem aprimorou de forma impressionante a legibilidade da linguagem e a capacidade das pessoas de raciocinar a respeito do código.

E ainda assim, o C# continuava na tentativa de alcançar o mesmo nível do Java. O Java já tinha liberado versões que incluíam genéricos e iteradores. Mas isso seria alterado logo, pois as linguagens continuaram a evoluir separadamente.

## <a name="c-version-30"></a>C# versão 3.0

O C# versão 3.0 chegou no final de 2007, juntamente com o Visual Studio 2008, porém o pacote completo de recursos de linguagem veio, na verdade, com o C# versão 3.5. Esta versão foi o marco de uma alteração significativa no crescimento do C#. Ela estabeleceu o C# como uma linguagem de programação realmente formidável. Vamos dar uma olhada em alguns recursos importantes nesta versão:

- [Propriedades autoimplementadas](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [Tipos anônimos](../programming-guide/classes-and-structs/anonymous-types.md)
- [Expressões de consulta](../linq/query-expression-basics.md)
- [Expressão lambda](https://www.daedtech.com/introduction-to-c-lambda-expressions/)
- [Árvores de expressão](https://blogs.msdn.microsoft.com/charlie/2008/01/31/expression-tree-basics/)
- [Métodos de extensão](https://www.codeproject.com/Tips/709310/Extension-Method-In-Csharp)
- [Variáveis locais implicitamente tipadas](../language-reference/keywords/var.md)
- [Métodos parciais](../language-reference/keywords/partial-method.md)
- Inicializadores de coleção e de objeto

Numa retrospectiva, muitos desses recursos parecerem inevitáveis e inseparáveis. Todos eles se encaixam estrategicamente. Costuma-se pensar que o recurso irresistível dessa versão do C# foi a expressão de consulta, também conhecida como LINQ (consulta integrada à linguagem).

Uma exibição mais detalhada analisa árvores de expressão, expressões lambda e tipos anônimos como a base na qual o LINQ é construído. Mas, de uma forma ou de outra, o C# 3.0 apresentou um conceito revolucionário. O C# 3.0 começou a definir as bases para transformar o C# em uma linguagem híbrida orientada a objeto e funcional.

Especificamente, agora você pode escrever consultas declarativas no estilo SQL para executar operações em coleções, entre outras coisas. Em vez de escrever um loop `for` para calcular a média de uma lista de inteiros, agora você pode fazer isso simplesmente como `list.Average()`. A combinação de expressões de consulta e métodos de extensão fez parecer que essa lista de inteiros se tornasse muito mais inteligente.

Levou algum tempo para que as pessoas entendessem e integrassem o conceito, mas isso aconteceu gradualmente. E agora, anos mais tarde, o código é muito mais conciso, simples e funcional.

## <a name="c-version-40"></a>C# versão 4.0

O C# versão 4.0 enfrentou dificuldades para sobreviver ao status inovador da versão 3.0. Com a versão 3.0, o C# tirou verdadeiramente a linguagem da sombra do Java e a colocou em proeminência. A linguagem foi rapidamente se tornando elegante.

A próxima versão introduziu alguns novos recursos interessantes:

- [Associação dinâmica](../language-reference/keywords/dynamic.md)
- [Argumentos opcionais/nomeados](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Genérico covariante e contravariante](../../standard/generics/covariance-and-contravariance.md)
- [Tipos de interoperabilidade inseridos](https://stackoverflow.com/questions/20514240/whats-the-difference-setting-embed-interop-types-true-and-false-in-visual-studi)

Os tipos de interoperabilidade inseridos atenuaram um problema de implantação. A contravariância e a covariância genérica oferecem maior capacidade para usar genéricos, mas eles são um tanto acadêmicos e provavelmente mais apreciados por autores de estruturas e bibliotecas. Os parâmetros nomeados e opcionais permitem eliminar várias sobrecargas de método e oferecem conveniência. Mas nenhum desses recursos é exatamente uma alteração de paradigma.

O recurso principal foi a introdução da palavra-chave `dynamic`. A palavra-chave `dynamic` introduziu na versão 4.0 do C# a capacidade de substituir o compilador na tipagem em tempo de compilação. Com o uso da palavra-chave dinâmica, você pode criar constructos semelhantes a linguagens dinamicamente tipadas, como JavaScript. Você pode criar um `dynamic x = "a string"` e, em seguida, adicionar seis a ela, deixando que o tempo de execução decida o que acontece em seguida.

A associação dinâmica pode induzi-lo a erros, mas também é bastante eficaz na linguagem.

## <a name="c-version-50"></a>C# versão 5.0

O C# versão 5.0 era uma versão focada da linguagem. Quase todo o esforço para essa versão foi dedicado a outro conceito inovador de linguagem: os modelos `async` e `await` para programação assíncrona.  Aqui está a lista dos recursos principais:

- [Membros assíncronos](../async.md)
- [Atributos de informações do chamador](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

O atributo de informações do chamador permite facilmente recuperar informações sobre o contexto no qual você está executando sem recorrer a uma infinidade de código de reflexão clichê. Ele tem muitos usos em diagnóstico e tarefas de registro em log.

Mas `async` e `await` são as verdadeiras estrelas dessa versão. Quando esses recursos foram lançados em 2012, o C# virou o jogo novamente, implantando a assincronia na linguagem como uma participante da maior importância. Se você já teve que lidar com operações de longa execução e a implementação de redes de retorno de chamada, você provavelmente adorou esse recurso de linguagem.

## <a name="c-version-60"></a>C# versão 6.0

Nas versões 3.0 e 5.0, o C# recebeu alguns novos recursos importantes em uma linguagem orientada a objeto. Na versão 6.0, em vez de introduzir apenas um recurso principal dominante, foram liberados vários recursos menores que tornaram a programação em C# mais produtiva. Aqui estão alguns deles:

- [Importações estáticas](../language-reference/keywords/using-static.md)
- [Filtros de exceção](https://www.thomaslevesque.com/2015/06/21/exception-filters-in-c-6/)
- [Inicializadores de propriedade](http://geekswithblogs.net/WinAZ/archive/2015/06/30/whatrsquos-new-in-c-6.0-auto-property-initializers.aspx)
- [Membros aptos para expressão](https://lostechies.com/jimmybogard/2015/12/17/c-6-feature-review-expression-bodied-function-members/)
- [Propagador nulo](https://davefancher.com/2014/08/14/c-6-0-null-propagation-operator/)
- [Interpolação de cadeia de caracteres](../language-reference/tokens/interpolated.md)
- [Operador nameof](https://stackoverflow.com/questions/31695900/what-is-the-purpose-of-nameof)
- [Inicializadores de índice](csharp-6.md#index-initializers)

Outros novos recursos incluem:

- Await em blocos catch/finally
- Valores padrão para propriedades somente getter

Cada um desses recursos é interessante em seus próprios méritos. Mas, se você os observar em conjunto, verá um padrão interessante. Nesta versão, o C# eliminou o clichê de linguagem para tornar o código mais conciso e legível. Portanto, para os fãs de código simples e conciso, essa versão da linguagem foi um grande benefício.

Fizeram ainda outra coisa com esta versão, embora não seja um recurso de linguagem tradicional em si. Lançaram [Roslyn, o compilador como um serviço](https://github.com/dotnet/roslyn). Agora o compilador de C# é escrito em C#, e você pode usar o compilador como parte de seus esforços de programação.

## <a name="c-version-70"></a>C# versão 7.0

A versão principal mais recente do C# é a versão 7.0. Esta versão tem algumas coisas interessantes e evolutivas na mesma direção que o C# 6.0, mas sem o compilador como um serviço. Aqui estão alguns dos novos recursos:

- [Variáveis Out](http://www.c-sharpcorner.com/article/out-variables-in-c-sharp-7-0/)
- [Tuplas e desconstrução](https://www.thomaslevesque.com/2016/08/23/tuple-deconstruction-in-c-7/)
- [Correspondência de padrões](./csharp-7.md#pattern-matching)
- [Funções locais](http://www.infoworld.com/article/3182416/application-development/c-7-in-depth-exploring-local-functions.html)
- [Membros aptos para expressão expandidos](./csharp-7.md#more-expression-bodied-members)
- [Locais e retornos de ref](./csharp-7.md#ref-locals-and-returns)

Outros recursos incluíam:

- [Descarta](../discards.md)
- [Literais binários](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.0/binary-literals.md)
- [Separadores de dígito](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.0/digit-separators.md)
- Locais e retornos de ref
- [Expressões throw](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.0/throw-expression.md)

Todas essas funcionalidades oferecem novos recursos interessantes para desenvolvedores e a oportunidade de escrever um código mais limpo do que nunca. Um ponto alto é a condensação da declaração de variáveis a serem usadas com a palavra-chave `out` e a permissão de vários valores retornados por meio de tupla.

Mas o C# está sendo colocado para um uso cada vez mais amplo. Agora o .NET Core tem qualquer sistema operacional como destino e tem a visão firme na nuvem e na portabilidade.  Essas novas funcionalidades certamente ocupam a mente e o tempo dos designers da linguagem, além de levarem a novos recursos.

_Artigo_ [_originalmente publicado no blog NDepend_](https://blog.ndepend.com/c-versions-look-language-history/)_, cortesia de Erik Dietrich e Patrick Smacchia._
