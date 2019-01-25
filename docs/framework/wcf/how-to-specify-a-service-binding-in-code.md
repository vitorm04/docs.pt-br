---
title: 'Como: Especificar uma associação de serviço no código'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 67ab5dd8-79c1-4e62-aa75-828ea918a53a
ms.openlocfilehash: f39b9d7bfdc1a5d8bf33c20f047738be1e41f226
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531193"
---
# <a name="how-to-specify-a-service-binding-in-code"></a><span data-ttu-id="497b1-102">Como: Especificar uma associação de serviço no código</span><span class="sxs-lookup"><span data-stu-id="497b1-102">How to: Specify a Service Binding in Code</span></span>
<span data-ttu-id="497b1-103">Neste exemplo, uma `ICalculator` contrato é definido para um serviço de Calculadora e, em seguida, o serviço é implementado de `CalculatorService` classe e, em seguida, seu ponto de extremidade é definido no código, onde ele é especificado que o serviço deve usar o <xref:System.ServiceModel.BasicHttpBinding> classe.</span><span class="sxs-lookup"><span data-stu-id="497b1-103">In this example, an `ICalculator` contract is defined for a calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is defined in code, where it is specified that the service must use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="497b1-104">Ele geralmente é a prática recomendada para especificar declarativamente as informações de endereço e associação na configuração em vez de imperativa no código.</span><span class="sxs-lookup"><span data-stu-id="497b1-104">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="497b1-105">Definir pontos de extremidade no código geralmente não é prático porque as associações e endereços para um serviço implantado normalmente são diferentes daqueles usados enquanto o serviço está sendo desenvolvido.</span><span class="sxs-lookup"><span data-stu-id="497b1-105">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="497b1-106">De modo geral, informações fora do código de endereçamento e manter a associação permite que eles alterem os sem ter que recompilar ou reimplantar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="497b1-106">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="497b1-107">Para obter uma descrição de como configurar esse serviço usando os elementos de configuração em vez de código, consulte [como: Especificar uma associação de serviço na configuração](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="497b1-107">For a description of how to configure this service using configuration elements instead of code, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
### <a name="to-specify-in-code-to-use-the-basichttpbinding-for-the-service"></a><span data-ttu-id="497b1-108">Para especificar no código para usar o BasicHttpBinding para o serviço</span><span class="sxs-lookup"><span data-stu-id="497b1-108">To specify in code to use the BasicHttpBinding for the service</span></span>  
  
1.  <span data-ttu-id="497b1-109">Defina um contrato de serviço para o tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="497b1-109">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2.  <span data-ttu-id="497b1-110">Implemente o contrato de serviço em uma classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="497b1-110">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3.  <span data-ttu-id="497b1-111">No aplicativo de hospedagem, crie o endereço base para o serviço e associação a ser usada com o serviço.</span><span class="sxs-lookup"><span data-stu-id="497b1-111">In the hosting application, create the base address for the service and the binding to use with the service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4.  <span data-ttu-id="497b1-112">Criar o host para o serviço, adicione o ponto de extremidade e, em seguida, abra o host.</span><span class="sxs-lookup"><span data-stu-id="497b1-112">Create the host for the service, add the endpoint, and then open the host.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#4)]
     [!code-vb[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#4)]  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="497b1-113">Para modificar os valores padrão das propriedades de associação</span><span class="sxs-lookup"><span data-stu-id="497b1-113">To modify the default values of the binding properties</span></span>  
  
1.  <span data-ttu-id="497b1-114">Para modificar um dos valores de propriedade padrão da <xref:System.ServiceModel.BasicHttpBinding> de classe, defina o valor da propriedade na associação para o novo valor antes de criar o host.</span><span class="sxs-lookup"><span data-stu-id="497b1-114">To modify one of the default property values of the <xref:System.ServiceModel.BasicHttpBinding> class, set the property value on the binding to the new value before creating the host.</span></span> <span data-ttu-id="497b1-115">Por exemplo, para alterar os valores de tempo limite de abertura e fechamento do padrão de 1 minuto para 2 minutos, use o seguinte.</span><span class="sxs-lookup"><span data-stu-id="497b1-115">For example, to change the default open and close timeout values of 1 minute to 2 minutes, use the following.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#5)]
     [!code-vb[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="497b1-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="497b1-116">See also</span></span>
- [<span data-ttu-id="497b1-117">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="497b1-117">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="497b1-118">Especificando um endereço do ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="497b1-118">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
