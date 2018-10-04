---
title: Visão geral de serviços de fluxo de trabalho de hospedagem
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: dbe271e30e9c4e98a52c01ffaa21de25c127c7ff
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48778949"
---
# <a name="hosting-workflow-services-overview"></a>Visão geral de serviços de fluxo de trabalho de hospedagem
Serviços de fluxo de trabalho devem ser hospedados para executar. O <xref:System.ServiceModel.WorkflowServiceHost> é o host de fluxo de trabalho de out-of-the-box que dá suporte a várias instâncias, configuração e mensagens do WCF (embora os fluxos de trabalho não é necessários usar o sistema de mensagens para ser hospedado).  Ele também se integra com persistência, acompanhamento e controle de instância por meio de um conjunto de comportamentos de serviço.  Assim como do WCF <xref:System.ServiceModel.ServiceHost>, o <xref:System.ServiceModel.WorkflowServiceHost> pode ser auto-hospedado em qualquer aplicativo gerenciado do .NET ou hospedado na web (como um arquivo. xamlx) no IIS / WAS.  Os tópicos desta seção descrevem como hospedar um serviço de fluxo de trabalho.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Serviços de fluxo de trabalho de hospedagem](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 Descreve os serviços de hospedagem de fluxo de trabalho.  
  
 [Detalhes internos do host de serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 Descreve como <xref:System.ServiceModel.WorkflowServiceHost> processa as mensagens recebidas.  
  
 [Extensibilidade de host de serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 Descreve como estender a funcionalidade do host do serviço de fluxo de trabalho.  
  
 [Ponto de extremidade de controle de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 Descreve como definir um ponto de extremidade que lhe permite criar instâncias de fluxo de trabalho.
  
 [Como hospedar um serviço de fluxo de trabalho com o Windows Server App Fabric](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 Demonstra como hospedar um serviço de fluxo de trabalho existente no Windows Server App Fabric.  
  
 [Configurando WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 Descreve como controlar a persistência, acompanhamento, o comportamento ocioso e sem tratamento de exceção.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
