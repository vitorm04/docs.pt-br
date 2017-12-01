---
title: "Estratégias para lidar com falhas parciais"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Estratégias para lidar com falhas parciais"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: ff3bed530b13a9b1822c7cccf5a4d47df6fc6239
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="strategies-for-handling-partial-failure"></a>Estratégias para lidar com falhas parciais

Estratégias para lidar com falhas parciais incluem o seguinte.

**Usar a comunicação assíncrona (por exemplo, comunicação baseada em mensagens) em microservices interno**. É altamente recomendável não criar longas cadeias de chamadas síncronas de HTTP entre o microservices interno porque esse design incorreto eventualmente se tornará a principal causa de interrupções incorretas. Ao contrário, exceto para as front-end comunicações entre os aplicativos cliente e o primeiro nível de microservices ou refinada Gateways de API, é recomendável usar apenas (com base em mensagem) comunicação assíncrona uma vez após a solicitação inicial / ciclo de resposta, entre o microservices interno. Consistência eventual e arquiteturas orientadas por eventos ajudarão para minimizar os efeitos em cascata. Essas abordagens impõem um nível mais alto de microsserviço autonomia e, portanto, evitar o problema mencionado aqui.

**Use as repetições com retirada exponencial**. Essa técnica ajuda a evitar curto e tentativas de falhas intermitentes realizando a chamada de um determinado número de vezes, caso o serviço não estava disponível apenas por um curto período. Isso pode ocorrer devido a problemas de rede intermitente ou quando um contêiner de microsserviço/é movido para outro nó em um cluster. No entanto, se essas tentativas não foram projetadas corretamente com disjuntores, ele pode aggravate o efeito de ondulação, causando, por fim, até mesmo um [dos (negação de serviço)](https://en.wikipedia.org/wiki/Denial-of-service_attack).

**Solução alternativa tempos limite de rede**. Em geral, os clientes devem ser criados para não ser bloqueado indefinidamente e para sempre usar tempos limite ao aguardar uma resposta. Usando tempos limites garante que recursos nunca são associados indefinidamente.

**Use o padrão de disjuntor**. Nessa abordagem, o processo de cliente rastreia o número de solicitações com falha. Se a taxa de erros exceder um limite configurado, um viagens "disjuntor" para que outras tentativas falham imediatamente. (Se um grande número de solicitações estiverem falhando, que sugere o serviço está indisponível e enviar solicitações é inútil.) Após um período de tempo limite, o cliente deve tentar novamente e se as novas solicitações forem bem-sucedidas, feche o disjuntor.

**Fornecer fallbacks**. Nessa abordagem, o processo de cliente executa a lógica de fallback quando uma solicitação falhar, como retornar dados armazenados em cache ou um valor padrão. Isso é uma abordagem adequada para consultas e é mais complexo para as atualizações ou comandos.

**Limitar o número de solicitações em fila**. Os clientes também devem impor um limite superior no número de solicitações pendentes que microsserviço um cliente pode enviar para um serviço específico. Se o limite for atingido, ele provavelmente será ineficaz fazer solicitações adicionais e as tentativas devem falhar imediatamente. Em termos de implementação, a Polly [Bulkhead isolamento](https://github.com/App-vNext/Polly/wiki/Bulkhead) política pode ser usada para atenderem a esse requisito. Essa abordagem é essencialmente um acelerador de paralelização com [SemaphoreSlim](https://docs.microsoft.com/dotnet/api/system.threading.semaphoreslim?view=netcore-1.1) como a implementação. Ele também permite que uma "fila" fora de bulkhead. Você proativamente pode lançar uma carga excessiva, mesmo antes da execução (por exemplo, porque a capacidade é considerada completa). Isso torna sua resposta a determinados cenários de falha mais rápido do que um disjuntor seria, desde que o disjuntor aguarda até que as falhas. O objeto BulkheadPolicy Polly expõe quanto o bulkhead fila, e são ofertas eventos no estouro assim também podem ser usados para a unidade de escala horizontal automatizada.

## <a name="additional-resources"></a>Recursos adicionais

-   **Padrões de resiliência**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **Adição de resiliência e otimizar o desempenho**
    [*https://msdn.microsoft.com/en-us/library/jj591574.aspx*](https://msdn.microsoft.com/en-us/library/jj591574.aspx)

-   **Bulkhead.** Repositório do GitHub. Implementação de política Polly. \
    [*https://GitHub.com/App-vNext/Polly/wiki/Bulkhead*](https://github.com/App-vNext/Polly/wiki/Bulkhead)

-   **Desenvolvendo aplicativos resilientes do Azure**
    [*https://docs.microsoft.com/azure/architecture/resiliency/*](https://docs.microsoft.com/azure/architecture/resiliency/)

-   **Tratamento de falhas transitórias**
    <https://docs.microsoft.com/azure/architecture/best-practices/transient-faults>


>[!div class="step-by-step"]
[Anterior] (identificador-parcial-failure.md) [Avançar] (implementar-tentativas-exponencial-backoff.md)
