---
title: Como criar um contrato unidirecional
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fb899bdc8d1452046b71fdce5d0782e1d1338d2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-one-way-contract"></a><span data-ttu-id="c2036-102">Como criar um contrato unidirecional</span><span class="sxs-lookup"><span data-stu-id="c2036-102">How to: Create a One-Way Contract</span></span>
<span data-ttu-id="c2036-103">Este tópico mostra as etapas básicas para criar métodos que usam um contrato unidirecional.</span><span class="sxs-lookup"><span data-stu-id="c2036-103">This topic shows the basic steps to create methods that use a one-way contract.</span></span> <span data-ttu-id="c2036-104">Esses métodos invocar operações em um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] de um cliente de serviço, mas não espera uma resposta.</span><span class="sxs-lookup"><span data-stu-id="c2036-104">Such methods invoke operations on a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service from a client but do not expect a reply.</span></span> <span data-ttu-id="c2036-105">Esse tipo de contrato pode ser usado, por exemplo, para publicar as notificações para vários assinantes.</span><span class="sxs-lookup"><span data-stu-id="c2036-105">This type of contract can be used, for example, to publish notifications to many subscribers.</span></span> <span data-ttu-id="c2036-106">Você também pode usar os contratos unidirecionais ao criar um contrato duplex (bidirecional), que permite que clientes e servidores para se comunicar uns com os outros independentemente para que qualquer um pode iniciar chamadas para o outro.</span><span class="sxs-lookup"><span data-stu-id="c2036-106">You can also use one-way contracts when creating a duplex (two-way) contract, which allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="c2036-107">Isso pode permitir que, em particular, o servidor fazer chamadas unidirecionais para o cliente que o cliente pode tratar eventos.</span><span class="sxs-lookup"><span data-stu-id="c2036-107">This can allow, in particular, the server to make one-way calls to the client that the client can treat as events.</span></span> <span data-ttu-id="c2036-108">Para obter informações detalhadas sobre como especificar métodos unidirecionais, consulte o <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade e o <xref:System.ServiceModel.OperationContractAttribute> classe.</span><span class="sxs-lookup"><span data-stu-id="c2036-108">For detailed information about specifying one-way methods, see the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property and the <xref:System.ServiceModel.OperationContractAttribute> class.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="c2036-109">criar um aplicativo cliente para um contrato duplex, consulte [como: serviços do Access com unidirecional e contratos de solicitação-resposta](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="c2036-109"> creating a client application for a duplex contract, see [How to: Access Services with One-Way and Request-Reply Contracts](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md).</span></span> <span data-ttu-id="c2036-110">Para obter um exemplo de funcionamento, consulte o [unidirecional](../../../../docs/framework/wcf/samples/one-way.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="c2036-110">For a working sample, see the [One-Way](../../../../docs/framework/wcf/samples/one-way.md) sample.</span></span>  
  
### <a name="to-create-a-one-way-contract"></a><span data-ttu-id="c2036-111">Para criar um contrato unidirecional</span><span class="sxs-lookup"><span data-stu-id="c2036-111">To create a one-way contract</span></span>  
  
1.  <span data-ttu-id="c2036-112">Criar o contrato de serviço aplicando o <xref:System.ServiceModel.ServiceContractAttribute> classe para a interface que define os métodos de serviço deve ser implementado.</span><span class="sxs-lookup"><span data-stu-id="c2036-112">Create the service contract by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface that defines the methods the service is to implement.</span></span>  
  
2.  <span data-ttu-id="c2036-113">Indicar quais métodos na interface um cliente pode chamada aplicando o <xref:System.ServiceModel.OperationContractAttribute> classe para eles.</span><span class="sxs-lookup"><span data-stu-id="c2036-113">Indicate which methods in the interface a client can invoked by applying the <xref:System.ServiceModel.OperationContractAttribute> class to them.</span></span>  
  
3.  <span data-ttu-id="c2036-114">Designar operações que não devem ter nenhuma saída (nenhum valor de retorno e nenhum limite ou parâmetros ref) como unidirecional, definindo o <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="c2036-114">Designate operations that must have no output (no return value and no out or ref parameters) as one-way by setting the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true`.</span></span> <span data-ttu-id="c2036-115">Observe que as operações que executar o <xref:System.ServiceModel.OperationContractAttribute> classe satisfazer um contrato de solicitação-resposta por padrão porque o <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> é de propriedade `false` por padrão.</span><span class="sxs-lookup"><span data-stu-id="c2036-115">Note that the operations that carry the <xref:System.ServiceModel.OperationContractAttribute> class satisfy a request-reply contract by default because the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property is `false` by default.</span></span> <span data-ttu-id="c2036-116">Portanto, você deve especificar explicitamente o valor da propriedade de atributo para ser `true` se você quiser um contrato unidirecional para o método.</span><span class="sxs-lookup"><span data-stu-id="c2036-116">So you must explicitly specify the value of the attribute property to be `true` if you want a one-way contract for the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2036-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c2036-117">Example</span></span>  
 <span data-ttu-id="c2036-118">O exemplo de código a seguir define um contrato para um serviço que inclui vários métodos unidirecionais.</span><span class="sxs-lookup"><span data-stu-id="c2036-118">The following code example defines a contract for a service that includes several one-way methods.</span></span> <span data-ttu-id="c2036-119">Todos os métodos têm contratos unidirecionais exceto `Equals`, que usa como padrão solicitação-resposta e retorna um resultado.</span><span class="sxs-lookup"><span data-stu-id="c2036-119">All of the methods have one-way contracts except `Equals`, which defaults to request-reply and returns a result.</span></span>  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c2036-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2036-120">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 <span data-ttu-id="c2036-121">[Designing and Implementing Services](../../../../docs/framework/wcf/designing-and-implementing-services.md) (Serviços de design e implantação)</span><span class="sxs-lookup"><span data-stu-id="c2036-121">[Designing and Implementing Services](../../../../docs/framework/wcf/designing-and-implementing-services.md)</span></span>  
 <span data-ttu-id="c2036-122">[How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) (Como definir um contrato de serviço)</span><span class="sxs-lookup"><span data-stu-id="c2036-122">[How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)</span></span>  
 [<span data-ttu-id="c2036-123">Sessão</span><span class="sxs-lookup"><span data-stu-id="c2036-123">Session</span></span>](../../../../docs/framework/wcf/samples/session.md)  
 [<span data-ttu-id="c2036-124">Como: criar um contrato Duplex</span><span class="sxs-lookup"><span data-stu-id="c2036-124">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
