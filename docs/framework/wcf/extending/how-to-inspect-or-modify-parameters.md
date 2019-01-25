---
title: 'Como: Inspecionar ou modificar parâmetros'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: 329e25b31deb1761d8522636675fe3160cad9e15
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721198"
---
# <a name="how-to-inspect-or-modify-parameters"></a><span data-ttu-id="6b452-102">Como: Inspecionar ou modificar parâmetros</span><span class="sxs-lookup"><span data-stu-id="6b452-102">How to: Inspect or Modify Parameters</span></span>
<span data-ttu-id="6b452-103">Você pode inspecionar ou modificar as mensagens de entrada ou saídas para uma única operação em um objeto de cliente do Windows Communication Foundation (WCF) ou um serviço WCF, Implementando o <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface e inseri-lo no tempo de execução do cliente ou serviço.</span><span class="sxs-lookup"><span data-stu-id="6b452-103">You can inspect or modify the incoming or outgoing messages for a single operation on a Windows Communication Foundation (WCF) client object or a WCF service by implementing the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface and inserting it into the client or service runtime.</span></span> <span data-ttu-id="6b452-104">Normalmente um comportamento de operação é usado para adicionar os inspetores de parâmetro para uma única operação; outros comportamentos podem ser usados para fornecer acesso fácil ao tempo de execução em um escopo maior.</span><span class="sxs-lookup"><span data-stu-id="6b452-104">Typically an operation behavior is used to add parameter inspectors for a single operation; other behaviors can be used to provide easy access to the runtime at a greater scope.</span></span> <span data-ttu-id="6b452-105">Para obter mais informações, consulte [estendendo clientes](../../../../docs/framework/wcf/extending/extending-clients.md) e [estendendo Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="6b452-105">For more information, see [Extending Clients](../../../../docs/framework/wcf/extending/extending-clients.md) and [Extending Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span></span>  
  
### <a name="inspecting-or-modifying-parameters"></a><span data-ttu-id="6b452-106">Inspecionar ou modificar parâmetros</span><span class="sxs-lookup"><span data-stu-id="6b452-106">Inspecting or Modifying Parameters</span></span>  
  
1.  <span data-ttu-id="6b452-107">Implementar a interface <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6b452-107">Implement the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface.</span></span>  
  
2.  <span data-ttu-id="6b452-108">Implementar uma <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (dependendo do escopo necessário) para adicionar o Inspetor de parâmetro como o <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> propriedades.</span><span class="sxs-lookup"><span data-stu-id="6b452-108">Implement a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (depending upon the required scope) to add your parameter inspector to either the <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> or <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> properties.</span></span>  
  
3.  <span data-ttu-id="6b452-109">Inserir seu comportamento antes de chamar <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> ou o <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> método o <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6b452-109">Insert your behavior prior to calling <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6b452-110">Para obter detalhes, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="6b452-110">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b452-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6b452-111">Example</span></span>  
 <span data-ttu-id="6b452-112">Os exemplos de código a seguir mostram, na ordem:</span><span class="sxs-lookup"><span data-stu-id="6b452-112">The following code examples show, in order:</span></span>  
  
-   <span data-ttu-id="6b452-113">Uma implementação de Inspetor de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6b452-113">A parameter inspector implementation.</span></span>  
  
-   <span data-ttu-id="6b452-114">A implementação de comportamento que insere o Inspetor de parâmetro usando um <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>e um <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6b452-114">The behavior implementation that inserts the parameter inspector using a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, and an <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="6b452-115">Um arquivo de configuração que carrega e executa o comportamento de ponto de extremidade em um aplicativo cliente para inserir o Inspetor de parâmetro no cliente.</span><span class="sxs-lookup"><span data-stu-id="6b452-115">A configuration file that loads and runs the endpoint behavior in a client application to insert the parameter inspector on the client.</span></span>  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a><span data-ttu-id="6b452-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b452-116">See also</span></span>
- [<span data-ttu-id="6b452-117">Configurando e estendendo o tempo de execução com comportamentos</span><span class="sxs-lookup"><span data-stu-id="6b452-117">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
