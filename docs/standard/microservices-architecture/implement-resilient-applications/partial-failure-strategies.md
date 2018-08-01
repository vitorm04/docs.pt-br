---
title: Estratégias para tratar falhas parciais
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Estratégias para tratar falhas parciais
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: ac82f6d506213614c7a4079e0f55f798f26a6550
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874397"
---
# <a name="strategies-for-handling-partial-failure"></a>Estratégias para tratar falhas parciais

As estratégias para lidar com falhas parciais incluem o seguinte.

**Usar a comunicação assíncrona (por exemplo, comunicação baseada em mensagens) entre microsserviços internos**. É altamente recomendável não criar longas cadeias de chamadas HTTP síncronas entre os microsserviços internos, porque esse design incorreto eventualmente se tornará a principal causa de interrupções incorretas. Pelo contrário, exceto pelas comunicações de front-end entre os aplicativos cliente e o primeiro nível de microsserviços ou Gateways de API refinados, é recomendável usar apenas comunicação assíncrona (com base em mensagem) uma vez após o ciclo de resposta/solicitação inicial, entre os microsserviços internos. Consistência eventual e arquiteturas orientadas a eventos ajudarão a minimizar os efeitos de ondulação. Essas abordagens impõem um nível mais alto de autonomia do microsserviço e, portanto, previnem contra o problema observado aqui.

**Usar novas tentativas com retirada exponencial**. Essa técnica ajuda a evitar falhas curtas e intermitentes executando novas tentativas de chamada um determinado número de vezes, caso o serviço não tivesse estado disponível apenas por um curto período de tempo. Isso pode ocorrer devido a problemas de rede intermitentes ou quando um microsserviço/contêiner é movido para um nó diferente em um cluster. No entanto, se essas novas tentativas não foram criadas corretamente com disjuntores, os efeitos de ondulação poderão ser agravados e, em último caso, poderá até haver uma [DoS (Negação de Serviço)](https://en.wikipedia.org/wiki/Denial-of-service_attack).

**Solução alternativa para tempos limite de rede**. Em geral, os clientes devem ser criados para não serem bloqueados indefinidamente e para sempre usar tempos limite ao aguardar uma resposta. Usar tempos limite garante que os recursos nunca fiquem bloqueados indefinidamente.

**Usar o padrão de disjuntor**. Nessa abordagem, o processo do cliente rastreia o número de solicitações com falha. Se a taxa de erro exceder um limite configurado, um "disjuntor" viajará para que outras tentativas falhem imediatamente. (Se um alto número de solicitações estão apresentando falha, isso sugere que o serviço não está disponível e que enviar solicitações é inútil.) Após um período de tempo limite, o cliente deverá tentar novamente e, se as novas solicitações forem bem-sucedidas, feche o disjuntor.

**Fornecer fallbacks**. Nessa abordagem, o processo de cliente executa a lógica de fallback quando uma solicitação falha, como retornar dados armazenados em cache ou um valor padrão. Essa é uma abordagem adequada para consultas e é mais complexa para atualizações ou comandos.

**Limitar o número de solicitações na fila**. Os clientes também devem impor um limite superior no número de solicitações pendentes que um microsserviço cliente pode enviar para um serviço específico. Se o limite tiver sido atingido, provavelmente será ineficaz fazer solicitações adicionais, e essas tentativas devem falhar imediatamente. Em termos de implementação, a política [Isolamento do bulkhead](https://github.com/App-vNext/Polly/wiki/Bulkhead) da Polly pode ser usada para atender a esse requisito. Essa abordagem é essencialmente uma restrição de paralelização com <xref:System.Threading.SemaphoreSlim> como a implementação. Ela também permite uma "fila" fora do bulkhead. É possível lançar proativamente uma carga excessiva mesmo antes da execução (por exemplo, devido à capacidade ser considerada cheia). Isso torna sua resposta a determinados cenários de falha mais rápida do que um disjuntor seria, uma vez que o disjuntor aguarda as falhas. O objeto BulkheadPolicy na Polly expõe o quão cheios o bulkhead e a fila estão e oferece eventos em estouro para que também possam ser usados para promover a colocação em escala horizontal automatizada.

## <a name="additional-resources"></a>Recursos adicionais

-   **Padrões de resiliência**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **Adicionando resiliência e otimizando o desempenho**
    [*https://msdn.microsoft.com/library/jj591574.aspx*](https://msdn.microsoft.com/library/jj591574.aspx)

-   **Bulkhead.** Repositório do GitHub. Implementação com a política Polly.\
    [*https://github.com/App-vNext/Polly/wiki/Bulkhead*](https://github.com/App-vNext/Polly/wiki/Bulkhead)

-   **Projetando aplicativos resilientes para o Azure**
    [*https://docs.microsoft.com/azure/architecture/resiliency/*](https://docs.microsoft.com/azure/architecture/resiliency/)

-   **Tratamento de falhas transitórias**
    <https://docs.microsoft.com/azure/architecture/best-practices/transient-faults>


>[!div class="step-by-step"]
[Anterior](handle-partial-failure.md)
[Próximo](implement-retries-exponential-backoff.md)
