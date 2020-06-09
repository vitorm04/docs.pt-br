---
title: Utilizando contratos no fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: def100f9483ea9ac8bf1aa3285d76edccffb030a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595005"
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="893cc-102">Utilizando contratos no fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="893cc-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="893cc-103">Ao implementar um serviço, você define um número de contratos que descrevem o serviço e os dados que ele envia e recebe.</span><span class="sxs-lookup"><span data-stu-id="893cc-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="893cc-104">Os dados são representados como contratos de dados e contratos de mensagem; o WCF e os serviços de fluxo de trabalho usam as definições de contrato de dados e de contrato de mensagem como parte das descrições de serviço.</span><span class="sxs-lookup"><span data-stu-id="893cc-104">The data is represented as data contracts and message contracts; both WCF and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="893cc-105">O próprio serviço expõe metadados (na forma de WSDL) para descrever as operações do serviço.</span><span class="sxs-lookup"><span data-stu-id="893cc-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="893cc-106">No WCF, os contratos de serviço e os contratos de operação definem o serviço e as operações que ele suporta.</span><span class="sxs-lookup"><span data-stu-id="893cc-106">In WCF, service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="893cc-107">No entanto, em um serviço de fluxo de trabalho, esses contratos fazem parte do próprio processo de negócios; Eles são expostos em metadados por um processo chamado inferência de contrato.</span><span class="sxs-lookup"><span data-stu-id="893cc-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="893cc-108">Inferência de contrato</span><span class="sxs-lookup"><span data-stu-id="893cc-108">Contract Inference</span></span>  
 <span data-ttu-id="893cc-109">Quando um serviço de fluxo de trabalho é hospedado usando <xref:System.ServiceModel.Activities.WorkflowServiceHost> , a definição de fluxo de trabalho é examinada e um contrato é gerado com base no conjunto de atividades de mensagens encontradas no fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="893cc-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="893cc-110">Em particular, as seguintes atividades e propriedades são usadas para gerar o contrato:</span><span class="sxs-lookup"><span data-stu-id="893cc-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <span data-ttu-id="893cc-111"><xref:System.ServiceModel.Activities.Receive> Atividade</span><span class="sxs-lookup"><span data-stu-id="893cc-111"><xref:System.ServiceModel.Activities.Receive> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>

 <span data-ttu-id="893cc-112"><xref:System.ServiceModel.Activities.SendReply> Atividade</span><span class="sxs-lookup"><span data-stu-id="893cc-112"><xref:System.ServiceModel.Activities.SendReply> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <span data-ttu-id="893cc-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Atividade</span><span class="sxs-lookup"><span data-stu-id="893cc-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activity</span></span>  
  
 <span data-ttu-id="893cc-114">O resultado final da inferência de contrato é uma descrição do serviço usando as mesmas estruturas de dados que o serviço WCF e os contratos de operação.</span><span class="sxs-lookup"><span data-stu-id="893cc-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="893cc-115">Essas informações são usadas para expor WSDL para o serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="893cc-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="893cc-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="893cc-116">See also</span></span>

- [<span data-ttu-id="893cc-117">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="893cc-117">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="893cc-118">Atividades de mensagem</span><span class="sxs-lookup"><span data-stu-id="893cc-118">Messaging Activities</span></span>](messaging-activities.md)
- [<span data-ttu-id="893cc-119">Como criar um serviço de fluxo de trabalho com atividades de mensagens</span><span class="sxs-lookup"><span data-stu-id="893cc-119">How to: Create a Workflow Service with Messaging Activities</span></span>](how-to-create-a-workflow-service-with-messaging-activities.md)
- [<span data-ttu-id="893cc-120">Como criar um serviço de fluxo de trabalho que consome um contrato de serviço existente</span><span class="sxs-lookup"><span data-stu-id="893cc-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
