---
title: Delegados versus eventos
description: Saber a diferença entre delegados e eventos e quando usar cada um desses recursos do .NET Core.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0fdc8629-2fdb-4a7c-a433-5b9d04eaf911
ms.openlocfilehash: 51d982c9b5b16a5fc28ede5f0318bc100bb33b68
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805760"
---
# <a name="distinguishing-delegates-and-events"></a>Distinção entre Delegados e Eventos

[Anterior](modern-events.md)

Desenvolvedores que são novos na plataforma .NET Core geralmente têm dificuldades para decidir entre um design baseado em `delegates` e um design baseado em `events`. A escolha de delegados ou eventos é muitas vezes difícil, porque as duas características linguísticas são semelhantes. De fato, os eventos são criados usando o suporte de linguagem para delegados.

Ambas oferecem um cenário de associação tardia: elas permitem cenários em que um componente se comunica chamando um método que é conhecido somente em runtime. Ambas dão suporte a métodos de assinante único e vários assinantes. Você pode ver esse suporte ser chamado de singlecast e multicast. Ambas dão suporte a uma sintaxe semelhante para adicionar e remover manipuladores. Por fim, acionar um evento e chamar um delegado usam exatamente a mesma sintaxe de chamada de método. As duas até mesmo dão suporte à mesma sintaxe de método `Invoke()` para uso com o operador `?.`.

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

## <a name="events-have-private-invocation"></a>Eventos têm invocação privada

Classes diferentes daquela em que um evento é contido só podem adicionar e remover ouvintes de eventos; apenas a classe que contém o evento pode invocar o evento. Eventos são tipicamente membros de classe pública.
Em comparação, os delegados são frequentemente passados como parâmetros e armazenados como membros de classe privada, se eles são armazenados em tudo.

## <a name="event-listeners-often-have-longer-lifetimes"></a>Ouvintes de evento frequentemente têm vida útil mais longa

Esse evento que os ouvintes têm vidas mais longas é uma justificativa um pouco mais fraca. No entanto, você pode descobrir que designs baseados em eventos são mais naturais quando a origem do evento for gerar eventos durante um longo período de tempo. Você pode ver exemplos de design baseado em eventos para controles UX em muitos sistemas. Quando você assina um evento, a origem do evento pode gerar eventos durante o tempo de vida do programa.
(Você pode cancelar a assinatura de eventos quando não precisar mais deles.)

Compare isso com vários designs baseados em delegados, em que um delegado é usado como um argumento para um método e o delegado não é usado depois que o método é retornado.

## <a name="evaluate-carefully"></a>Avalie cuidadosamente

As considerações acima não são regras rígidas e óbvias. Em vez disso, elas são diretrizes que podem ajudá-lo a decidir qual opção é melhor para seu uso específico. Como elas são semelhantes, você pode até mesmo fazer protótipos das suas e considerar com qual seria mais natural trabalhar. Ambas lidam bem com cenários de associação tardia. Use a que comunica melhor o seu design.
