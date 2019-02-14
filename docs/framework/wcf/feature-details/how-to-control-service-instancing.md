---
title: 'Como: Controlar instanciação de serviço'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
ms.openlocfilehash: 06324b30d2fbd68a12619375024b9f86019adbb1
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56260953"
---
# <a name="how-to-control-service-instancing"></a><span data-ttu-id="dd504-102">Como: Controlar instanciação de serviço</span><span class="sxs-lookup"><span data-stu-id="dd504-102">How to: Control Service Instancing</span></span>
<span data-ttu-id="dd504-103">Definir o modo de instância de um serviço permite que você especifique quando um <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (e seu objeto de serviço associado definido pelo usuário) é criado.</span><span class="sxs-lookup"><span data-stu-id="dd504-103">Setting the instance mode of a service enables you to specify when a <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (and its associated user-defined service object) is created.</span></span> <span data-ttu-id="dd504-104">Consulte o <xref:System.ServiceModel.InstanceContextMode> enumeração para os modos possíveis.</span><span class="sxs-lookup"><span data-stu-id="dd504-104">See the <xref:System.ServiceModel.InstanceContextMode> enumeration for the possible modes.</span></span> <span data-ttu-id="dd504-105">Para obter mais informações sobre comportamentos, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="dd504-105">For more information about behaviors, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span> <span data-ttu-id="dd504-106">Para obter exemplos de funcionamento, consulte [comportamentos](../../../../docs/framework/wcf/samples/behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="dd504-106">For working examples, see [Behaviors](../../../../docs/framework/wcf/samples/behaviors.md).</span></span>  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a><span data-ttu-id="dd504-107">Para controlar o tempo de vida de instância de serviço usando código</span><span class="sxs-lookup"><span data-stu-id="dd504-107">To control the service instance lifetime using code</span></span>  
  
1.  <span data-ttu-id="dd504-108">Aplicar o <xref:System.ServiceModel.ServiceBehaviorAttribute> à classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="dd504-108">Apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> to the service class.</span></span>  
  
2.  <span data-ttu-id="dd504-109">Defina as <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedade para um dos seguintes valores: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, ou <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="dd504-109">Set the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property to one of the following values: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, or <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span>  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="dd504-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dd504-110">Example</span></span>  
 <span data-ttu-id="dd504-111">O seguinte exemplo de código define a <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedade do <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo <xref:System.ServiceModel.InstanceContextMode.PerCall>.</span><span class="sxs-lookup"><span data-stu-id="dd504-111">The following code example sets the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property of the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to <xref:System.ServiceModel.InstanceContextMode.PerCall>.</span></span>  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="dd504-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd504-112">See also</span></span>
- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>
- <xref:System.ServiceModel.InstanceContextMode>
- [<span data-ttu-id="dd504-113">Serviço: Exemplos de comportamentos</span><span class="sxs-lookup"><span data-stu-id="dd504-113">Service: Behaviors Samples</span></span>](../samples/behaviors.md)
