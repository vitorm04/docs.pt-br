---
title: Como criar um serviço que requer sessões
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 29c2a87daaf763a50aa657c9badc002ff2fa27e1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593328"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="e87be-102">Como criar um serviço que requer sessões</span><span class="sxs-lookup"><span data-stu-id="e87be-102">How to: Create a Service That Requires Sessions</span></span>
<span data-ttu-id="e87be-103">As sessões criam um estado compartilhado entre dois ou mais pontos de extremidade que habilitam recursos úteis, como retornos de chamada, segurança de saltos múltiplos e associações entre clientes e instâncias de serviço.</span><span class="sxs-lookup"><span data-stu-id="e87be-103">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> <span data-ttu-id="e87be-104">Para obter mais informações sobre sessões em aplicativos Windows Communication Foundation (WCF), consulte [usando sessões](../using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="e87be-104">For more information about sessions in Windows Communication Foundation (WCF) applications, see [Using Sessions](../using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="e87be-105">Para especificar que um contrato exige sua ligação para dar suporte a sessões</span><span class="sxs-lookup"><span data-stu-id="e87be-105">To specify that a contract require its binding to support sessions</span></span>  
  
1. <span data-ttu-id="e87be-106">Crie um contrato de serviço com pelo menos uma operação.</span><span class="sxs-lookup"><span data-stu-id="e87be-106">Create a service contract with at least one operation.</span></span> <span data-ttu-id="e87be-107">Para obter um exemplo de como criar um contrato de serviço, consulte [como definir um contrato de serviço](../how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="e87be-107">For an example of how to create a service contract, see [How to: Define a Service Contract](../how-to-define-a-wcf-service-contract.md).</span></span>  
  
2. <span data-ttu-id="e87be-108">Modifique o <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> que declara o contrato definindo a <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> propriedade como:</span><span class="sxs-lookup"><span data-stu-id="e87be-108">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    - <span data-ttu-id="e87be-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>Se este contrato deve ser executado dentro de uma sessão.</span><span class="sxs-lookup"><span data-stu-id="e87be-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> if this contract must be run within a session.</span></span>  
  
    - <span data-ttu-id="e87be-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>Se esse contrato puder ser executado dentro de uma sessão.</span><span class="sxs-lookup"><span data-stu-id="e87be-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> if this contract can be run within a session.</span></span>  
  
    - <span data-ttu-id="e87be-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>Se este contrato não deve ser executado dentro de uma sessão.</span><span class="sxs-lookup"><span data-stu-id="e87be-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> if this contract must not be run within a session.</span></span>  
  
3. <span data-ttu-id="e87be-112">Configure seu ponto de extremidade de serviço para usar uma associação que dá suporte a sessões.</span><span class="sxs-lookup"><span data-stu-id="e87be-112">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="e87be-113">O exemplo de configuração a seguir mostra o uso do <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> , que dá suporte a uma `-` sessão WS ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="e87be-113">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a><span data-ttu-id="e87be-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e87be-114">Example</span></span>  
 <span data-ttu-id="e87be-115">O código de exemplo a seguir mostra como especificar um requisito de sessão de nível de contrato e usar um arquivo de configuração para dar suporte a esse requisito com a <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> associação.</span><span class="sxs-lookup"><span data-stu-id="e87be-115">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a><span data-ttu-id="e87be-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="e87be-116">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
