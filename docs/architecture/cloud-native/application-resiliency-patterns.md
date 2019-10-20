---
title: Padrões de resiliência de aplicativo
description: Arquitetando aplicativos .NET nativos da nuvem para o Azure | Padrões de resiliência do aplicativo
ms.date: 06/30/2019
ms.openlocfilehash: 67ae20f14a67f3a96d6c74cad727afe680ff3178
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72315947"
---
# <a name="application-resiliency-patterns"></a>Padrões de resiliência de aplicativo

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

A primeira linha de defesa é a resiliência de aplicativo habilitada para software. 

Embora você possa investir um tempo considerável escrevendo sua própria estrutura de resiliência, esses produtos já existem. Por exemplo, [Polly](http://www.thepollyproject.org/) é uma biblioteca abrangente de resiliência do .net e de tratamento de falhas transitórias que permite aos desenvolvedores expressar políticas de resiliência de uma maneira fluente e thread-safe. O Polly tem como alvo aplicativos criados com o .NET Framework completo ou o .NET Core. A Figura 6-2 mostra as políticas de resiliência (ou seja, a funcionalidade) disponíveis na biblioteca Polly. Essas políticas podem ser aplicadas individualmente ou combinadas em conjunto.

![Estrutura Polly](./media/polly-resiliency-framework.png)

**Figura 6-2**. Recursos da estrutura de resiliência do Polly

Observe como, na figura anterior, as políticas de resiliência se aplicam a mensagens de solicitação, sejam provenientes de um cliente externo ou outro serviço de back-end. O objetivo é compensar a solicitação de um serviço que pode estar momentaneamente indisponível. Essas interrupções curtas normalmente se manifestam com os códigos de status HTTP mostrados na Figura 6-3.

![Códigos de status HTTP para tentar novamente](./media/http-status-codes.png)

**Figura 6-3**. Códigos de status HTTP para tentar novamente

Pergunta: você tentaria novamente um código de status HTTP de 403-Proibido? Nº Aqui, o sistema está funcionando corretamente, mas informando ao chamador que eles não estão autorizados a executar a operação solicitada. Deve-se ter cuidado para repetir apenas as operações causadas por falhas.

Como recomendado no capítulo 1, os desenvolvedores da Microsoft que constroem aplicativos nativos de nuvem devem ter como destino o .NET Core. A versão 2,1 introduziu a biblioteca [HTTPClientFactory](https://www.stevejgordon.co.uk/introduction-to-httpclientfactory-aspnetcore) para criar instâncias de cliente http para interagir com recursos baseados em URL. Substituindo a classe HTTPClient original, a classe Factory dá suporte a muitos recursos avançados, um dos quais é uma [integração total](../microservices/implement-resilient-applications/implement-http-call-retries-exponential-backoff-polly.md) com a biblioteca de resiliência Polly. Com ele, você pode definir facilmente políticas de resiliência na classe de inicialização do aplicativo para lidar com falhas parciais e problemas de conectividade.

Em seguida, vamos expandir em padrões de repetição e de disjuntor.

### <a name="retry-pattern"></a>Padrão de repetição

Em um ambiente de nuvem nativa distribuída, as chamadas para serviços e recursos de nuvem podem falhar devido a falhas transitórias (de curta duração), que normalmente se corrigem após um breve período de tempo. A implementação de uma estratégia de repetição ajuda um serviço nativo de nuvem a lidar com esses cenários.

O [padrão de repetição](https://docs.microsoft.com/azure/architecture/patterns/retry) permite que um serviço Repita uma operação de solicitação com falha a um número (configurável) de vezes com um tempo de espera crescente exponencialmente. A Figura 6-4 mostra uma nova tentativa em ação.

![Padrão de repetição em ação](./media/retry-pattern.png)

**Figura 6-4**. Padrão de repetição em ação

Na figura anterior, um padrão de repetição foi implementado para uma operação de solicitação. Ele está configurado para permitir até quatro repetições antes de falhar com um intervalo de retirada (tempo de espera) a partir de dois segundos, o que exponencialmente dobra para cada tentativa subsequente.

- A primeira invocação falha e retorna um código de status HTTP de 500. O aplicativo aguarda dois segundos e tenta novamente a chamada.
- A segunda invocação também falha e retorna um código de status HTTP de 500. O aplicativo agora dobra o intervalo de retirada para quatro segundos e tenta novamente a chamada.
- Por fim, a terceira chamada é realizada com sucesso.
- Nesse cenário, a operação de repetição teria tentado até quatro repetições enquanto dobra a duração da retirada antes de falhar a chamada.

É importante aumentar o período de retirada antes de tentar novamente a chamada para permitir que o tempo do serviço seja autocorrigido. É uma prática recomendada implementar uma retirada exponencialmente crescente (duplicando o período em cada repetição) para permitir o tempo de correção adequado.

## <a name="circuit-breaker-pattern"></a>Padrão de disjuntor

Embora o padrão de repetição possa ajudar a recuperar uma solicitação confusas em uma falha parcial, há situações em que as falhas podem ser causadas por eventos inesperados que exigirão períodos de tempo mais longos para resolver. Essas falhas podem variar em termos de gravidade de uma perda parcial de conectividade até a falha completa de um serviço. Nessas situações, é inútil que um aplicativo repita continuamente uma operação que provavelmente não terá sucesso.

Para piorar as coisas, a execução de operações contínuas de repetição em um serviço não responsivo pode movê-lo para um cenário de negação de serviço autoimposto, no qual você inunda o serviço com chamadas contínuas esgotando recursos como memória, threads e banco de dados conexões, causando falha em partes não relacionadas do sistema que usam os mesmos recursos.

Nessas situações, seria preferível para a operação falhar imediatamente e tentar invocar o serviço apenas se for provável que tenha êxito.

O [padrão de disjuntor](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker) pode impedir que um aplicativo tente executar repetidamente uma operação que provavelmente falhará. Ele também monitora o aplicativo com uma chamada de avaliação periódica para determinar se a falha foi resolvida. A Figura 6-5 mostra o padrão de disjuntor em ação.

![Padrão de disjuntor em ação](./media/circuit-breaker-pattern.png)

**Figura 6-5**. Padrão de disjuntor em ação

Na figura anterior, um padrão de disjuntor foi adicionado ao padrão de nova tentativa original. Observe como após 10 solicitações com falha, os separadores de circuito são abertos e não permite mais chamadas para o serviço. O valor CheckCircuit, definido como 30 segundos, especifica a frequência com que a biblioteca permite que uma solicitação prossiga para o serviço. Se essa chamada for realizada com sucesso, o circuito será fechado e o serviço estará novamente disponível para o tráfego.

Tenha em mente que a intenção do padrão de disjuntor é *diferente* daquela do padrão de repetição. O padrão de repetição permite que um aplicativo Repita uma operação na expectativa de que ele terá sucesso. O padrão de disjuntor impede que um aplicativo faça uma operação que provavelmente falhará. Geralmente, um aplicativo *combinará* esses dois padrões usando o padrão de repetição para invocar uma operação por meio de um disjuntor. No entanto, a lógica de repetição deve ser sensível a quaisquer exceções retornadas pelo disjuntor e abandonar tentativas de repetição se o disjuntor indicar que uma falha não é transitória.

A resiliência do aplicativo é necessária para lidar com operações solicitadas problemáticas. Mas, é apenas metade da história. Em seguida, abordamos os recursos de resiliência disponíveis na nuvem do Azure.

>[!div class="step-by-step"]
>[Anterior](resiliency.md)
>[Próximo](infrastructure-resiliency-azure.md)
