---
title: "Recomendações para aplicativos web do ASP.NET Core de hospedagem do Azure"
description: "Projetar aplicativos Web modernos com ASP.NET Core e o Azure | Recomendações para os aplicativos web ASP.NET de hospedagem do Azure"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: c361a28321ec9dcbfee1db8036757632a5d81f7c
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2017
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>Recomendações para aplicativos Web do ASP.NET Core de hospedagem do Azure

> "Líderes de linha de negócios everywhere estão ignorando os departamentos de TI para obter aplicativos da nuvem (também conhecido como SaaS) e pagar por eles como seriam em uma assinatura de revista. E quando o serviço não é mais necessário, pode cancelar a assinatura com nenhum equipamento deixado no canto."  
> _\-Daryl Plummer, analista da Gartner_

## <a name="summary"></a>Resumo

Tudo o que seu aplicativo necessidades e arquitetura, do Windows Azure pode dar suporte a ele. Suas necessidades de hospedagem podem ser tão simples quanto um site estático para um aplicativo sofisticado extremamente composto de dezenas de serviços. Para aplicativos do ASP.NET Core monolítico web e serviços de suporte, há várias configurações bem conhecidas que são recomendadas. As recomendações a seguir são agrupadas de acordo com o tipo de recurso a ser hospedado completo se os dados, aplicativos ou processos individuais.

## <a name="web-applications"></a>Aplicativos Web

Aplicativos da Web podem ser hospedados com:

-   Aplicativos do serviço de aplicativo Web

-   Contêineres

-   Malha do serviço do Azure

-   Máquinas virtuais (VMs)

Desses, o serviço de aplicativo Web de aplicativos são a abordagem recomendada para a maioria dos cenários. Para arquiteturas de microsserviço, considere uma abordagem baseada no contêiner ou do service fabric. Se você precisar de mais controle sobre os computadores executando o aplicativo, considere a possibilidade de máquinas virtuais do Azure.

### <a name="app-service-web-apps"></a>Aplicativos do serviço de aplicativo Web

Os aplicativos do serviço de aplicativo Web oferece uma plataforma de totalmente gerenciada otimizada para aplicativos web de hospedagem. É um platform-as-a-service(PaaS) oferta que permite que você se concentre em sua lógica de negócios, enquanto o Azure se encarrega da infraestrutura necessária para executar e dimensionar o aplicativo. Alguns dos principais recursos do serviço de aplicativo Web de aplicativos:

-   Otimização de DevOps (integração contínua e entrega, vários ambientes, A / B testes, suporte a script)

-   Escala global e alta disponibilidade

-   Conexões com plataformas de SaaS e seus dados no local

-   Segurança e conformidade

-   integração com o Visual Studio

Serviço de aplicativo do Azure é a melhor opção para a maioria dos aplicativos web. Gerenciamento e implantação são integradas à plataforma, sites podem ser dimensionados rapidamente para lidar com cargas de tráfego intenso e o Gerenciador de tráfego e balanceamento de carga interna fornecer alta disponibilidade. Você pode mover os sites existentes para o serviço de aplicativo do Azure com facilidade usando uma ferramenta de migração on-line, usar um aplicativo de código-fonte aberto da Galeria de aplicativos da Web, ou criar um novo site usando a estrutura e as ferramentas de sua escolha. O recurso WebJobs facilita a adicionar um trabalho em segundo plano para seu aplicativo da web do serviço de aplicativo de processamento.

### <a name="containers-and-azure-container-service"></a>Contêineres e serviço de contêiner do Azure

Serviço de contêiner do Azure simplifica a criar, configurar e gerenciar um cluster de máquinas virtuais que são pré-configurados para executar aplicativos em contêineres. Ele usa uma configuração otimizada de ferramentas populares de agendamento e a coordenação de código-fonte aberto. Isso permite que você use suas habilidades existentes ou exploram um corpo grande e crescente de experiência da comunidade, para implantar e gerenciar aplicativos de contêiner no Microsoft Azure.

Serviço de contêiner do Azure simplifica a criar, configurar e gerenciar um cluster de máquinas virtuais que são pré-configurados para executar aplicativos em contêineres. Ele usa uma configuração otimizada de ferramentas populares de agendamento e a coordenação de código-fonte aberto. Isso permite que você use suas habilidades existentes ou exploram um corpo grande e crescente de experiência da comunidade, para implantar e gerenciar aplicativos de contêiner no Microsoft Azure.

Um objetivo do serviço de contêiner do Azure é fornecer um ambiente de hospedagem de contêiner usando ferramentas de código-fonte aberto e tecnologias que são comuns entre os clientes da Microsoft hoje. Para esse fim, o serviço de contêiner do Azure expõe os pontos de extremidade de API padrão para o orchestrator escolhido (controlador de domínio/OS, Docker Swarm ou Kubernetes). Ao usar esses pontos de extremidade, você pode utilizar qualquer software que é capaz de se comunicando com esses pontos de extremidade. Por exemplo, no caso do ponto de extremidade Docker Swarm, você pode optar por usar a interface de linha de comando do Docker (CLI). Para o SO/controlador de domínio, você pode escolher DCOS CLI. Para Kubernetes, você pode escolher kubectl. Figura 11-1 mostra como você usaria esses pontos de extremidade para gerenciar os clusters do contêiner.

![](./media/image11-1.png)

**Figura 11-1.** Gerenciamento do Azure do serviço de contêiner com Docker, Kubernetes ou DC/OS pontos de extremidade.

### <a name="azure-service-fabric"></a>Malha do serviço do Azure

Service Fabric é uma boa opção se você estiver criando um novo aplicativo ou reescrever em um aplicativo existente para usar uma arquitetura de microsserviço. Aplicativos, que são executados em um pool compartilhado de computadores, podem começar pequenos e crescer em grande escala com centenas ou milhares de computadores, conforme necessário. Serviços com monitoração de estado mais fácil de maneira consistente e confiável armazenar o estado do aplicativo e do Service Fabric gerencia automaticamente o particionamento de serviço, dimensionamento e disponibilidade para você. Serviço de malha também oferece suporte a WebAPI com Interface Web aberta para .NET (OWIN) e o ASP.NET Core. Em comparação com o serviço de aplicativo, Service Fabric que também esteja fornece mais controle sobre ou acesso direto à infraestrutura subjacente. Você pode remoto em servidores ou configurar tarefas de inicialização do servidor.

### <a name="azure-virtual-machines"></a>Máquinas Virtuais do Azure

Se você tiver um aplicativo existente que exige modificações significativas para ser executado no serviço de aplicativo ou serviço de malha, você pode escolher as máquinas virtuais para simplificar a migração para a nuvem. No entanto, corretamente configurar, proteger e VMs mantendo requer muito mais tempo e conhecimento de TI em comparação com o serviço de aplicativo do Azure e do Service Fabric. Se você estiver pensando em máquinas virtuais do Azure, certifique-se de que levar em conta o esforço de manutenção contínua necessário para o patch, atualizar e gerenciar seu ambiente de VM. Máquinas virtuais do Azure é a infraestrutura-como-um-serviço (IaaS), enquanto o serviço de aplicativo e serviço de malha são plataforma-como-um-serviço (Paas).

#### <a name="feature-comparison"></a>Comparação de recursos

| Serviço de aplicativo de recurso | Malha do serviço | Máquina virtual |
|---------|----------|----------|
| Implantação quase instantânea | X | X | |
| Expansão vertical para máquinas maiores sem reimplantação | X | X | |
| Instâncias compartilham conteúdo e configuração; não é necessário reimplantar ou reconfigure ao dimensionar | X | X | |
| Vários ambientes de implantação (produção, preparo) | X | X | |
| Gerenciamento automático de atualização do sistema operacional | X | | |
| Perfeita para alternar entre as plataformas de 32/64 bits | X | | |
| Código de implantação com Git, FTP | X | | X |
| Código de implantação com WebDeploy | X | | X |
| Implantar o código com o TFS | X | X | X |
| Host da web ou camada de serviço da web da arquitetura de várias camada | X | X | X |
| Acessar os serviços do Azure, como o barramento de serviço, armazenamento, banco de dados SQL | X | X | X |
| Instalar qualquer MSI personalizado | | X | X |

## <a name="logical-processes"></a>Processos lógicos

Processos individuais de lógicos que podem ser separados do restante do aplicativo podem ser implantados independentemente para funções do Azure de modo "sem servidor". As funções do Azure permite que você simplesmente escrever o código necessário para um problema específico, sem se preocupar com o aplicativo ou a infraestrutura para executá-lo. Você pode escolher entre uma variedade de linguagens de programação, incluindo C\#, F\#, Node.js, Python e PHP, permitindo que você escolha a linguagem mais produtiva para a tarefa em questão. Como a maioria das soluções com base em nuvem, você paga apenas pelo período de tempo que seu uso e você pode confiar em funções do Azure para expandir conforme necessário.

## <a name="data"></a>Dados

O Azure oferece uma ampla variedade de opções de armazenamento de dados, para que seu aplicativo pode usar o provedor de dados apropriado para os dados em questão.

Para dados transacionais e relacionais, bancos de dados do SQL Azure são a melhor opção. Para ler mais dados de alto desempenho, um cache Redis com o apoio de um banco de dados do SQL Azure é uma boa solução.

Dados JSON não estruturados podem ser armazenados em uma variedade de maneiras, colunas de banco de dados SQL para Blobs ou tabelas no armazenamento do Azure, de documentos. Desses, DocumentDB oferece o melhor consultar a funcionalidade e é a opção recomendada para um grande número de documentos com base em JSON que devem dar suporte à consulta.

Dados transitório ou evento-baseado em comandos usados para orquestrar o comportamento do aplicativo podem usar o barramento de serviço do Azure ou filas do armazenamento do Azure. Barramento de armazenamento do Azure oferece mais flexibilidade e é o serviço recomendado para mensagens não trivial dentro e entre aplicativos.

## <a name="architecture-recommendations"></a>Recomendações de arquitetura

Requisitos do seu aplicativo devem determinar sua arquitetura. Há muitos serviços do Azure diferentes disponíveis, escolhendo que certo é uma decisão importante. A Microsoft oferece uma galeria de arquiteturas de referência para ajudar a identificar típicas arquiteturas otimizadas para cenários comuns. Você pode associar uma arquitetura de referência que mapas estreitamente às necessidades do seu aplicativo ou em menos oferece um ponto de partida.

Figura 11-2 mostra uma arquitetura de referência de exemplo. Este diagrama descreve uma abordagem de arquitetura recomendada para um site de sistema de gerenciamento de conteúdo Sitecore otimizado para marketing.

![](./media/image11-2.png)

**Figura 11-2.** Sitecore marketing arquitetura de referência do site.

**Referências – recomendações de hospedagem do Azure**

-   Architectures\ de solução do Azure
    <https://Azure.microsoft.com/Solutions/Architecture/>

-   Guide\ de desenvolvedores do Azure
    <https://Azure.microsoft.com/Campaigns/Developer-Guide/>

-   O que é o serviço de aplicativo do Azure? \
    <https://docs.microsoft.com/Azure/App-Service/App-Service-Value-prop-What-is>

-   Serviço de aplicativo do Azure, máquinas virtuais, serviço de malha e Comparison\ de serviços de nuvem
    <https://docs.microsoft.com/Azure/App-Service-Web/Choose-Web-site-Cloud-Service-VM>

>[!div class="step-by-step"]
[Anterior] (desenvolvimento-processo-para-azure.md)
