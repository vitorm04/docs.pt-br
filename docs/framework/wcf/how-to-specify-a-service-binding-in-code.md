---
title: "Como especificar uma associação de serviço em código"
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
ms.assetid: 67ab5dd8-79c1-4e62-aa75-828ea918a53a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a852fddcfa5aadbd5a942929bd131588e652cacb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-service-binding-in-code"></a><span data-ttu-id="ddb23-102">Como especificar uma associação de serviço em código</span><span class="sxs-lookup"><span data-stu-id="ddb23-102">How to: Specify a Service Binding in Code</span></span>
<span data-ttu-id="ddb23-103">Neste exemplo, um `ICalculator` contrato é definido para um serviço de cálculo, o serviço é implementado no `CalculatorService` classe e seu ponto de extremidade é definido no código, onde ele é especificado que o serviço deve usar o <xref:System.ServiceModel.BasicHttpBinding> classe.</span><span class="sxs-lookup"><span data-stu-id="ddb23-103">In this example, an `ICalculator` contract is defined for a calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is defined in code, where it is specified that the service must use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="ddb23-104">Geralmente é a prática recomendada para especificar declarativamente a associação e as informações de endereço na configuração em vez de imperativa no código.</span><span class="sxs-lookup"><span data-stu-id="ddb23-104">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="ddb23-105">Definir pontos de extremidade no código geralmente não é prático porque as associações e os endereços para um serviço implantado normalmente são diferentes daqueles usados enquanto o serviço está sendo desenvolvido.</span><span class="sxs-lookup"><span data-stu-id="ddb23-105">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="ddb23-106">Geralmente, informações sem o código de endereçamento e manter a associação permite que a alteração sem precisar recompilar ou reimplantar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ddb23-106">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="ddb23-107">Para obter uma descrição de como configurar este serviço usando os elementos de configuração em vez de código, consulte [como: especificar uma associação de serviço na configuração](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="ddb23-107">For a description of how to configure this service using configuration elements instead of code, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
### <a name="to-specify-in-code-to-use-the-basichttpbinding-for-the-service"></a><span data-ttu-id="ddb23-108">Para especificar em código para usar o BasicHttpBinding para o serviço</span><span class="sxs-lookup"><span data-stu-id="ddb23-108">To specify in code to use the BasicHttpBinding for the service</span></span>  
  
1.  <span data-ttu-id="ddb23-109">Defina um contrato de serviço para o tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="ddb23-109">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2.  <span data-ttu-id="ddb23-110">Implemente o contrato de serviço em uma classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="ddb23-110">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3.  <span data-ttu-id="ddb23-111">No aplicativo de hospedagem, crie o endereço base para o serviço e a associação para usar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="ddb23-111">In the hosting application, create the base address for the service and the binding to use with the service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4.  <span data-ttu-id="ddb23-112">Crie o host para o serviço, adicionar o ponto de extremidade e, em seguida, abrir o host.</span><span class="sxs-lookup"><span data-stu-id="ddb23-112">Create the host for the service, add the endpoint, and then open the host.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#4)]
     [!code-vb[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#4)]  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="ddb23-113">Para modificar os valores padrão das propriedades de associação</span><span class="sxs-lookup"><span data-stu-id="ddb23-113">To modify the default values of the binding properties</span></span>  
  
1.  <span data-ttu-id="ddb23-114">Para modificar um dos valores de propriedade padrão da <xref:System.ServiceModel.BasicHttpBinding> classe, defina o valor da propriedade na associação para o novo valor antes de criar o host.</span><span class="sxs-lookup"><span data-stu-id="ddb23-114">To modify one of the default property values of the <xref:System.ServiceModel.BasicHttpBinding> class, set the property value on the binding to the new value before creating the host.</span></span> <span data-ttu-id="ddb23-115">Por exemplo, para alterar os valores de tempo limite de abertura e fechamento do padrão de 1 minuto para 2 minutos, use o seguinte.</span><span class="sxs-lookup"><span data-stu-id="ddb23-115">For example, to change the default open and close timeout values of 1 minute to 2 minutes, use the following.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#5)]
     [!code-vb[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ddb23-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ddb23-116">See Also</span></span>  
 [<span data-ttu-id="ddb23-117">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="ddb23-117">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="ddb23-118">Especificando um endereço do ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="ddb23-118">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
