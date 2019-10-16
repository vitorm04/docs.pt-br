---
title: Como especificar uma associação de serviço em código
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 67ab5dd8-79c1-4e62-aa75-828ea918a53a
ms.openlocfilehash: 3c6cfd084055d59d3292b49897ff710f14f92737
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320868"
---
# <a name="how-to-specify-a-service-binding-in-code"></a><span data-ttu-id="b13d1-102">Como especificar uma associação de serviço em código</span><span class="sxs-lookup"><span data-stu-id="b13d1-102">How to: Specify a Service Binding in Code</span></span>
<span data-ttu-id="b13d1-103">Neste exemplo, um contrato `ICalculator` é definido para um serviço de calculadora, o serviço é implementado na classe `CalculatorService` e, em seguida, seu ponto de extremidade é definido no código, onde é especificado que o serviço deve usar a classe <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="b13d1-103">In this example, an `ICalculator` contract is defined for a calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is defined in code, where it is specified that the service must use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="b13d1-104">Geralmente, é a prática recomendada especificar a associação e as informações de endereço de forma declarativa na configuração, em vez de imperativa no código.</span><span class="sxs-lookup"><span data-stu-id="b13d1-104">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="b13d1-105">A definição de pontos de extremidade no código geralmente não é prática porque as associações e os endereços para um serviço implantado são normalmente diferentes daqueles usados enquanto o serviço está sendo desenvolvido.</span><span class="sxs-lookup"><span data-stu-id="b13d1-105">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="b13d1-106">Em geral, manter as informações de vinculação e endereçamento do código permite que elas sejam alteradas sem a necessidade de recompilar ou reimplantar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b13d1-106">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="b13d1-107">Para obter uma descrição de como configurar esse serviço usando elementos de configuração em vez de código, consulte [como especificar uma associação de serviço na configuração](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="b13d1-107">For a description of how to configure this service using configuration elements instead of code, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
### <a name="to-specify-in-code-to-use-the-basichttpbinding-for-the-service"></a><span data-ttu-id="b13d1-108">Para especificar no código usar o BasicHttpBinding para o serviço</span><span class="sxs-lookup"><span data-stu-id="b13d1-108">To specify in code to use the BasicHttpBinding for the service</span></span>  
  
1. <span data-ttu-id="b13d1-109">Defina um contrato de serviço para o tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="b13d1-109">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="b13d1-110">Implemente o contrato de serviço em uma classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="b13d1-110">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. <span data-ttu-id="b13d1-111">No aplicativo de hospedagem, crie o endereço base para o serviço e a associação a ser usada com o serviço.</span><span class="sxs-lookup"><span data-stu-id="b13d1-111">In the hosting application, create the base address for the service and the binding to use with the service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. <span data-ttu-id="b13d1-112">Crie o host para o serviço, adicione o ponto de extremidade e, em seguida, abra o host.</span><span class="sxs-lookup"><span data-stu-id="b13d1-112">Create the host for the service, add the endpoint, and then open the host.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#4)]
     [!code-vb[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#4)]  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="b13d1-113">Para modificar os valores padrão das propriedades de associação</span><span class="sxs-lookup"><span data-stu-id="b13d1-113">To modify the default values of the binding properties</span></span>  
  
1. <span data-ttu-id="b13d1-114">Para modificar um dos valores de propriedade padrão da classe <xref:System.ServiceModel.BasicHttpBinding>, defina o valor da propriedade na associação ao novo valor antes de criar o host.</span><span class="sxs-lookup"><span data-stu-id="b13d1-114">To modify one of the default property values of the <xref:System.ServiceModel.BasicHttpBinding> class, set the property value on the binding to the new value before creating the host.</span></span> <span data-ttu-id="b13d1-115">Por exemplo, para alterar os valores de tempo limite de abertura e fechamento padrão de 1 minuto para 2 minutos, use o seguinte.</span><span class="sxs-lookup"><span data-stu-id="b13d1-115">For example, to change the default open and close timeout values of 1 minute to 2 minutes, use the following.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#5)]
     [!code-vb[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b13d1-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b13d1-116">See also</span></span>

- [<span data-ttu-id="b13d1-117">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b13d1-117">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b13d1-118">Especificando um endereço do ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="b13d1-118">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)
