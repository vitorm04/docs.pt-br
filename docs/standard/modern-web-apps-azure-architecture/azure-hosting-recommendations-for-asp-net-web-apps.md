---
title: Recomendações de hospedagem do Azure para aplicativos Web ASP.NET Core
description: Projetar aplicativos Web modernos com o ASP.NET Core e o Azure | Recomendações de hospedagem do Azure para aplicativos Web ASP.NET Core
author: ardalis
ms.author: wiwagn
ms.date: 06/27/2018
ms.openlocfilehash: 221ea2a9fc154468f16ce09195a0415883ada9df
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53125926"
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>Recomendações de hospedagem do Azure para aplicativos Web ASP.NET Core

> "Os líderes de linha de negócios em toda parte estão ignorando os departamentos de TI para obter aplicativos da nuvem (também conhecidos como SaaS) e pagando por eles como pagariam a assinatura de uma revista. E quando o serviço não é mais necessário, eles podem cancelar a assinatura sem nenhum equipamento deixado inutilizado no canto."  
> _\- Daryl Plummer, analista do Gartner_

Quaisquer que sejam as necessidades e a arquitetura de seu aplicativo, o Microsoft Azure pode dar suporte a elas. Suas necessidades de hospedagem podem variar de um simples site estático até aplicativos extremamente sofisticados compostos por dezenas de serviços. Para aplicativos Web ASP.NET Core monolíticos e os serviços de suporte, há várias configurações bem conhecidas que são recomendadas. As recomendações neste artigo são agrupadas com base no tipo de recurso a ser hospedado, seja para aplicativos completos, processos individuais ou dados.

## <a name="web-applications"></a>Aplicativos Web

Os aplicativos Web podem ser hospedados com:

- Aplicativos Web do Serviço de Aplicativo

- Contêineres

- Azure Service Fabric

- VMs (Máquinas Virtuais)

Entre essas opções, os Aplicativos Web do Serviço de Aplicativo é a abordagem recomendada para a maioria dos cenários. Para arquiteturas de microsserviço, considere uma abordagem baseada em contêiner ou o Service Fabric. Caso precise ter mais controle sobre os computadores que executam o aplicativo, considere a possibilidade de usar as Máquinas Virtuais do Azure.

### <a name="app-service-web-apps"></a>Aplicativos Web do Serviço de Aplicativo

Os Aplicativos Web do Serviço de Aplicativo oferecem uma plataforma totalmente gerenciada, otimizada para a hospedagem de aplicativos Web. É uma oferta de PaaS (plataforma como serviço) que permite que você se concentre na lógica de negócios, enquanto o Azure se encarrega da infraestrutura necessária para executar e dimensionar o aplicativo. Alguns dos principais recursos dos Aplicativos Web do Serviço de Aplicativo:

- Otimização de DevOps (integração e entrega contínuas, múltiplos ambientes, testes A/B, suporte a script).

- Escala global e alta disponibilidade.

- Conexões com plataformas de SaaS e seus dados locais.

- Segurança e conformidade.

- Integração com o Visual Studio.

O Serviço de Aplicativo do Azure é a melhor opção para a maioria dos aplicativos Web. A implantação e o gerenciamento estão integrados à plataforma, os sites podem ser dimensionados rapidamente para manipular cargas de alto tráfego e o balanceamento de carga interno e o gerenciador de tráfego fornecem alta disponibilidade. Você pode mover os sites existentes para o Serviço de Aplicativo do Azure com facilidade usando uma ferramenta de migração online, usar um aplicativo de software livre por meio da Galeria de Aplicativos Web ou criar um novo site usando a estrutura e as ferramentas de sua escolha. O recurso WebJobs facilita a adição de um processamento de trabalho em segundo plano ao aplicativo Web do Serviço de Aplicativo.

### <a name="azure-kubernetes-service"></a>Serviço de Kubernetes do Azure

O AKS (Serviço de Kubernetes do Azure) gerencia seu ambiente Kubernetes hospedado, acelerando e facilitando a implantação e o gerenciamento de aplicativos em contêineres, sem exigir conhecimento em orquestração de contêiner. Ele também elimina a sobrecarga de operações e manutenção contínuas por meio de provisionamento, atualização e dimensionamento de recursos sob demanda, sem deixar seus aplicativos offline.

O AKS reduz a complexidade e a sobrecarga operacional do gerenciamento de um cluster do Kubernetes descarregando grande parte dessa responsabilidade para o Azure. Como se trata de um serviço de Kubernetes hospedado, o Azure trata das tarefas críticas, como monitoramento de integridade e manutenção, para você. Além disso, você paga apenas pelos nós do agente dentro dos clusters, não pelos mestres. Como um serviço de Kubernetes gerenciados, o AKS fornece:

- Atualizações de versão e aplicação de patch automatizadas para o Kubernetes.
- Dimensionamento fácil do cluster.
- Plano de controle hospedado de autorrecuperação (mestres).
- Economia de custos – pague somente pelos nós do pool de agentes em execução.

Com o Azure lidando com o gerenciamento dos nós no cluster do AKS, você não precisa mais executar muitas tarefas manualmente, como as atualizações de cluster. Como o Azure lida com essas tarefas de manutenção importantes, o AKS não fornece acesso direto (como com SSH) ao cluster.

### <a name="azure-service-fabric"></a>Azure Service Fabric

O Service Fabric é uma boa opção se você está criando um novo aplicativo ou reescrevendo um aplicativo existente para usar uma arquitetura de microsserviço. Os aplicativos, que são executados em um pool compartilhado de computadores, podem começar pequenos e crescer em grande escala com centenas ou milhares de computadores, conforme necessário. Os serviços com estado facilitam o armazenamento consistente e confiável do estado do aplicativo, e o Service Fabric gerencia automaticamente o particionamento de serviço, o dimensionamento e a disponibilidade para você. O Service Fabric também é compatível com a WebAPI com o Open Web Interface para .NET (OWIN) e ASP.NET Core. Em comparação com o Serviço de Aplicativo, o Service Fabric também fornece mais controle sobre a infraestrutura subjacente ou o acesso direto a ela. Você pode acessar os servidores remotamente ou configurar tarefas de inicialização do servidor.

### <a name="azure-virtual-machines"></a>Máquinas Virtuais do Azure

Caso você já tenha um aplicativo que exige modificações significativas para ser executado no Serviço de Aplicativo ou no Service Fabric, escolha as Máquinas Virtuais para simplificar a migração para a nuvem. No entanto, a configuração, a proteção e a manutenção corretas das VMs exigem muito mais tempo e conhecimento de TI em comparação ao Serviço de Aplicativo do Azure e o Service Fabric. Se estiver considerando o uso das Máquinas Virtuais do Azure, leve em conta o esforço de manutenção contínuo necessário para aplicar patch, atualizar e gerenciar seu ambiente de VM. As Máquinas Virtuais do Azure são uma IaaS (infraestrutura como serviço), enquanto o Serviço de Aplicativo e o Service Fabric são uma PaaS (plataforma como serviço).

#### <a name="feature-comparison"></a>Comparação entre recursos

| Recurso                                                                                    | Serviço de Aplicativo | Contêineres (AKS) | Service Fabric | Máquina virtual |
| ------------------------------------------------------------------------------------------ | ----------- | ---------------- | -------------- | --------------- |
| Implantação quase instantânea                                                                    | X           | X                | X              |                 |
| Escala vertical para computadores maiores sem reimplantação                                               | X           | X                | X              |                 |
| As instâncias compartilham o conteúdo e a configuração; não é necessário reimplantá-las nem reconfigurá-las durante a escala | X           | X                | X              |                 |
| Ambientes de implantação múltiplos (produção, preparo)                                     | X           | X                | X              |                 |
| Gerenciamento automático de atualizações do sistema operacional                                                             | X           | X                |                |                 |
| Comutação direta entre plataformas de 32/64 bits                                             | X           | X                |                |                 |
| Implantação de código com o GIT, FTP                                                                  | X           | X                |                | X               |
| Implantação de código com a Implantação da Web                                                                 | X           | X                |                | X               |
| Implantação de código com o TFS                                                                       | X           | X                | X              | X               |
| Hospedagem da camada da Web ou de serviço Web da arquitetura de várias camadas                                    | X           | X                | X              | X               |
| Acesso a serviços do Azure como o Barramento de Serviço, Armazenamento, Banco de Dados SQL                              | X           | X                | X              | X               |
| Instalação de qualquer MSI personalizado                                                                     |             | X                | X              | X               |

## <a name="logical-processes"></a>Processos lógicos

Processos lógicos individuais que podem ser desacoplados do restante do aplicativo podem ser implantados de forma independente no Azure Functions de modo "sem servidor". O Azure Functions permite simplesmente escrever o código necessário para um problema específico, sem a preocupação com o aplicativo ou a infraestrutura necessária para executá-lo. Escolha uma entre uma variedade de linguagens de programação, incluindo C\#, F\#, Node.js, Python e PHP, que permitem que você escolha a linguagem mais produtiva para a tarefa em mãos. Como a maioria das soluções baseadas em nuvem, você paga apenas pelo tempo que usar e pode confiar no Azure Functions para escalar verticalmente, conforme necessário.

## <a name="data"></a>Dados

O Azure oferece uma ampla variedade de opções de armazenamento de dados, de modo que seu aplicativo possa usar o provedor de dados apropriado para os dados em questão.

Para dados transacionais e relacionais, os Bancos de Dados SQL do Azure são a melhor opção. Para dados de alto desempenho em sua maior parte de leitura, um Cache Redis com o apoio de um Banco de Dados SQL do Azure é uma boa solução.

Dados JSON não estruturados podem ser armazenados de várias maneiras que variam de colunas do Banco de Dados SQL, Blobs ou Tabelas no Armazenamento do Azure ao DocumentDB. Entre essas opções, o DocumentDB oferece a melhor funcionalidade de consulta e é a opção recomendada para uma grande quantidade de documentos baseados em JSON que devem dar suporte à consulta.

Dados transitórios baseados em comando ou evento usados para orquestrar o comportamento do aplicativo podem usar o Barramento de Serviço do Azure ou as Filas do Armazenamento do Azure. O Barramento do Armazenamento do Azure oferece mais flexibilidade e é o serviço recomendado para mensagens não triviais enviadas dentro e entre aplicativos.

## <a name="architecture-recommendations"></a>Recomendações de arquitetura

Os requisitos do aplicativo devem determinar sua arquitetura. Há muitos serviços do Azure diferentes disponíveis. Escolher o certo é uma decisão importante. A Microsoft oferece uma galeria de arquiteturas de referência para ajudar a identificar as arquiteturas típicas otimizadas para cenários comuns. Você pode encontrar uma arquitetura de referência que mapeie de perto as necessidades do seu aplicativo ou que, pelo menos, ofereça um ponto de partida.

A Figura 11-2 mostra uma arquitetura de referência de exemplo. Esse diagrama descreve uma abordagem de arquitetura recomendada para um site de sistema de gerenciamento de conteúdo do Sitecore otimizado para marketing.

![](./media/image11-2.png)

**Figura 11-1.** Arquitetura de referência do site de marketing do Sitecore.

**Referências – recomendações de hospedagem do Azure**

- Arquiteturas de solução do Azure\
  <https://azure.microsoft.com/solutions/architecture/>

- Guia do Desenvolvedor do Azure\
  <https://azure.microsoft.com/campaigns/developer-guide/>

- Visão geral dos Aplicativos Web\
  <https://docs.microsoft.com/azure/app-service/app-service-web-overview>

- Comparação entre o Serviço de Aplicativo do Azure, as Máquinas Virtuais, o Service Fabric e os Serviços de Nuvem\
  <https://docs.microsoft.com/azure/app-service-web/choose-web-site-cloud-service-vm>

- Introdução ao AKS (Serviço de Kubernetes do Azure)\
  <https://docs.microsoft.com/azure/aks/intro-kubernetes>

>[!div class="step-by-step"]
>[Anterior](development-process-for-azure.md)