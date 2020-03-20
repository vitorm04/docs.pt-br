---
title: Utilizando contratos no fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: 9f967d75a8e9d24fcfac8b7376a3d4840fba52f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184270"
---
# <a name="using-contracts-in-workflow"></a>Utilizando contratos no fluxo de trabalho
Ao implementar um serviço, você define uma série de contratos que descrevem o serviço e os dados que ele envia e recebe. Os dados são representados como contratos de dados e contratos de mensagens; tanto os serviços wcf quanto de fluxo de trabalho usam definições de contrato de dados e contrato de mensagem como parte das descrições do serviço. O próprio serviço expõe metadados (sob a forma de WSDL) a fim de descrever as operações do serviço. No WCF, os contratos de prestação de serviços e contratos de operação definem o serviço e as operações que suporta. No entanto, em um serviço de fluxo de trabalho, esses contratos fazem parte do próprio processo de negócios; eles são expostos em metadados por um processo chamado inferência contratual.  
  
## <a name="contract-inference"></a>Inferência de Contrato  
 Quando um serviço de fluxo <xref:System.ServiceModel.Activities.WorkflowServiceHost>de trabalho é hospedado usando, a definição do fluxo de trabalho é examinada e um contrato é gerado com base no conjunto de atividades de mensagens encontradas no fluxo de trabalho. Em particular, as seguintes atividades e propriedades são utilizadas para gerar o contrato:  
  
 <xref:System.ServiceModel.Activities.Receive> Atividade  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>

 <xref:System.ServiceModel.Activities.SendReply> Atividade  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> Atividade  
  
 O resultado final da inferência contratual é uma descrição do serviço utilizando as mesmas estruturas de dados que os contratos de serviço e operação do WCF. Essas informações são então usadas para expor o WSDL para o serviço de fluxo de trabalho.  
  
## <a name="see-also"></a>Confira também

- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Atividades de mensagem](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
- [Como criar um serviço de fluxo de trabalho com atividades de mensagens](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [Como criar um serviço de fluxo de trabalho que consome um contrato de serviço existente](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
