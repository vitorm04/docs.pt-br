---
title: Construa serviços resistentes prontos para a nuvem. adote as falhas transitórias na nuvem
description: Modernizar os aplicativos .NET existentes com contêineres Azure Cloud e Windows | Construa serviços resistentes prontos para a nuvem. adote as falhas transitórias na nuvem
ms.date: 04/30/2018
ms.openlocfilehash: e516dc675ceb8def25c6d676bced0ea7f253b2d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74711266"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>Compilar serviços resilientes prontos para a nuvem: adotar falhas transitórias na nuvem 

A resiliência é a capacidade de se recuperar de falhas e continuar funcionando. Resiliência não se trata de evitar falhas, mas de aceitar o fato de que falhas ocorrerão e, em seguida, responder a elas de uma maneira que evite o tempo de inatividade ou a perda de dados. A meta de resiliência é retornar o aplicativo para um estado totalmente funcional após uma falha.

Seu aplicativo está pronto para a nuvem quando, no mínimo, implementa um modelo baseado em software de resiliência, em vez de um modelo baseado em hardware. Sua aplicação na nuvem deve abraçar as falhas parciais que certamente ocorrerão. Projete ou reteste parcialmente sua aplicação para obter resiliência com falhas parciais esperadas. Ele deve ser projetado para lidar com falhas parciais, como paralisações transitórias de rede e nódulos, ou VMs quebrando na nuvem. Mesmo os contêineres que estão sendo movidos para um nó diferente dentro de um cluster orquestrador podem causar falhas curtas intermitentes dentro do aplicativo.

## <a name="handling-partial-failure"></a>Tratando falha parcial

Em um aplicativo baseado em nuvem, há um risco sempre presente de falha parcial. Por exemplo, uma única instância de site ou um contêiner pode falhar, ou pode estar indisponível ou sem resposta por um curto período de tempo. Ou, um único VM ou servidor pode falhar.

Como clientes e serviços são processos separados, um serviço pode não ser capaz de responder em tempo hábil à solicitação de um cliente. O serviço pode estar sobrecarregado e responder lentamente às solicitações, ou pode não estar acessível por um curto período de tempo devido a problemas de rede.

Por exemplo, considere um aplicativo monolítico .NET que acessa um banco de dados no Banco de Dados SQL do Azure. Se o banco de dados SQL do Azure ou qualquer outro serviço de terceiros não for responsivo por um breve período de tempo (um banco de dados SQL do Azure pode ser movido para um nó ou servidor diferente e ficar sem resposta por alguns segundos), quando o usuário tentar fazer qualquer ação, o aplicativo pode falhar e mostrar uma exceção no mesmo momento.

Um cenário semelhante pode ocorrer em um aplicativo que consome serviços HTTP. A rede ou o serviço em si pode não estar disponível na nuvem durante uma falha curta e transitória.

Uma aplicação resiliente como a mostrada na Figura 4-9 deve implementar técnicas como "repetições com recuo exponencial" para dar ao aplicativo a oportunidade de lidar com falhas transitórias nos recursos. Você também deve usar "disjuntores" em suas aplicações. Um disjuntor impede um aplicativo de tentar acessar um recurso quando é realmente uma falha a longo prazo. Ao usar um disjuntor, o aplicativo evita provocar uma negação de serviço a si mesmo.

![Diagrama de falhas parciais tratadas por repetições com recuo exponencial.](./media/retry-partial-failures.png)

**Figura 4-9.** Falhas parciais tratadas por tentativas com recuo exponencial

Você pode usar essas técnicas tanto em recursos HTTP quanto em recursos de banco de dados. Na Figura 4-9, o aplicativo é baseado em uma arquitetura de 3 níveis, então você precisa dessas técnicas no nível de serviços (HTTP) e no nível de nível de dados (TCP). Em um aplicativo monolítico que usa apenas um único nível de aplicativo, além do banco de dados (sem serviços adicionais ou microserviços), lidar com falhas transitórias no nível de conexão do banco de dados pode ser suficiente. Nesse cenário, é necessária apenas uma configuração específica da conexão do banco de dados.

Ao implementar comunicações resilientes que acessam o banco de dados, dependendo da versão do .NET que você está usando, pode ser simples (por exemplo, [com o Framework 6 ou posterior](/ef/ef6/fundamentals/connection-resiliency/retry-logic). É só uma questão de configurar a conexão do banco de dados). Ou, você pode precisar usar bibliotecas adicionais como o [Transient Fault Handling Application Block](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)) (para versões anteriores do .NET), ou até mesmo implementar sua própria biblioteca.

Ao implementar repetições HTTP e disjuntores, a recomendação para o .NET é usar a biblioteca [Polly,](https://github.com/App-vNext/Polly) que tem como alvo o .NET Framework 4.0, o .NET Framework 4.5 e o .NET Standard 1.1, que inclui o suporte ao .NET Core.

Para saber como implementar estratégias para lidar com falhas parciais na nuvem, consulte as seguintes referências.

### <a name="additional-resources"></a>Recursos adicionais

- **Implementação de comunicação resiliente para lidar com falha parcial**

    [https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/partial-failure-strategies](../../microservices/implement-resilient-applications/partial-failure-strategies.md)

- **Resiliência de conexão entityframework e lógica de repetição (versão 6 e posterior)**

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- **Bloco de aplicativos de tratamento de falhas transitórias**

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- **Biblioteca Polly para comunicação HTTP resiliente**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
>[Próximo](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[anterior](modernize-your-apps-with-monitoring-and-telemetry.md)
