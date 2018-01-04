---
title: "Visão geral de serviços de fluxo de trabalho"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e536dda3-e286-441e-99a7-49ddc004b646
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c38abe8ab0ac99a7e5bd0499ff826a00730b211
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-services-overview"></a>Visão geral de serviços de fluxo de trabalho
Serviços de fluxo de trabalho são [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-com base em serviços que são implementados usando fluxos de trabalho. Serviços de fluxo de trabalho são fluxos de trabalho que usam as atividades de mensagens para enviar e receber [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mensagens. .NET framework 4.5 apresenta uma série de atividades de mensagens que permite enviar e receber mensagens de um fluxo de trabalho. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]atividades de mensagem e como eles podem ser usados para implementar os padrões de troca de mensagens diferentes, consulte [atividades de mensagens](../../../../docs/framework/wcf/feature-details/messaging-activities.md).  
  
## <a name="benefits-of-using-workflow-services"></a>Benefícios do uso de serviços de fluxo de trabalho  
 À medida que os aplicativos cada vez mais tornou-se distribuído, serviços individuais são responsáveis por chamar outros serviços para descarregar uma parte do trabalho. Implementar essas chamadas como operações assíncronas apresenta alguma complexidade no código. Tratamento de erro adiciona complexidade adicional na forma de tratamento de exceções e fornecer informações de rastreamento detalhadas. Alguns serviços geralmente são longas e podem levar até valiosos recursos do sistema ao aguardar a entrada. Devido a esses problemas, aplicativos distribuídos são geralmente muito complexa e difícil de escrever e manter. Fluxos de trabalho são uma maneira natural para expressar a coordenação de trabalho assíncrono, especialmente as chamadas para os serviços externos. Fluxos de trabalho também são eficazes para representar a processos de negócios de longa execução. É essas qualidades que tornam o fluxo de trabalho um excelente ativo para a criação de serviços em um ambiente distribuído.  
  
## <a name="implementing-a-workflow-service"></a>Implementar um serviço de fluxo de trabalho  
 Ao implementar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço, você define um número de contratos que descrevem o serviço e os dados que ele envia e recebe. Os dados são representados como contratos de dados e de mensagem. Serviços WCF e o fluxo de trabalho usam definições de contrato de mensagem e contrato de dados como parte de descrições de serviços. O próprio serviço expõe metadados (na forma de WSDL) para descrever as operações do serviço. No WCF, contratos de serviço e operação definir o serviço e as operações que ele suporta. No entanto, em um serviço de fluxo de trabalho, esses contratos são parte do processo de negócios em si. Eles serão expostos nos metadados por um processo chamado inferência de contrato. Quando um serviço de fluxo de trabalho é hospedado usando <xref:System.ServiceModel.Activities.WorkflowServiceHost>, a definição de fluxo de trabalho é examinada e um contrato é gerado com base no conjunto de atividades encontradas no fluxo de trabalho do sistema de mensagens. Em particular, as seguintes atividades e propriedades são usadas para gerar o contrato:  
  
 <xref:System.ServiceModel.Activities.Receive>Atividade  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.OperationContractName%2A>  --> `System.ServiceModel.Activities.Receive.OperationContractName`
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.ValueType%2A>  --> `System.ServiceModel.Activities.Receive.ValueType`
  
 <xref:System.ServiceModel.Activities.SendReply>Atividade  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.SendReply.ValueType%2A> -->
`xref:System.ServiceModel.Activities.SendReply.ValueType`
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>Atividade  
  
 O resultado final de inferência de contrato é uma descrição do serviço usando as mesmas estruturas de dados como [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços e contratos de operação. Em seguida, essas informações são usadas para expor o WSDL para o serviço de fluxo de trabalho.  
  
> [!NOTE]
>  [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]não permite escrever serviços de fluxo de trabalho usando uma definição de contrato existente sem suporte a algumas ferramentas adicionais. Contratos de serviço de fluxo de trabalho são criados pelo processo de inferência de contrato discutido anteriormente. Contratos de mensagem e contratos de dados são totalmente suportados, no entanto.  
  
## <a name="workflow-services-and-msmq-based-bindings"></a>Serviços de fluxo de trabalho e associações de MSMQ  
 O WCF define duas associações baseadas em MSMQ <xref:System.ServiceModel.NetMsmqBinding> e <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  Associações de MSMQ geralmente são usadas com os serviços de fluxo de trabalho devido à natureza de tais serviços longas. As associações de MSMQ têm um `ValidityDuration` propriedade que especifica quanto tempo as mensagens MSMQ podem assumir que seja válido. Devido à natureza dos serviços de fluxo de trabalho de longa execução é possível que a duração da validade de uma mensagem MSMQ pode decorrer antes do serviço de fluxo de trabalho pode processá-los. Portanto, é muito importante definir a duração da validade de uma associação de MSMQ com um valor apropriado. Esse valor deve ser escolhido com base em fluxo de trabalho e como ele processa as mensagens. Por exemplo, se você tiver um fluxo de trabalho com um <xref:System.ServiceModel.Activities.Receive> atividade seguida por uma atividade personalizada que leva 10 minutos para ser executado, seguido por outro <xref:System.ServiceModel.Activities.Receive> atividade, o valor correto para `ValidityDuration` deve ser maior que 10 minutos.  
  
## <a name="hosting-a-workflow-service"></a>Hospedar um serviço de fluxo de trabalho  
 Como [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços de fluxo de trabalho de serviços devem ser hospedados. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]serviços usam o <xref:System.ServiceModel.ServiceHost> classe para serviços de hospedagem e fluxo de trabalho serviços usam <xref:System.ServiceModel.Activities.WorkflowServiceHost> para hospedar serviços. Como [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços de fluxo de trabalho de serviços podem ser hospedados em uma variedade de maneiras, por exemplo:  
  
-   Em um gerenciado [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplicativo.  
  
-   No Internet Information Services (IIS).  
  
-   No serviço de ativação de processos do Windows (WAS).  
  
-   Em um serviço gerenciado do Windows.  
  
 Serviços de fluxo de trabalho hospedados em um gerenciado [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplicativo ou um serviço gerenciado do Windows cria uma instância do <xref:System.ServiceModel.Activities.WorkflowServiceHost> classe e passá-lo em uma instância do <xref:System.ServiceModel.Activities.WorkflowService> que contém a definição de fluxo de trabalho dentro do <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> propriedade. Uma definição de fluxo de trabalho que contém atividades de mensagens é exposta como um serviço de fluxo de trabalho.  
  
 Para hospedar um serviço de fluxo de trabalho do IIS ou do WAS, coloque o arquivo de .xamlx que contém a definição de serviço de fluxo de trabalho em um diretório virtual. Um ponto de extremidade padrão (usando <xref:System.ServiceModel.BasicHttpBinding>) é criado automaticamente [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md). Você também pode colocar um arquivo Web. config no diretório virtual para especificar seus próprios pontos de extremidade. Se a definição de fluxo de trabalho está em um assembly, você pode colocar um arquivo. svc no diretório virtual e o assembly de fluxo de trabalho no diretório App_Code. O arquivo. svc deve especificar a fábrica do host de serviço e a classe que implementa o serviço de fluxo de trabalho. O exemplo a seguir mostra como especificar a fábrica do host de serviço e especifique a classe que implementa o serviço de fluxo de trabalho.  
  
```  
<%@ServiceHost Factory=" System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory  
Service="EchoService"%>  
```
