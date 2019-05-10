---
title: Utilizando contratos no fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: dc2d631d8a9e588645dd60495c54799b2a2dd8a0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64637756"
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="aabcb-102">Utilizando contratos no fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="aabcb-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="aabcb-103">Ao implementar um serviço, você pode definir um número de contratos que descrevem o serviço e os dados que ele envia e recebe.</span><span class="sxs-lookup"><span data-stu-id="aabcb-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="aabcb-104">Os dados são representados como contratos de dados e os contratos de mensagem; serviços WCF e o fluxo de trabalho usam definições de contrato de mensagem e de contrato de dados como parte de descrições do serviço.</span><span class="sxs-lookup"><span data-stu-id="aabcb-104">The data is represented as data contracts and message contracts; both WCF and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="aabcb-105">O próprio serviço expõe metadados (na forma de WSDL) para descrever as operações do serviço.</span><span class="sxs-lookup"><span data-stu-id="aabcb-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="aabcb-106">No WCF, contratos de serviço e operação definir o serviço e as operações que ele suporta.</span><span class="sxs-lookup"><span data-stu-id="aabcb-106">In WCF, service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="aabcb-107">No entanto, em um serviço de fluxo de trabalho, esses contratos são parte do processo de negócios em si; eles são expostos nos metadados por um processo chamado inferência do contrato.</span><span class="sxs-lookup"><span data-stu-id="aabcb-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="aabcb-108">Inferência de tipos de contrato</span><span class="sxs-lookup"><span data-stu-id="aabcb-108">Contract Inference</span></span>  
 <span data-ttu-id="aabcb-109">Quando um serviço de fluxo de trabalho é hospedado usando <xref:System.ServiceModel.Activities.WorkflowServiceHost>, a definição de fluxo de trabalho é examinada e um contrato é gerado com base no conjunto de atividades encontradas no fluxo de trabalho de mensagens.</span><span class="sxs-lookup"><span data-stu-id="aabcb-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="aabcb-110">Em particular as atividades e as propriedades a seguir são usadas para gerar o contrato:</span><span class="sxs-lookup"><span data-stu-id="aabcb-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <span data-ttu-id="aabcb-111"><xref:System.ServiceModel.Activities.Receive> Atividade</span><span class="sxs-lookup"><span data-stu-id="aabcb-111"><xref:System.ServiceModel.Activities.Receive> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>   
 
 <span data-ttu-id="aabcb-112"><xref:System.ServiceModel.Activities.SendReply> Atividade</span><span class="sxs-lookup"><span data-stu-id="aabcb-112"><xref:System.ServiceModel.Activities.SendReply> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <span data-ttu-id="aabcb-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Atividade</span><span class="sxs-lookup"><span data-stu-id="aabcb-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activity</span></span>  
  
 <span data-ttu-id="aabcb-114">O resultado final da inferência do contrato é uma descrição do serviço usando as mesmas estruturas de dados como contratos de serviço e operação do WCF.</span><span class="sxs-lookup"><span data-stu-id="aabcb-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="aabcb-115">Essas informações, em seguida, são usadas para expor o WSDL para o serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="aabcb-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aabcb-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aabcb-116">See also</span></span>

- [<span data-ttu-id="aabcb-117">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="aabcb-117">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="aabcb-118">Atividades de mensagens</span><span class="sxs-lookup"><span data-stu-id="aabcb-118">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
- [<span data-ttu-id="aabcb-119">Como: Criar um serviço de fluxo de trabalho com atividades de mensagem</span><span class="sxs-lookup"><span data-stu-id="aabcb-119">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [<span data-ttu-id="aabcb-120">Como: Criar um serviço de fluxo de trabalho que consome um contrato de serviço existente</span><span class="sxs-lookup"><span data-stu-id="aabcb-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
