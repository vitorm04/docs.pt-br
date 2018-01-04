---
title: "Como inspecionar e modificar mensagens do serviço"
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
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64d9ccf97533be6be0da5d1e23763e8174aead3c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a><span data-ttu-id="9fbd1-102">Como inspecionar e modificar mensagens do serviço</span><span class="sxs-lookup"><span data-stu-id="9fbd1-102">How to: Inspect and Modify Messages on the Service</span></span>
<span data-ttu-id="9fbd1-103">Você pode inspecionar ou modificar as mensagens de entrada ou saídas em uma [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] cliente implementando um <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> e inseri-lo no tempo de execução do serviço.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-103">You can inspect or modify the incoming or outgoing messages across a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client by implementing a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> and inserting it into the service runtime.</span></span> <span data-ttu-id="9fbd1-104">Para obter mais informações, consulte [estendendo Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="9fbd1-104">For more information, see [Extending Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span></span> <span data-ttu-id="9fbd1-105">O recurso equivalente do serviço é o <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="9fbd1-106">Para inspecionar ou modificar as mensagens</span><span class="sxs-lookup"><span data-stu-id="9fbd1-106">To inspect or modify messages</span></span>  
  
1.  <span data-ttu-id="9fbd1-107">Implementar a interface <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-107">Implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2.  <span data-ttu-id="9fbd1-108">Implementar um <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, ou <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interface de acordo com o escopo no qual você deseja inserir facilmente o Inspetor de mensagens do serviço.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-108">Implement a <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interface depending upon the scope at which you want to easily insert your service message inspector.</span></span>  
  
3.  <span data-ttu-id="9fbd1-109">Insira seu comportamento antes de chamar o <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> método o <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-109">Insert your behavior prior to calling the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9fbd1-110">Para obter detalhes, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="9fbd1-110">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fbd1-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9fbd1-111">Example</span></span>  
 <span data-ttu-id="9fbd1-112">Os exemplos de código a seguir mostram, em ordem:</span><span class="sxs-lookup"><span data-stu-id="9fbd1-112">The following code examples show, in order:</span></span>  
  
-   <span data-ttu-id="9fbd1-113">Uma implementação de Inspetor de serviço.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-113">A service inspector implementation.</span></span>  
  
-   <span data-ttu-id="9fbd1-114">Um comportamento de serviço que insere o Inspetor.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-114">A service behavior that inserts the inspector.</span></span>  
  
-   <span data-ttu-id="9fbd1-115">Um arquivo de configuração que carrega e executa o comportamento em um aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="9fbd1-115">A configuration file that loads and runs the behavior in a service application.</span></span>  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a><span data-ttu-id="9fbd1-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9fbd1-116">See Also</span></span>  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>  
 [<span data-ttu-id="9fbd1-117">Configurando e estendendo o tempo de execução com comportamentos</span><span class="sxs-lookup"><span data-stu-id="9fbd1-117">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
