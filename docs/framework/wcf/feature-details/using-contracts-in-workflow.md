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
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="07d10-102">Utilizando contratos no fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="07d10-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="07d10-103">Ao implementar um serviço, você define uma série de contratos que descrevem o serviço e os dados que ele envia e recebe.</span><span class="sxs-lookup"><span data-stu-id="07d10-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="07d10-104">Os dados são representados como contratos de dados e contratos de mensagens; tanto os serviços wcf quanto de fluxo de trabalho usam definições de contrato de dados e contrato de mensagem como parte das descrições do serviço.</span><span class="sxs-lookup"><span data-stu-id="07d10-104">The data is represented as data contracts and message contracts; both WCF and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="07d10-105">O próprio serviço expõe metadados (sob a forma de WSDL) a fim de descrever as operações do serviço.</span><span class="sxs-lookup"><span data-stu-id="07d10-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="07d10-106">No WCF, os contratos de prestação de serviços e contratos de operação definem o serviço e as operações que suporta.</span><span class="sxs-lookup"><span data-stu-id="07d10-106">In WCF, service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="07d10-107">No entanto, em um serviço de fluxo de trabalho, esses contratos fazem parte do próprio processo de negócios; eles são expostos em metadados por um processo chamado inferência contratual.</span><span class="sxs-lookup"><span data-stu-id="07d10-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="07d10-108">Inferência de Contrato</span><span class="sxs-lookup"><span data-stu-id="07d10-108">Contract Inference</span></span>  
 <span data-ttu-id="07d10-109">Quando um serviço de fluxo <xref:System.ServiceModel.Activities.WorkflowServiceHost>de trabalho é hospedado usando, a definição do fluxo de trabalho é examinada e um contrato é gerado com base no conjunto de atividades de mensagens encontradas no fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="07d10-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="07d10-110">Em particular, as seguintes atividades e propriedades são utilizadas para gerar o contrato:</span><span class="sxs-lookup"><span data-stu-id="07d10-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <span data-ttu-id="07d10-111"><xref:System.ServiceModel.Activities.Receive> Atividade</span><span class="sxs-lookup"><span data-stu-id="07d10-111"><xref:System.ServiceModel.Activities.Receive> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>

 <span data-ttu-id="07d10-112"><xref:System.ServiceModel.Activities.SendReply> Atividade</span><span class="sxs-lookup"><span data-stu-id="07d10-112"><xref:System.ServiceModel.Activities.SendReply> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <span data-ttu-id="07d10-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Atividade</span><span class="sxs-lookup"><span data-stu-id="07d10-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activity</span></span>  
  
 <span data-ttu-id="07d10-114">O resultado final da inferência contratual é uma descrição do serviço utilizando as mesmas estruturas de dados que os contratos de serviço e operação do WCF.</span><span class="sxs-lookup"><span data-stu-id="07d10-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="07d10-115">Essas informações são então usadas para expor o WSDL para o serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="07d10-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07d10-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="07d10-116">See also</span></span>

- [<span data-ttu-id="07d10-117">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="07d10-117">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="07d10-118">Atividades de mensagem</span><span class="sxs-lookup"><span data-stu-id="07d10-118">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
- [<span data-ttu-id="07d10-119">Como criar um serviço de fluxo de trabalho com atividades de mensagens</span><span class="sxs-lookup"><span data-stu-id="07d10-119">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [<span data-ttu-id="07d10-120">Como criar um serviço de fluxo de trabalho que consome um contrato de serviço existente</span><span class="sxs-lookup"><span data-stu-id="07d10-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
