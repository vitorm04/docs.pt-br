---
title: Tour do .NET
description: Um tour guiado por alguns dos recursos-chave da plataforma .NET.
keywords: ".NET, .NET Core, Tour, Linguagens de Programação, Não Seguro, Gerenciamento de Memória, Segurança de Tipos, Async"
author: cartermp
manager: wpickett
ms.author: phcart
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
translationtype: Human Translation
ms.sourcegitcommit: 2c57b5cebd63b1d94b127cd269e3b319fb24dd97
ms.openlocfilehash: 02e2fa22e36fd2f6618527ad3c89cbbd8587dfe2

---

# <a name="tour-of-net"></a>Tour do .NET

O .NET é uma plataforma de desenvolvimento de uso geral.  Ele tem vários recursos importantes, como várias linguagens de programação, modelos de programação assíncronos e simultâneos e interoperabilidade nativa, o que permite que uma ampla variedade de cenários em várias plataformas.

Este artigo oferece um tour guiado por alguns dos recursos-chave da plataforma .NET.

Consulte [Componentes de arquitetura do .NET](components.md) para saber mais sobre cada uma das "partes" de arquitetura do .NET e por que elas são usadas.

## <a name="how-to-run-the-code-samples"></a>Como executar os exemplos de código

Para saber como configurar um ambiente de desenvolvimento para executar os exemplos de código, consulte [Introdução](getting-started.md).  É possível copiar e colar os exemplos de código desta página no seu ambiente para executá-los. 

> [!NOTE]
No futuro, este site de documentação terá a capacidade de executar esses exemplos de código no seu navegador.

## <a name="programming-languages"></a>Linguagens de programação

O .NET dá suporte a várias linguagens de programação.  Os tempos de execução do .NET implementam o [Common Language Infrastructure (CLI)](https://www.visualstudio.com/en-us/mt639507), que (entre outras coisas) especifica um tempo de execução independente de linguagem e interoperabilidade de linguagem.  Isso significa que você pode escolher qualquer linguagem .NET para criar aplicativos e serviços no .NET.

A Microsoft desenvolve ativamente e oferece suporte a três linguagens .NET: C#, F# e Visual Basic .NET. 

* C# é simples, poderosa, fortemente tipada e orientada a objeto, mantendo a expressividade e elegância das linguagens de estilo C. Qualquer pessoa familiarizada com C e linguagens semelhantes encontrará poucos problemas para adaptar-se a C#.  Confira o [Guia de C#](../csharp/index.md) para saber mais sobre o C#.

* F# é uma linguagem de programação de plataforma cruzada com prioridade para a parte funcional e que também dá suporte à programação imperativa e orientada a objeto tradicional.  Confira o [Guia de F#](../fsharp/index.md) para saber mais sobre o F#.

* Visual Basic é uma linguagem fácil de aprender que você pode usar para criar uma variedade de aplicativos executados no .NET.

## <a name="automatic-memory-management"></a>Gerenciamento automático de memória

O .NET usa [coleta de lixo](garbagecollection/index.md) para fornecer gerenciamento automático de memória para os programas.  O GC opera em uma abordagem lenta para gerenciamento de memória, dando prioridade à produtividade do aplicativo sobre a coleta imediata de memória.  Para saber mais sobre o GC do .NET, confira [Noções básicas da coleta de lixo (GC)](garbagecollection/fundamentals.md).

As duas linhas a seguir alocam memória:

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L1-L2)]

Não há nenhuma palavra-chave análoga para desalocar memória, pois a desalocação ocorre automaticamente quando o coletor de lixo recupera a memória por meio de sua execução agendada.

Tipos em um determinado escopo normalmente saem do escopo depois que um método é concluído, momento no qual eles podem ser coletados. No entanto, é possível indicar ao GC que um determinado objeto está fora do escopo antes da saída do método usando a instrução `using`:

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

Uma vez que o bloco `using` for concluído, o GC saberá que o objeto `stream` no exemplo acima está livre para ser coletado e ter sua memória recuperada.

Essas regras têm uma semântica ligeiramente diferente no F#.  Para saber mais sobre o gerenciamento de recursos no F#, confira [Gerenciamento de Recursos: A`use` Palavra-Chave](../fsharp/language-reference/resource-management-the-use-keyword.md)

Um dos recursos menos óbvios, mas muito abrangente que é habilitado por um coletor de lixo é a segurança da memória. O que não varia quanto à segurança da memória é muito simples: a memória de um programa está segura se ele acessa somente a memória que foi alocada (e não liberada). Ponteiros pendentes são sempre bugs e rastreá-los é muitas vezes difícil.

O tempo de execução do .NET fornece serviços adicionais para cumprir a promessa de segurança da memória, normalmente não oferecida por um GC. Isso garante que programas não façam indexação após o final de uma matriz nem acessem um campo fantasma após o fim de um objeto.

O exemplo a seguir gerará uma exceção como resultado de segurança da memória.

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

## <a name="type-safety"></a>Segurança de tipos

Os objetos são alocados em termos de tipos. As únicas operações permitidas para um determinado objeto e a memória que ele consome são aquelas do seu tipo. Um `Dog` tipo pode ter os métodos `Jump` e `WagTail`, mas provavelmente não terá um método `SumTotal`. Um programa só pode chamar os métodos declarados de um determinado tipo. Todas as outras chamadas resultarão em um erro em tempo de compilação ou uma exceção de tempo de execução (no caso de usar recursos dinâmicos ou `object`).

Linguagens .NET são orientadas a objeto, com hierarquias de classes base e classes derivadas. O tempo de execução do .NET só permitirá conversões de objeto e chamadas alinhadas à hierarquia de objetos. Lembre-se de que todos os tipos definidos em qualquer linguagem .NET derivam do tipo base `object`.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L18-L23)]

A segurança de tipos também é usada para ajudar a forçar o encapsulamento, garantindo a fidelidade das palavras-chave acessadoras. Palavras-chave acessadoras são artefatos que controlam o acesso a membros de um determinado tipo por outro código. Elas geralmente são usadas para vários tipos de dados dentro de um tipo que são usados para gerenciar seu comportamento.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L3-L3)]

C#, Visual Basic e F# dão suporte à **inferência de tipo** de variável local. Inferência de tipos significa que o compilador deduzirá o tipo da expressão no lado esquerdo da expressão no lado direito. Isso não significa que a segurança de tipos é interrompida ou evitada. O tipo resultante **tem** um tipo forte com tudo o que a expressão implica. Vamos reescrever as duas primeiras linhas do exemplo anterior para apresentar a inferência de tipos. Observe que o restante do exemplo é exatamente o mesmo.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L28-L34)]

F# tem ainda mais recursos de inferência de tipos do que inferência de tipo de variável local encontradas no C# e no Visual Basic.  Para obter mais informações, confira [Inferência de Tipos](../fsharp/language-reference/type-inference.md).

## <a name="delegates-and-lambdas"></a>Delegados e lambdas

Delegados são como ponteiros de função do C++, com uma grande diferença: eles são fortemente tipados. Eles são um tipo de método desconectado dentro do sistema de tipos CLR. Métodos regulares são anexados a uma classe e só podem ser chamados diretamente por meio de convenções de chamada estáticas ou de instância.

Delegados são usados em várias APIs e locais no mundo do .NET, principalmente por meio de expressões lambda, que são a base do LINQ.

Leia mais sobre isso no documento [Delegados e lambdas](delegates-lambdas.md).

## <a name="generics"></a>Genéricos

Genéricos são um recurso adicionado no .NET Framework 2.0. Em resumo, os genéricos permitem que o programador introduza um "parâmetro de tipo" ao criar suas classes, o que permite que o código do cliente (os usuários do tipo) especifiquem o tipo exato a usar no lugar do parâmetro de tipo.

Os genéricos foram adicionados para ajudar os programadores a implementar estruturas de dados genéricos. Antes de sua chegada, para que um tipo de, digamos, `List` fosse genérico, seria necessário que ele trabalhasse com elementos do tipo `object`. Isso implicaria em diversos problemas de desempenho e semântica, além de possíveis erros de tempo de execução sutis. O mais notório deles é quando uma estrutura de dados contém, por exemplo, inteiros e cadeias de caracteres e uma `InvalidCastException` é gerada ao trabalhar com os membros da lista.

O exemplo a seguir mostra uma execução de programa básico usando uma instância de tipos @System.Collections.Generic.List%601.

[!code-csharp[GenericsShort](../../samples/csharp/snippets/tour/GenericsShort.csx)]

Para obter mais informações, veja o artigo [Visão geral de tipos genéricos (Genéricos)](generics.md).

## <a name="async-programming"></a>Programação assíncrona

Programação assíncrona é um conceito de primeira classe no .NET, com suporte assíncrono no tempo de execução, bibliotecas do framework e construções de linguagem .NET. Internamente, elas são baseadas em objetos (como `Task`) que aproveitam o sistema operacional para realizar trabalhos vinculados a E/S de modo tão eficiente quanto possível.

Para saber mais sobre programação assíncrona no .NET, comece com a [Visão geral da assincronia](async.md).

## <a name="language-integrated-query-linq"></a>LINQ (Consulta Integrada à Linguagem)

O LINQ é um poderoso conjunto de recursos para C# e VB que permite que você escreva código simples e declarativo para operar em dados. Os dados podem ser de várias formas (como objetos na memória, em um banco de dados SQL ou um documento XML), mas o código LINQ que você escreve normalmente não parecerá diferente para cada fonte de dados!

Para obter mais informações e ver alguns exemplos, confira [LINQ (consulta integrada à linguagem)](using-linq.md).

## <a name="native-interoperability"></a>Interoperabilidade nativa

Cada sistema operacional atualmente em uso fornece bastante suporte de plataforma para várias tarefas de programação. O .NET fornece várias maneiras de explorar essas APIs. Coletivamente, esse suporte é chamado "interoperabilidade nativa" e nesta seção damos uma olhada em como acessar APIs nativas do código .NET gerenciado.

A principal maneira de fazer interoperabilidade nativa é via "invocação de plataforma" ou P/Invoke, de forma abreviada. Esse suporte no .NET Core está disponível nas plataformas Linux e Windows. Outra maneira somente para Windows de fazer interoperabilidade nativa é conhecida como "interoperabilidade COM" e é usada para trabalhar com [componentes COM](https://msdn.microsoft.com/library/bwa2bx93.aspx) em código gerenciado. Ela foi desenvolvida com base na infraestrutura de P/Invoke, mas funciona de maneiras levemente diferentes.

A maioria do suporte de interoperabilidade do Mono (e, portanto, do Xamarin) para Java e Objective-C é criado da mesma forma, ou seja, eles usam os mesmos princípios.

Leia mais sobre isso no documento [Interoperabilidade nativa](native-interop.md).

## <a name="unsafe-code"></a>Código não seguro

O CLR habilita a capacidade de acessar a memória nativa e fazer aritmética de ponteiro via código `unsafe`. Essas operações são necessárias para certos algoritmos e interoperabilidade do sistema. Embora poderoso, uso de código não seguro não é recomendado a menos que seja necessário para fornecer interoperabilidade com APIs do sistema ou implementar o algoritmo mais eficiente. Código não seguro pode não executar da mesma maneira em ambientes diferentes e também perde os benefícios de um coletor de lixo e da segurança de tipo. Recomenda-se restringir e centralizar ao máximo o código não seguro, alé de testar esse código detalhadamente.

O exemplo a seguir é uma versão modificada do `ToString()` método da classe `StringBuilder`.  Ele ilustra como o uso do código `unsafe` pode implementar um algoritmo com eficiência movendo blocos de memória diretamente:

[!code-csharp[Unsafe](../../samples/csharp/snippets/tour/Unsafe.csx)]

## <a name="next-steps"></a>Próximas etapas

Se você estiver interessado em um tour pelos recursos do C#, confira [Tour do C#](../csharp/tour-of-csharp/index.md).

Se você estiver interessado em um tour pelos recursos do F#, confira [Tour do F#](../fsharp/tour.md).

Se você deseja começar a gravar códigos, confira [Introdução](getting-started.md).

Para saber mais sobre componentes importantes do .NET, confira [Componentes de Arquitetura do .NET](components.md).


<!--HONumber=Nov16_HO3-->


