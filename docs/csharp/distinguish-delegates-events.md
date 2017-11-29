---
title: "Distinção entre Delegados e Eventos"
description: "Saber a diferença entre delegados e eventos e quando usar cada um desses recursos do .NET Core."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0fdc8629-2fdb-4a7c-a433-5b9d04eaf911
ms.openlocfilehash: 3026a0d853cb17dcf05d3b98d814044d743e48dc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="distinguishing-delegates-and-events"></a>Distinção entre Delegados e Eventos

[Anterior](modern-events.md)

Desenvolvedores que são novos na plataforma .NET Core geralmente têm dificuldades para decidir entre um design baseado em `delegates` e um design baseado em `events`. Este é um conceito difícil, porque os recursos das duas linguagens são muito semelhantes. De fato, os eventos são criados usando o suporte de linguagem para delegados. 

Ambas oferecem um cenário de associação tardia: elas permitem cenários em que um componente se comunica chamando um método que é conhecido somente em tempo de execução. Ambas dão suporte a métodos de assinante único e vários assinantes. Você pode ver esse suporte ser chamado de singlecast e multicast. Ambas dão suporte a uma sintaxe semelhante para adicionar e remover manipuladores. Por fim, acionar um evento e chamar um delegado usam exatamente a mesma sintaxe de chamada de método. As duas até mesmo dão suporte à mesma sintaxe de método `Invoke()` para uso com o operador `?.`.

Com todas essas semelhanças, é fácil de ter problemas para determinar quando usar qual.

## <a name="listening-to-events-is-optional"></a>Ouvir eventos é opcional

O aspecto mais importante para determinar qual recurso da linguagem usar é se é necessário ou não que haja um assinante anexado. Se seu código precisar chamar o código fornecido pelo assinante, você deverá usar um design baseado em delegados. Se seu código puder concluir todo o seu trabalho sem chamar nenhum assinante, você deverá usar um design baseado em eventos. 

Considere os exemplos criados durante esta seção. O código que você criou usando `List.Sort()` deve receber uma função de comparador para classificar corretamente os elementos. Consultas de LINQ devem receber delegados para determinar quais elementos retornar. Ambos usaram um design criado com delegados.

Considere o evento `Progress`. Ele relata o progresso de uma tarefa.
A tarefa continua quer haja ouvintes ou não.
O `FileSearcher` é outro exemplo. Ele ainda pesquisaria e localizaria todos os arquivos que foram buscados, mesmo que não houvesse assinantes do evento anexados.
Controles de UX ainda funcionam corretamente, mesmo quando não houver nenhum assinante ouvindo os eventos. Ambos usam os designs baseados em eventos.

## <a name="return-values-require-delegates"></a>Valores retornados exigem delegados

Outra consideração é o protótipo do método que você gostaria de ter para seu método de delegado. Como você viu, todos os delegados usados para os eventos têm um tipo retornado nulo. Você também viu que há expressões para criar manipuladores de eventos que passam informações para as origens dos eventos modificando propriedades do objeto de argumento de evento. Embora essas expressões funcionem, elas não são tão naturais quanto retornar um valor de um método.

Observe que essas duas heurísticas geralmente podem estar presentes: se o método de delegado retornar um valor, provavelmente ele terá impacto sobre o algoritmo de alguma forma.

## <a name="event-listeners-often-have-longer-lifetimes"></a>Ouvintes de evento frequentemente têm vida útil mais longa 

Essa é uma justificativa ligeiramente mais fraca. No entanto, você pode descobrir que designs baseados em eventos são mais naturais quando a origem do evento for gerar eventos durante um longo período de tempo. Você pode ver exemplos disso para controles de UX em vários sistemas. Quando você assina um evento, a origem do evento pode gerar eventos durante o tempo de vida do programa.
(Você pode cancelar a assinatura de eventos quando não precisar mais deles.)

Compare isso com vários designs baseados em delegados, em que um delegado é usado como um argumento para um método e o delegado não é usado depois que o método é retornado.

## <a name="evaluate-carefully"></a>Avalie cuidadosamente

As considerações acima não são regras rígidas e óbvias. Em vez disso, elas são diretrizes que podem ajudá-lo a decidir qual opção é melhor para seu uso específico. Como elas são semelhantes, você pode até mesmo fazer protótipos das suas e considerar com qual seria mais natural trabalhar. Ambas lidam bem com cenários de associação tardia. Use a que comunica melhor o seu design.
