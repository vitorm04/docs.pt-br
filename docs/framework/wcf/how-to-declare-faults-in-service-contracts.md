---
title: 'Como: declarar falhas em contratos de serviço'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 6f08ef6eb62b31b0969779d51d0a068145a23fc0
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971964"
---
# <a name="how-to-declare-faults-in-service-contracts"></a><span data-ttu-id="9fa1d-102">Como: declarar falhas em contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="9fa1d-102">How to: Declare Faults in Service Contracts</span></span>

<span data-ttu-id="9fa1d-103">No código gerenciado, as exceções são geradas quando ocorrem condições de erro.</span><span class="sxs-lookup"><span data-stu-id="9fa1d-103">In managed code, exceptions are thrown when error conditions occur.</span></span> <span data-ttu-id="9fa1d-104">Nos aplicativos Windows Communication Foundation (WCF), no entanto, os contratos de serviço especificam quais informações de erro são retornadas aos clientes declarando falhas de SOAP no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="9fa1d-104">In Windows Communication Foundation (WCF) applications, however, service contracts specify what error information is returned to clients by declaring SOAP faults in the service contract.</span></span> <span data-ttu-id="9fa1d-105">Para obter uma visão geral da relação entre exceções e falhas, consulte [especificando e manipulando falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="9fa1d-105">For an overview of the relationship between exceptions and faults, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>

## <a name="create-a-service-contract-that-specifies-a-soap-fault"></a><span data-ttu-id="9fa1d-106">Criar um contrato de serviço que especifica uma falha de SOAP</span><span class="sxs-lookup"><span data-stu-id="9fa1d-106">Create a service contract that specifies a SOAP fault</span></span>

1. <span data-ttu-id="9fa1d-107">Crie um contrato de serviço que contenha pelo menos uma operação.</span><span class="sxs-lookup"><span data-stu-id="9fa1d-107">Create a service contract that contains at least one operation.</span></span> <span data-ttu-id="9fa1d-108">Para obter um exemplo, consulte [ Defina um contrato](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)de serviço.</span><span class="sxs-lookup"><span data-stu-id="9fa1d-108">For an example, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>

2. <span data-ttu-id="9fa1d-109">Selecione uma operação que possa especificar uma condição de erro sobre a qual os clientes podem esperar para serem notificados.</span><span class="sxs-lookup"><span data-stu-id="9fa1d-109">Select an operation that can specify an error condition about which clients can expect to be notified.</span></span> <span data-ttu-id="9fa1d-110">Para decidir quais condições de erro justificam o retorno de falhas de SOAP aos clientes, consulte [especificando e manipulando falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="9fa1d-110">To decide which error conditions justify returning SOAP faults to clients, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>

3. <span data-ttu-id="9fa1d-111">Aplique um <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> à operação selecionada e passe um tipo de falha serializável para o construtor.</span><span class="sxs-lookup"><span data-stu-id="9fa1d-111">Apply a <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> to the selected operation and pass a serializable fault type to the constructor.</span></span> <span data-ttu-id="9fa1d-112">Para obter detalhes sobre como criar e usar tipos serializáveis, consulte [especificando transferência de dados em contratos de serviço](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="9fa1d-112">For details about creating and using serializable types, see [Specifying Data Transfer in Service Contracts](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="9fa1d-113">O exemplo a seguir mostra como especificar que a `SampleMethod` operação pode resultar em um `GreetingFault`.</span><span class="sxs-lookup"><span data-stu-id="9fa1d-113">The following example shows how to specify that the `SampleMethod` operation can result in a `GreetingFault`.</span></span>

     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]

4. <span data-ttu-id="9fa1d-114">Repita as etapas 2 e 3 para todas as operações no contrato que comunicam condições de erro aos clientes.</span><span class="sxs-lookup"><span data-stu-id="9fa1d-114">Repeat steps 2 and 3 for all operations in the contract that communicate error conditions to clients.</span></span>

## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a><span data-ttu-id="9fa1d-115">Implementando uma operação para retornar uma falha de SOAP especificada</span><span class="sxs-lookup"><span data-stu-id="9fa1d-115">Implementing an Operation to Return a Specified SOAP Fault</span></span>
 <span data-ttu-id="9fa1d-116">Depois que uma operação tiver especificado que uma falha SOAP específica pode ser retornada (como no procedimento anterior) para comunicar uma condição de erro a um aplicativo de chamada, a próxima etapa será implementar essa especificação.</span><span class="sxs-lookup"><span data-stu-id="9fa1d-116">Once an operation has specified that a specific SOAP fault can be returned (such as in the preceding procedure) to communicate an error condition to a calling application, the next step is to implement that specification.</span></span>

### <a name="throw-the-specified-soap-fault-in-the-operation"></a><span data-ttu-id="9fa1d-117">Lançar a falha SOAP especificada na operação</span><span class="sxs-lookup"><span data-stu-id="9fa1d-117">Throw the specified SOAP fault in the operation</span></span>

1. <span data-ttu-id="9fa1d-118">Quando uma <xref:System.ServiceModel.FaultContractAttribute>condição de erro especificada ocorre em uma operação, o lança um <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> novo em que a falha SOAP especificada é o parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="9fa1d-118">When a <xref:System.ServiceModel.FaultContractAttribute>-specified error condition occurs in an operation, throw a new <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> where the specified SOAP fault is the type parameter.</span></span> <span data-ttu-id="9fa1d-119">O exemplo a seguir mostra como lançar o `GreetingFault` `SampleMethod` no mostrado no procedimento anterior e na seção de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9fa1d-119">The following example shows how to throw the `GreetingFault` in the `SampleMethod` shown in the preceding procedure and in the following Code section.</span></span>

     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]

## <a name="example"></a><span data-ttu-id="9fa1d-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9fa1d-120">Example</span></span>

<span data-ttu-id="9fa1d-121">O exemplo de código a seguir mostra uma implementação de uma única operação que `GreetingFault` especifica um `SampleMethod` para a operação.</span><span class="sxs-lookup"><span data-stu-id="9fa1d-121">The following code example shows an implementation of a single operation that specifies a `GreetingFault` for the `SampleMethod` operation.</span></span>

[!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
[!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]

## <a name="see-also"></a><span data-ttu-id="9fa1d-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9fa1d-122">See also</span></span>

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
