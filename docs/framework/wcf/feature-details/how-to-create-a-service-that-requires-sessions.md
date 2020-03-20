---
title: Como criar um serviço que requer sessões
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 495de5a926cfc0c5aab88337f5f33b991c49e71a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184984"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="efd81-102">Como criar um serviço que requer sessões</span><span class="sxs-lookup"><span data-stu-id="efd81-102">How to: Create a Service That Requires Sessions</span></span>
<span data-ttu-id="efd81-103">As sessões criam um estado compartilhado entre dois ou mais pontos finais que permite recursos úteis, como retornos de chamadas, segurança multi-hop e associações entre clientes e instâncias de serviço.</span><span class="sxs-lookup"><span data-stu-id="efd81-103">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> <span data-ttu-id="efd81-104">Para obter mais informações sobre sessões em aplicativos da Windows Communication Foundation (WCF), consulte [Usando sessões](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="efd81-104">For more information about sessions in Windows Communication Foundation (WCF) applications, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="efd81-105">Para especificar que um contrato requer sua vinculação para suportar sessões</span><span class="sxs-lookup"><span data-stu-id="efd81-105">To specify that a contract require its binding to support sessions</span></span>  
  
1. <span data-ttu-id="efd81-106">Crie um contrato de serviço com pelo menos uma operação.</span><span class="sxs-lookup"><span data-stu-id="efd81-106">Create a service contract with at least one operation.</span></span> <span data-ttu-id="efd81-107">Para um exemplo de como criar um contrato de serviço, consulte [Como: Definir um Contrato de Serviço](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="efd81-107">For an example of how to create a service contract, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2. <span data-ttu-id="efd81-108">Modificar <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> o que declara o <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> contrato definindo a propriedade para:</span><span class="sxs-lookup"><span data-stu-id="efd81-108">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    - <span data-ttu-id="efd81-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>se este contrato deve ser executado dentro de uma sessão.</span><span class="sxs-lookup"><span data-stu-id="efd81-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> if this contract must be run within a session.</span></span>  
  
    - <span data-ttu-id="efd81-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>se este contrato pode ser executado dentro de uma sessão.</span><span class="sxs-lookup"><span data-stu-id="efd81-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> if this contract can be run within a session.</span></span>  
  
    - <span data-ttu-id="efd81-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>se este contrato não deve ser executado dentro de uma sessão.</span><span class="sxs-lookup"><span data-stu-id="efd81-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> if this contract must not be run within a session.</span></span>  
  
3. <span data-ttu-id="efd81-112">Configure o ponto final do serviço para usar uma vinculação que suporte as sessões.</span><span class="sxs-lookup"><span data-stu-id="efd81-112">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="efd81-113">O exemplo de configuração <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>a seguir mostra o`-`uso do , que suporta uma sessão WS ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="efd81-113">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a><span data-ttu-id="efd81-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="efd81-114">Example</span></span>  
 <span data-ttu-id="efd81-115">O código de exemplo a seguir mostra como especificar um requisito de <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> sessão de nível de contrato e usar um arquivo de configuração para suportar esse requisito com a vinculação.</span><span class="sxs-lookup"><span data-stu-id="efd81-115">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a><span data-ttu-id="efd81-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="efd81-116">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
