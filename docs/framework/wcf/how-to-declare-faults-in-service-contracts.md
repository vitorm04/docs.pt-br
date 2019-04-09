---
title: 'Como: declarar falhas em contratos de serviço'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 90abb29550ce7e027244b220f30e9fe46e282ff3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129487"
---
# <a name="how-to-declare-faults-in-service-contracts"></a><span data-ttu-id="f8041-102">Como: declarar falhas em contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="f8041-102">How to: Declare Faults in Service Contracts</span></span>
<span data-ttu-id="f8041-103">No código gerenciado, as exceções são geradas quando ocorrem condições de erro.</span><span class="sxs-lookup"><span data-stu-id="f8041-103">In managed code, exceptions are thrown when error conditions occur.</span></span> <span data-ttu-id="f8041-104">Em aplicativos do Windows Communication Foundation (WCF), no entanto, os contratos de serviço especificam quais informações de erro serão retornadas aos clientes por meio da declaração de falhas de SOAP no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="f8041-104">In Windows Communication Foundation (WCF) applications, however, service contracts specify what error information is returned to clients by declaring SOAP faults in the service contract.</span></span> <span data-ttu-id="f8041-105">Para obter uma visão geral da relação entre exceções e falhas, consulte [especificação e tratamento de falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="f8041-105">For an overview of the relationship between exceptions and faults, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
### <a name="create-a-service-contract-that-specifies-a-soap-fault"></a><span data-ttu-id="f8041-106">Criar um contrato de serviço que especifica uma falha de SOAP</span><span class="sxs-lookup"><span data-stu-id="f8041-106">Create a service contract that specifies a SOAP fault</span></span>  
  
1.  <span data-ttu-id="f8041-107">Crie um contrato de serviço que contém pelo menos uma operação.</span><span class="sxs-lookup"><span data-stu-id="f8041-107">Create a service contract that contains at least one operation.</span></span> <span data-ttu-id="f8041-108">Para obter um exemplo, consulte [ Definir um contrato de serviço](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="f8041-108">For an example, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2.  <span data-ttu-id="f8041-109">Selecione uma operação que pode especificar uma condição de erro sobre o qual os clientes podem esperar ser notificado.</span><span class="sxs-lookup"><span data-stu-id="f8041-109">Select an operation that can specify an error condition about which clients can expect to be notified.</span></span> <span data-ttu-id="f8041-110">Para decidir quais condições de erro justificam retornar falhas de SOAP aos clientes, consulte [especificação e tratamento de falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="f8041-110">To decide which error conditions justify returning SOAP faults to clients, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
3.  <span data-ttu-id="f8041-111">Aplicar um <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> para a operação selecionada e a passagem de uma falha serializável de tipo para o construtor.</span><span class="sxs-lookup"><span data-stu-id="f8041-111">Apply a <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> to the selected operation and pass a serializable fault type to the constructor.</span></span> <span data-ttu-id="f8041-112">Para obter detalhes sobre como criar e usar tipos serializáveis, consulte [especificando a transferência de dados em contratos de serviço](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="f8041-112">For details about creating and using serializable types, see [Specifying Data Transfer in Service Contracts](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="f8041-113">O exemplo a seguir mostra como especificar que o `SampleMethod` operação pode resultar em um `GreetingFault`.</span><span class="sxs-lookup"><span data-stu-id="f8041-113">The following example shows how to specify that the `SampleMethod` operation can result in a `GreetingFault`.</span></span>  
  
     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
4.  <span data-ttu-id="f8041-114">Repita as etapas 2 e 3 para todas as operações no contrato que se comunicam as condições de erro para os clientes.</span><span class="sxs-lookup"><span data-stu-id="f8041-114">Repeat steps 2 and 3 for all operations in the contract that communicate error conditions to clients.</span></span>  
  
## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a><span data-ttu-id="f8041-115">Implementando uma operação para retornar uma falha SOAP especificada</span><span class="sxs-lookup"><span data-stu-id="f8041-115">Implementing an Operation to Return a Specified SOAP Fault</span></span>  
 <span data-ttu-id="f8041-116">Depois que uma operação especificou que uma falha SOAP específica pode ser retornada (como no procedimento anterior) para se comunicar uma condição de erro para um aplicativo de chamada, a próxima etapa é implementar essa especificação.</span><span class="sxs-lookup"><span data-stu-id="f8041-116">Once an operation has specified that a specific SOAP fault can be returned (such as in the preceding procedure) to communicate an error condition to a calling application, the next step is to implement that specification.</span></span>  
  
#### <a name="throw-the-specified-soap-fault-in-the-operation"></a><span data-ttu-id="f8041-117">Gerar a falha SOAP especificada na operação</span><span class="sxs-lookup"><span data-stu-id="f8041-117">Throw the specified SOAP fault in the operation</span></span>  
  
1.  <span data-ttu-id="f8041-118">Quando um <xref:System.ServiceModel.FaultContractAttribute>-a condição de erro especificada ocorre em uma operação lançar uma nova <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> onde a falha SOAP especificada é o parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="f8041-118">When a <xref:System.ServiceModel.FaultContractAttribute>-specified error condition occurs in an operation, throw a new <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> where the specified SOAP fault is the type parameter.</span></span> <span data-ttu-id="f8041-119">O exemplo a seguir mostra como gerar o `GreetingFault` no `SampleMethod` mostrado no procedimento anterior e na seção de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="f8041-119">The following example shows how to throw the `GreetingFault` in the `SampleMethod` shown in the preceding procedure and in the following Code section.</span></span>  
  
     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="f8041-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f8041-120">Example</span></span>  
 <span data-ttu-id="f8041-121">O exemplo de código a seguir mostra uma implementação de uma única operação que especifica um `GreetingFault` para o `SampleMethod` operação.</span><span class="sxs-lookup"><span data-stu-id="f8041-121">The following code example shows an implementation of a single operation that specifies a `GreetingFault` for the `SampleMethod` operation.</span></span>  
  
 [!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
 [!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f8041-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8041-122">See also</span></span>

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
