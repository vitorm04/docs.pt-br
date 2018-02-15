---
title: "Crie serviços resilientes prontos para a nuvem. Adotar as falhas transitórias na nuvem"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Crie serviços resilientes prontos para a nuvem. Adotar as falhas transitórias na nuvem"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: aaf1ef968600a56d91267c6c12efa90d99446dd7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>Criar serviços resilientes prontos para a nuvem: adotar falhas transitórias na nuvem 

A resiliência é a capacidade de recuperar de falhas e continuar a funcionar. Resiliência não é sobre como evitar falhas, mas aceitando o fato de que as falhas ocorrerão e, em seguida, responder a eles de maneira que evita o tempo de inatividade ou perda de dados. A meta de resiliência é retornar o aplicativo para um estado totalmente funcional após uma falha.

O aplicativo está pronto para a nuvem quando, no mínimo, ele implementa um modelo baseado em software de resiliência, em vez de um modelo baseado em hardware. Seu aplicativo de nuvem deve compreender as falhas parciais que certamente ocorrerá. Você precisa criar ou parcialmente refatorar seu aplicativo, se você quiser obter resiliência a falhas parciais esperadas. Deve ser projetado para lidar com falhas parciais, como interrupções de rede transitório e nós ou VMs falhas na nuvem. Contêineres mesmo sendo movidos para outro nó em um cluster do orchestrator podem causar falhas intermitentes de curtas dentro do aplicativo.

## <a name="handling-partial-failure"></a>Tratamento de falha parcial

Em um aplicativo baseado em nuvem, há um risco de falha parcial de sempre presente. Por exemplo, uma instância de site único ou um contêiner pode falhar, ou ele pode estar indisponível ou não responder por um curto período. Ou, um único servidor ou VM pode falhar.

Como os clientes e serviços são processos separados, um serviço não poderá responder de maneira oportuna a solicitação do cliente. O serviço pode estar sobrecarregado e muito lentamente responder às solicitações, ou ele pode simplesmente não estar acessível por um curto período devido a problemas de rede.

Por exemplo, considere um aplicativo .NET monolítico que acessa um banco de dados no banco de dados do SQL Azure. Se o banco de dados do SQL Azure ou qualquer outro serviço de terceiros não está respondendo para um breve tempo (um banco de dados do SQL Azure pode ser movido para um nó diferente ou servidor e ficar sem resposta por alguns segundos), quando o usuário tenta realizar qualquer ação, o aplicativo pode falhar e mostrar w uma exceção no mesmo momento.

Um cenário semelhante pode ocorrer em um aplicativo que consome serviços HTTP. A rede ou o próprio serviço pode não estar disponível na nuvem durante uma falha transitória, curta.

Um aplicativo resiliente, como mostrado na Figura 4-9 deve implementar técnicas, como "repetições com retirada exponencial" para que o aplicativo tenha a oportunidade para lidar com falhas transitórias de recursos. Você também deve usar "disjuntores" em seus aplicativos. Um disjuntor interrompe um aplicativo tentar acessar um recurso quando ela é realmente uma falha de longo prazo. Ao usar um disjuntor, o aplicativo evita provocar uma negação de serviço para si mesmo.

![Falhas parciais tratadas pelas novas tentativas com retirada exponencial](./media/image9.png)

> **Figura 4-9.** Falhas parciais tratadas pelas novas tentativas com retirada exponencial

Você pode usar essas técnicas em recursos HTTP e nos recursos de banco de dados. Na Figura 4-9, o aplicativo é baseado em uma arquitetura de camada 3, portanto, você precisa estas técnicas no nível de serviços (HTTP) e no nível da camada de dados (TCP). Em um aplicativo monolítico que usa somente uma camada de aplicativo único além do banco de dados (não há serviços adicionais ou microservices), tratar falhas temporárias no nível de conexão do banco de dados pode ser suficiente. Nesse cenário, normalmente apenas uma configuração específica de conexão de banco de dados é necessária.

Ao implementar comunicações resilientes que acessam o banco de dados, dependendo da versão do .NET que você está usando, pode ser muito simples (por exemplo, [com o Entity Framework 6 ou posterior](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx), é apenas uma questão de configurar o conexão de banco de dados). Ou, talvez seja necessário usar as bibliotecas adicionais como o [Transient Fault Handling Application Block](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx) (para versões anteriores do .NET), ou até mesmo implementar sua própria biblioteca.

Ao implementar tentativas HTTP e disjuntores, a recomendação para .NET é usar o [Polly](https://github.com/App-vNext/Polly) biblioteca, que tem como alvo o .NET 4.0, .NET 4.5 e .NET padrão 1.1, que inclui suporte ao .NET Core.

Para saber como implementar estratégias para lidar com falhas parciais na nuvem, consulte as seguintes referências.

### <a name="additional-resources"></a>Recursos adicionais

-   **Implementar a comunicação flexível para lidar com falhas parciais**

    [https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies](https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies)

-   **Entity Framework conexão resiliência lógica e repetição (versão 6 e posterior)**

    [https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx)

-   **O Transient Fault Handling Application Block**

<!-- -->

-   [https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx)

-   **Biblioteca de Polly para comunicação de HTTP resiliente**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
[Anterior](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Próximo](modernize-your-apps-with-monitoring-and-telemetry.md)
