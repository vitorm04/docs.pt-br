---
title: Compile serviços resilientes prontos para a nuvem. Adotar falhas transitórias na nuvem
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Compile serviços resilientes prontos para a nuvem. Adotar falhas transitórias na nuvem
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 801d017457d1cdc3c8a495c8127b203380cb1d9e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971826"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>Compile serviços resilientes prontos para a nuvem: Adotar falhas transitórias na nuvem

A resiliência é a capacidade de recuperar de falhas e continuar a funcionar. A resiliência não é sobre como evitar falhas, mas aceitar o fato de que as falhas ocorrerão e, em seguida, responder a elas de uma maneira que evite o tempo de inatividade ou perda de dados. A meta de resiliência é retornar o aplicativo para um estado totalmente funcional após uma falha.

Seu aplicativo está pronto para a nuvem quando, no mínimo, ele implementa um modelo baseado em software de resiliência, em vez de um modelo baseado em hardware. Seu aplicativo de nuvem deve compreender as falhas parciais que certamente ocorrerá. Design ou parcialmente refatorar seu aplicativo para obter resiliência com falhas parciais esperadas. Ele deve ser projetado para lidar com falhas parciais, como interrupções de rede transitórios e nós ou VMs falhando na nuvem. Até mesmo contêineres que estão sendo movidos para outro nó em um cluster do orquestrador podem causar falhas curtas intermitentes no aplicativo.

## <a name="handling-partial-failure"></a>Tratando falha parcial

Em um aplicativo baseado em nuvem, há um risco de sempre presente de falha parcial. Por exemplo, uma instância de site único ou um contêiner pode falhar, ou ele pode estar indisponível ou não responder por um curto período. Ou, um único servidor ou VM pode falhar.

Como os clientes e serviços são processos separados, um serviço pode não ser capaz de responder de maneira oportuna a uma solicitação do cliente. O serviço pode estar sobrecarregado e responder lentamente às solicitações, ou ele pode não estar acessível por um curto período devido a problemas de rede.

Por exemplo, considere um aplicativo .NET monolítico que acessa um banco de dados SQL do Azure. Se o banco de dados SQL do Azure ou qualquer outro serviço de terceiros não está respondendo para um breve momento (um banco de dados SQL do Azure pode ser movido para um nó diferente ou servidor e ficar sem resposta por alguns segundos), quando o usuário tenta realizar nenhuma ação, o aplicativo pode falhar e mostrar w uma exceção no mesmo momento.

Um cenário semelhante pode ocorrer em um aplicativo que consome serviços HTTP. A rede ou o próprio serviço pode não estar disponível na nuvem durante uma falha transitória, curta.

Um aplicativo resiliente semelhante à mostrada na Figura 4 a 9 deve implementar técnicas como "novas tentativas com retirada exponencial" para dar ao aplicativo uma oportunidade de lidar com falhas transitórias nos recursos. Você também deve usar "disjuntores" em seus aplicativos. Um disjuntor interrompe um aplicativo tentar acessar um recurso quando ele é, na verdade, uma falha de longo prazo. Ao usar um disjuntor, o aplicativo evita provocar uma negação de serviço a mesmo.

![Falhas parciais manipuladas por novas tentativas com retirada exponencial](./media/image9.png)

> **Figura 4 a 9.** Falhas parciais manipuladas por novas tentativas com retirada exponencial

Você pode usar essas técnicas nos recursos HTTP e nos recursos de banco de dados. Na Figura 4 a 9, o aplicativo se baseia em uma arquitetura de camada 3, portanto, você precisa dessas técnicas no nível de serviços (HTTP) e no nível da camada de dados (TCP). Em um aplicativo monolítico que usa apenas uma camada de aplicativo único, além do banco de dados (sem serviços adicionais nem microsserviços), tratamento de falhas transitórias no nível de conexão do banco de dados pode ser suficiente. Nesse cenário, é necessária apenas uma configuração específica de conexão de banco de dados.

Quando a implementação da comunicação resiliente que acessam o banco de dados, dependendo da versão do .NET que você está usando, pode ser simples (por exemplo, [com o Entity Framework 6 ou posterior](/ef/ef6/fundamentals/connection-resiliency/retry-logic). Ele é apenas uma questão de configurar a conexão de banco de dados). Ou, talvez seja necessário usar bibliotecas adicionais, como o [Transient Fault Handling Application Block](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)) (para versões anteriores do .NET), ou até mesmo implementar sua própria biblioteca.

Ao implementar novas tentativas HTTP e os disjuntores, a recomendação para .NET é usar o [Polly](https://github.com/App-vNext/Polly) biblioteca, que tem como alvo o .NET Framework 4.0, .NET Framework 4.5 e .NET Standard 1.1, que inclui suporte ao .NET Core.

Para saber como implementar estratégias para tratar falhas parciais na nuvem, consulte as referências a seguir.

### <a name="additional-resources"></a>Recursos adicionais

-   **Implementando comunicação resiliente para lidar com falhas parciais**

    [https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies](../../microservices-architecture/implement-resilient-applications/partial-failure-strategies.md)

-   **Entity Framework conexão resiliência e lógica de repetição (versão 6 e posterior)**

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

-   **O Transient Fault Handling Application Block**

-   <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

-   **Biblioteca Polly para comunicação resiliente de HTTP**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
>[Anterior](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[Próximo](modernize-your-apps-with-monitoring-and-telemetry.md)
