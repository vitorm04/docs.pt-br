---
title: "O histórico do c# - guia c#"
description: "Qual o idioma a aparência nas primeiras versões e como ele evoluiu desde?"
keywords: "C#, .NET, .NET Core, o que há de novo, histórico de c#"
author: erikdietrich
ms.author: wiwagn
ms.date: 09/20/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 207c97c5dd7e04f815da61bff7f44393aea86222
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="the-history-of-c"></a>O histórico do c# #

Qual o idioma aparência em sua primeira encarnação? E como ele evoluiu nos anos desde?

## <a name="c-version-10"></a>C# versão 1.0

Quando você voltar e aparência, a versão c# do 1.0 parecia muito Java. Como [faz parte de suas metas de design indicado para ECMA](http://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html), ele procurado ser um "finalidade simples, moderna geral orientada a objeto idioma."  No momento, parece Java significa que ela obtida essas metas de design inicial.

Mas, se você examinar novamente no c# 1.0 agora, você encontraria por conta própria um pouco dizzy. Ela não tinha os recursos internos async e algumas das funcionalidades ótima em torno de genéricos que faremos para concedidas. Na verdade, ela não tinha genéricos completamente.  E [LINQ](../linq/index.md)? Não disponível ainda. Isso exigiria a alguns anos para sair.

C# versão 1.0 pesquisados extraído de recursos, em comparação comparados hoje. Você encontraria por conta própria, gravando algum código detalhado. Mas, ainda assim, você deve iniciar em algum lugar. C# versão 1.0 foi uma alternativa viável ao Java na plataforma Windows.

## <a name="c-version-20"></a>C# versão 2.0

Agora, as coisas começam a ficar interessantes. Vamos dar uma olhada em alguns recursos principais do c# 2.0, lançada em 2005, junto com o Visual Studio 2005:

- [Genéricos](../programming-guide/generics/index.md)
- [Tipos parciais](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [Métodos anônimos](../programming-guide/statements-expressions-operators/anonymous-methods.md)
- [Tipos que permitem valor nulo](../programming-guide/nullable-types/index.md)
- [Iteradores](../programming-guide/concepts/iterators.md)
- [Covariância e contravariância](../programming-guide/concepts/covariance-contravariance/index.md)

Embora c# pode ter sido iniciado como um idioma Oriented (OO) muito genérico, c# versão 2.0 alteradas que rapidamente. Depois que eles tinham seus pés sob eles, eles deu após alguns pontos problemáticos de desenvolvedor grave. E eles deu após-los de maneira intensa.

Com genéricos, você pode ter tipos e métodos que podem operar em um tipo arbitrário enquanto ainda retém a segurança de tipo. Portanto, por exemplo, ter um <xref:System.Collections.Generic.List%601> permite que você tenha `List<string>` ou `List<int>` e executar operações de segurança de tipo nessas cadeias de caracteres ou inteiros enquanto você percorrê-los. Isso é melhor do que criar `ListInt` herdeiros ou conversão de `Object` para cada operação.

Iteradores c# versão 2.0 colocado. Para colocar sucintamente, isso permite que você percorrer os itens em uma `List` (ou outros tipos enumeráveis) com um `foreach` loop. Ter isso como parte da linguagem de primeira classe drasticamente aprimorado legibilidade da linguagem e capacidade de pessoas motivo sobre o código.

E ainda, c# continua a executar um pouco de ajuste com Java. Java já tinha liberado versões que incluía genéricos e iteradores. Mas, que em breve será alterado conforme os idiomas continuados a evoluir separadas.

## <a name="c-version-30"></a>C# versão 3.0

C# versão 3.0 fornecida no final de 2007, junto com o Visual Studio 2008, embora, na verdade, seriam barco completo de recursos de linguagem com c# versão 3.5. Esta versão é marcado como uma alteração principal no crescimento do c#. Estabeleceu c# como linguagem de programação realmente formidável. Vamos dar uma olhada em alguns recursos importantes nesta versão:

- [Propriedades de auto implementado](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [Tipos anônimos](../programming-guide/classes-and-structs/anonymous-types.md)
- [Expressões de consulta](../linq/query-expression-basics.md)
- [Expressão lambda](https://www.daedtech.com/introduction-to-c-lambda-expressions/)
- [Árvores de expressão](https://blogs.msdn.microsoft.com/charlie/2008/01/31/expression-tree-basics/)
- [Métodos de extensão](https://www.codeproject.com/Tips/709310/Extension-Method-In-Csharp)

Em retrospecto, muitos desses recursos parecerem inevitável e inseparável. Todos eles se encaixam estrategicamente. Geralmente, ele é considerado recurso killer do versão c# foi a expressão de consulta, também conhecido como LINQ (consulta).

Uma exibição mais sutis examina tipos anônimos, expressões lambda e tress expressão como a base na qual o LINQ é construído. Mas, em qualquer caso, o c# 3.0 apresentados um conceito revolucionário. C# 3.0 começou a definir as bases para transformar c# em um híbrido orientada a objeto / funcional idioma.

Especificamente, agora você pode escrever estilo SQL, consultas declarativas para executar operações em coleções, entre outras coisas. Em vez de escrever um `for` loop para calcular a média de uma lista de números inteiros, você pode agora fazer isso simplesmente como `list.Average()`. A combinação de expressões de consulta e os métodos de extensão tornou pareça como se a lista de inteiros tivessem muito mais inteligente.

Levou tempo para serem realmente segure e integrar o conceito, mas eles fizeram gradualmente. E agora, anos mais tarde, código mais conciso, simples e funcional.

## <a name="c-version-40"></a>C# versão 4.0

C# versão 4.0 teria dificuldades, mantendo ao inovador status da versão 3.0. Com a versão 3.0, c# migrou o idioma firmemente fora da sombra do Java e em importância. O idioma foi se tornando elegante.

A próxima versão introduzir alguns novos recursos interessantes:

- [Vinculação dinâmica](../language-reference/keywords/dynamic.md)
- [Argumentos opcionais/denominado](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Genérico covariante e contravariant](../../standard/generics/covariance-and-contravariance.md)
- [Tipos de interoperabilidade inseridos](https://stackoverflow.com/questions/20514240/whats-the-difference-setting-embed-interop-types-true-and-false-in-visual-studi)

Tipos de interoperabilidade inseridos atenuada um problema de implantação. Contravariância e covariância genérica oferecem mais energia para usar genéricos, mas eles são um pouco acadêmicas e provavelmente mais apreciados por autores de estrutura e biblioteca. Parâmetros nomeados e opcionais permitem eliminar várias sobrecargas de método e proporcionar conveniência. Mas nenhum desses recursos é exatamente paradigma de alteração.

O recurso principal foi a introdução do `dynamic` palavra-chave. O `dynamic` palavra-chave introduzidas em c# versão 4.0 a habilidade de substituir o compilador no tempo de compilação é digitado. Usando a palavra-chave dinâmica, você pode criar construções semelhantes a dinamicamente digitadas linguagens como JavaScript. Você pode criar um `dynamic x = "a string"` e, em seguida, adicione seis, deixá-lo até o tempo de execução para classificar o que acontece em seguida.

Isso lhe dá a possibilidade de erros, mas também muita energia no idioma.

## <a name="c-version-50"></a>C# versão 5.0

C# versão 5.0 era uma versão concentrada do idioma. Quase todo o esforço para essa versão entrou em outro conceito inovador idioma.  Aqui está a lista de recursos principais:

- [Membros assíncronos](../async.md)
- [Atributos de informações do chamador](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

O atributo de informações do chamador permite facilmente recuperar informações sobre o contexto no qual você estiver executando sem recorrer a uma código de reflexão clichê inúmeras. Ele tem muitos usos de diagnóstico e tarefas de registro em log.

Mas `async` e `await` são as estrelas reais dessa versão. Quando esses recursos foi lançado em 2012, c# alterado o jogo novamente Implantando assincronia para o idioma como um participante de primeira classe. Se você já tiver lidar com operações de longa duração e a implementação de webs de retornos de chamada, você provavelmente amaram esse recurso de idioma.

## <a name="c-version-60"></a>C# versão 6.0

Com as versões 3.0 e 5.0, c# tivesse adicionado alguns recursos impressionantes em uma linguagem orientada a objeto. Com a versão 6.0, ele seria vá longe fazendo um recurso killer dominante e versão em vez disso, muitos recursos que deliciar usuários do idioma. Aqui estão algumas delas:

- [Importações estáticas](../language-reference/keywords/using-static.md)
- [Filtros de exceção](https://www.thomaslevesque.com/2015/06/21/exception-filters-in-c-6/)
- [Inicializadores de propriedade](http://geekswithblogs.net/WinAZ/archive/2015/06/30/whatrsquos-new-in-c-6.0-auto-property-initializers.aspx)
- [Membros de expressão bodied](https://lostechies.com/jimmybogard/2015/12/17/c-6-feature-review-expression-bodied-function-members/)
- [Propagador nulo](https://davefancher.com/2014/08/14/c-6-0-null-propagation-operator/)
- [Interpolação de cadeia de caracteres](../language-reference/keywords/interpolated-strings.md)
- [nome do operador](https://stackoverflow.com/questions/31695900/what-is-the-purpose-of-nameof)
- [Inicializador de dicionário](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md)

Cada um desses recursos é interessante em seus próprios méritos. Mas, se você observá-los completamente, você verá um padrão interessante. Nesta versão, c# eliminado clichê de idioma para tornar o código mais conciso e legível. Portanto, para ventiladores de código simples, esta versão de idioma era um enorme ganho.

Faziam outra coisa junto com esta versão, embora ele não é um recurso de idioma tradicional em si. Elas lançadas [Roslyn compilador como um serviço](https://github.com/dotnet/roslyn). O compilador c# agora é escrito em c#, e você pode usar o compilador como parte dos esforços de programação.

## <a name="c-version-70"></a>C# versão 7.0

A versão principal mais recente é c# versão 7.0. Esta versão tem algumas coisas interessantes e evolutiva do modo do c# 6.0, mas sem o compilador como um serviço. Aqui estão alguns dos novos recursos:

- [Limite de variáveis](http://www.c-sharpcorner.com/article/out-variables-in-c-sharp-7-0/)
- [Tuplas e deconstruction](https://www.thomaslevesque.com/2016/08/23/tuple-deconstruction-in-c-7/)
- [Correspondência de padrões](./csharp-7.md#pattern-matching)
- [Funções locais](http://www.infoworld.com/article/3182416/application-development/c-7-in-depth-exploring-local-functions.html)
- [Membros de expressão expandido bodied](./csharp-7.md#more-expression-bodied-members)
- [Retornos e locais de ref](./csharp-7.md#ref-locals-and-returns)

Todos esses recursos oferecem moderados novos recursos para desenvolvedores e a oportunidade de escrever código de limpo mesmo que nunca. Um realce é condensação a declaração de variáveis a serem usadas com o `out` palavra-chave e permitindo que vários valores de retorno por meio de tupla.

Mas c# sendo colocados para uso de cada vez mais amplo. .NET core agora tem como alvo a qualquer sistema operacional e tem seus olhos firmemente na nuvem e portabilidade.  Isso certamente ocupa ideias e a hora, além de criar novos recursos dos designers de idioma.

_Artigo_ [ _originalmente publicado no blog do NDepend_](https://blog.ndepend.com/c-versions-look-language-history/)_, pela Erik Dietrich e Patrick Smacchia._
