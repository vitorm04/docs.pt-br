---
title: Utilizando contratos no fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: 1772c61147bb8a96f3f78b4226a1d341df3eb9d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="using-contracts-in-workflow"></a>Utilizando contratos no fluxo de trabalho
Ao implementar um serviço, você pode definir um número de contratos que descrevem o serviço e os dados que ele envia e recebe. Os dados são representados como contratos de dados e de mensagem; serviços WCF e o fluxo de trabalho usam definições de contrato de mensagem e contrato de dados como parte de descrições de serviços. O próprio serviço expõe metadados (na forma de WSDL) para descrever as operações do serviço. No WCF, contratos de serviço e operação definir o serviço e as operações que ele suporta. No entanto, em um serviço de fluxo de trabalho, esses contratos são parte do processo de negócios em si; eles serão expostos nos metadados por um processo chamado inferência de contrato.  
  
## <a name="contract-inference"></a>Inferência de contrato  
 Quando um serviço de fluxo de trabalho é hospedado usando <xref:System.ServiceModel.Activities.WorkflowServiceHost>, a definição de fluxo de trabalho é examinada e um contrato é gerado com base no conjunto de atividades encontradas no fluxo de trabalho do sistema de mensagens. Em particular as seguintes atividades e propriedades são usadas para gerar o contrato:  
  
 <xref:System.ServiceModel.Activities.Receive> Atividade  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>   
 
 <xref:System.ServiceModel.Activities.SendReply> Atividade  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> Atividade  
  
 O resultado final de inferência de contrato é uma descrição do serviço usando as mesmas estruturas de dados como contratos de serviço e operação do WCF. Em seguida, essas informações são usadas para expor o WSDL para o serviço de fluxo de trabalho.  
  
## <a name="see-also"></a>Consulte também  
 [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Atividades de mensagens](../../../../docs/framework/wcf/feature-details/messaging-activities.md)  
 [Como criar um serviço de fluxo de trabalho com atividades de mensagens](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 [Como criar um serviço de fluxo de trabalho que consome um contrato de serviço existente](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
