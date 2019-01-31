---
title: Visão geral dos serviços de fluxo de trabalho - WCF
ms.date: 03/30/2017
ms.assetid: e536dda3-e286-441e-99a7-49ddc004b646
ms.openlocfilehash: 1461ef545c4b31f84e62d82453320179d9aa74e0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278662"
---
# <a name="workflow-services-overview"></a>Visão geral dos serviços de fluxo de trabalho

Serviços de fluxo de trabalho são serviços baseados no WCF que são implementados usando fluxos de trabalho. Os serviços de fluxo de trabalho são fluxos de trabalho que usam as atividades de mensagens para enviar e receber mensagens do Windows Communication Foundation (WCF). .NET framework 4.5 apresenta uma série de atividades de mensagem que permitem que você enviar e receber mensagens de dentro de um fluxo de trabalho. Para obter mais informações sobre as atividades e como eles podem ser usados para implementar padrões de troca de mensagem diferente de mensagens, consulte [atividades de mensagens](messaging-activities.md).

## <a name="benefits-of-using-workflow-services"></a>Benefícios do uso de serviços de fluxo de trabalho

À medida que os aplicativos se tornam cada vez mais distribuídos, serviços individuais são responsáveis por chamar outros serviços para descarregar uma parte do trabalho. Implementar essas chamadas como operações assíncronas apresenta alguma complexidade no código. Tratamento de erro adiciona complexidade adicional na forma de tratamento de exceções e fornecendo informações de rastreamento detalhadas. Alguns serviços geralmente são de longa execução e podem demorar até recursos valiosos do sistema enquanto aguarda a entrada. Devido a esses problemas, aplicativos distribuídos costumam ser muito complexo e difícil de escrever e manter. Fluxos de trabalho são uma maneira natural de expressar a coordenação do trabalho assíncrono, especialmente as chamadas para serviços externos. Fluxos de trabalho também são eficazes para representar a processos de negócios de longa execução. Ele é essas qualidades que tornam o fluxo de trabalho de um excelente ativo para a criação de serviços em um ambiente distribuído.

## <a name="implementing-a-workflow-service"></a>Implementação de um serviço de fluxo de trabalho

Ao implementar um serviço WCF, você pode definir um número de contratos que descrevem o serviço e os dados que ele envia e recebe. Os dados são representados como contratos de dados e contratos de mensagem. Serviços WCF e o fluxo de trabalho usam definições de contrato de mensagem e de contrato de dados como parte de descrições do serviço. O próprio serviço expõe metadados (na forma de WSDL) para descrever as operações do serviço. No WCF, contratos de serviço e operação definir o serviço e as operações que ele suporta. No entanto, em um serviço de fluxo de trabalho, esses contratos são parte do processo de negócios em si. Eles são expostos nos metadados por um processo chamado inferência do contrato. Quando um serviço de fluxo de trabalho é hospedado usando <xref:System.ServiceModel.Activities.WorkflowServiceHost>, a definição de fluxo de trabalho é examinada e um contrato é gerado com base no conjunto de atividades encontradas no fluxo de trabalho de mensagens. Em particular, as atividades e as propriedades a seguir são usadas para gerar o contrato:

<xref:System.ServiceModel.Activities.Receive> Atividade

- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>

- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>

- <xref:System.ServiceModel.Activities.Receive.Action%2A>

<xref:System.ServiceModel.Activities.SendReply> Atividade

- <xref:System.ServiceModel.Activities.SendReply.Action%2A>

<xref:System.ServiceModel.Activities.TransactedReceiveScope> Atividade

O resultado final da inferência do contrato é uma descrição do serviço usando as mesmas estruturas de dados como serviços WCF e contratos de operação. Essas informações, em seguida, são usadas para expor o WSDL para o serviço de fluxo de trabalho.

> [!NOTE]
> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] não permite escrever serviços de fluxo de trabalho usando uma definição de contrato existente sem algum suporte de ferramentas adicionais. Contratos de serviço de fluxo de trabalho são criados pelo processo de inferência de tipos de contrato abordado anteriormente. Contratos de mensagem e contratos de dados são totalmente compatíveis, no entanto.

## <a name="workflow-services-and-msmq-based-bindings"></a>Serviços de fluxo de trabalho e associações do MSMQ

O WCF define duas ligações com base em MSMQ <xref:System.ServiceModel.NetMsmqBinding> e <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  Associações do MSMQ geralmente são usadas com os serviços de fluxo de trabalho devido à natureza de longa execução de tais serviços. As associações com base em MSMQ têm um `ValidityDuration` propriedade que especifica quanto tempo mensagens MSMQ podem supor que seja válida. Devido à natureza de serviços de fluxo de trabalho de longa execução, é possível que a duração da validade de uma mensagem MSMQ pode decorrer antes que o serviço de fluxo de trabalho possa processá-los. Portanto, é muito importante definir a duração da validade de uma associação de MSMQ com um valor apropriado. Esse valor deve ser escolhido com base no fluxo de trabalho e como ele processa as mensagens. Por exemplo, se você tiver um fluxo de trabalho com um <xref:System.ServiceModel.Activities.Receive> atividade seguida por uma atividade personalizada que leva 10 minutos para ser executado, seguido de outra <xref:System.ServiceModel.Activities.Receive> atividade, o valor correto para `ValidityDuration` seja maior que 10 minutos.

## <a name="hosting-a-workflow-service"></a>Hospedar um serviço de fluxo de trabalho

Assim como serviços WCF, serviços de fluxo de trabalho devem ser hospedados. Serviços WCF usam a <xref:System.ServiceModel.ServiceHost> serviços de classe para o fluxo de trabalho e hospedar serviços usam <xref:System.ServiceModel.Activities.WorkflowServiceHost> para hospedar os serviços. Assim como serviços WCF, serviços de fluxo de trabalho podem ser hospedados em uma variedade de maneiras, por exemplo:

- Em um gerenciado [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplicativo.

- No Internet Information Services (IIS).

- No serviço de ativação de processos do Windows (WAS).

- Em um serviço Windows gerenciado.

Serviços de fluxo de trabalho hospedados em um gerenciado [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplicativo ou um serviço Windows gerenciado criar uma instância do <xref:System.ServiceModel.Activities.WorkflowServiceHost> de classe e passá-lo uma instância da <xref:System.ServiceModel.Activities.WorkflowService> que contém a definição de fluxo de trabalho dentro a <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> propriedade. Uma definição de fluxo de trabalho que contém as atividades de mensagem é exposta como um serviço de fluxo de trabalho.

Para hospedar um serviço de fluxo de trabalho no IIS ou WAS, coloque o arquivo. xamlx que contém a definição de serviço de fluxo de trabalho em um diretório virtual. Um ponto de extremidade padrão (usando <xref:System.ServiceModel.BasicHttpBinding>) é criado automaticamente para obter mais informações, consulte [simplificado configuração](../../../../docs/framework/wcf/simplified-configuration.md). Você também pode colocar um arquivo Web. config no diretório virtual para especificar seus próprios pontos de extremidade. Se sua definição de fluxo de trabalho está em um assembly, você pode colocar um arquivo. svc no diretório virtual e o assembly de fluxo de trabalho no diretório App_Code. O arquivo. svc deve especificar a fábrica do host de serviço e a classe que implementa o serviço de fluxo de trabalho. O exemplo a seguir mostra como especificar a fábrica do host de serviço e especificar a classe que implementa o serviço de fluxo de trabalho.

```
<%@ServiceHost Factory=" System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory
Service="EchoService"%>
```