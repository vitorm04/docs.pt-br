---
title: "Como criar um serviço que requer sessões"
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
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1fba00b6b8aed8e27d5f16612bb77191f6674abe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="36be4-102">Como criar um serviço que requer sessões</span><span class="sxs-lookup"><span data-stu-id="36be4-102">How to: Create a Service That Requires Sessions</span></span>
<span data-ttu-id="36be4-103">As sessões criam um estado compartilhado entre dois ou mais pontos de extremidade que habilita recursos úteis como retornos de chamada, a segurança de vários salto e associações entre clientes e instâncias de serviço.</span><span class="sxs-lookup"><span data-stu-id="36be4-103">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="36be4-104">sessões em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplicativos, consulte [sessões usando](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="36be4-104"> sessions in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] applications, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="36be4-105">Para especificar que um contrato exige sua associação dar suporte a sessões</span><span class="sxs-lookup"><span data-stu-id="36be4-105">To specify that a contract require its binding to support sessions</span></span>  
  
1.  <span data-ttu-id="36be4-106">Crie um contrato de serviço com pelo menos uma operação.</span><span class="sxs-lookup"><span data-stu-id="36be4-106">Create a service contract with at least one operation.</span></span> <span data-ttu-id="36be4-107">Para obter um exemplo de como criar um contrato de serviço, consulte [como: definir um contrato de serviço](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="36be4-107">For an example of how to create a service contract, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2.  <span data-ttu-id="36be4-108">Modificar o <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> que declara o contrato, definindo o <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> propriedade como:</span><span class="sxs-lookup"><span data-stu-id="36be4-108">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    -   <span data-ttu-id="36be4-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>Se este contrato deve ser executado em uma sessão.</span><span class="sxs-lookup"><span data-stu-id="36be4-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> if this contract must be run within a session.</span></span>  
  
    -   <span data-ttu-id="36be4-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>Se este contrato pode ser executado em uma sessão.</span><span class="sxs-lookup"><span data-stu-id="36be4-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> if this contract can be run within a session.</span></span>  
  
    -   <span data-ttu-id="36be4-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>Se este contrato não deve ser executado em uma sessão.</span><span class="sxs-lookup"><span data-stu-id="36be4-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> if this contract must not be run within a session.</span></span>  
  
3.  <span data-ttu-id="36be4-112">Configure o ponto de extremidade de serviço para usar uma associação que dá suporte a sessões.</span><span class="sxs-lookup"><span data-stu-id="36be4-112">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="36be4-113">O exemplo de configuração a seguir mostra o uso do <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, que oferece suporte a um WS`-`ReliableMessaging sessão.</span><span class="sxs-lookup"><span data-stu-id="36be4-113">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]   
  
## <a name="example"></a><span data-ttu-id="36be4-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="36be4-114">Example</span></span>  
 <span data-ttu-id="36be4-115">O exemplo de código a seguir mostra como especificar um requisito de contrato de nível de sessão e usar um arquivo de configuração para dar suporte a esse requisito com o <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> associação.</span><span class="sxs-lookup"><span data-stu-id="36be4-115">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)] 
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]      
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]     
  
## <a name="see-also"></a><span data-ttu-id="36be4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36be4-116">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>  
 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
