---
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: 3e3e4bf18b204db5a4068cc3f6cbb1337d5f611d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254308"
---
# <a name="comcontracts"></a><span data-ttu-id="d03c6-101">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="d03c6-101">\<comContracts></span></span>
<span data-ttu-id="d03c6-102">O `comContracts` seção de configuração contém elementos que permitem que você especificar várias propriedades de um contrato de serviço de integração COM+.</span><span class="sxs-lookup"><span data-stu-id="d03c6-102">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="d03c6-103">Especificando o Namespace e um contrato</span><span class="sxs-lookup"><span data-stu-id="d03c6-103">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="d03c6-104">Contratos de serviço de integração COM+ são atualmente restritos ao `http://tempuri.org` namespace, e o nome do contrato é derivado da interface COM suporte.</span><span class="sxs-lookup"><span data-stu-id="d03c6-104">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="d03c6-105">No entanto, você pode especificar alternativas usando o `comContracts` seção no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d03c6-105">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="d03c6-106">Por exemplo, você pode usar a configuração a seguir para especificar o nome de namespace e o contrato do contrato de serviço, bem como uma opção para impor o uso em associações de sessão.</span><span class="sxs-lookup"><span data-stu-id="d03c6-106">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="d03c6-107">Quando o serviço é inicializado, os namespaces especificados e os nomes de contrato são aplicados as descrições de serviço gerado.</span><span class="sxs-lookup"><span data-stu-id="d03c6-107">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="d03c6-108">Quando essa seção está vazia, a inicialização de serviço aplica-se um nome de namespace e contrato padrão obtido a ID de interface COM suporte.</span><span class="sxs-lookup"><span data-stu-id="d03c6-108">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="d03c6-109">Além disso, você pode usar o [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elemento para especificar métodos COM+ que são expostos quando a interface em um componente COM+ é exposta como um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="d03c6-109">In addition, you can use the [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="d03c6-110">Você também pode usar o [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) para especificar os tipos persistentes usados na integração.</span><span class="sxs-lookup"><span data-stu-id="d03c6-110">You can also use the [\<persistableTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="d03c6-111">Por fim, você pode usar o [ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) elemento incluir definido pelo usuário tipos (UDT) que devem ser incluídas no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="d03c6-111">Finally, you can use the [\<userDefinedType>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d03c6-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d03c6-112">See also</span></span>
- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="d03c6-113">\<exposedMethod></span><span class="sxs-lookup"><span data-stu-id="d03c6-113">\<exposedMethod></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)
- [<span data-ttu-id="d03c6-114">\<persistableTypes></span><span class="sxs-lookup"><span data-stu-id="d03c6-114">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)
- [<span data-ttu-id="d03c6-115">\<userDefinedType></span><span class="sxs-lookup"><span data-stu-id="d03c6-115">\<userDefinedType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)
- [<span data-ttu-id="d03c6-116">\<comContract></span><span class="sxs-lookup"><span data-stu-id="d03c6-116">\<comContract></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)
- [<span data-ttu-id="d03c6-117">Integração de aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="d03c6-117">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="d03c6-118">Como: Definir as configurações de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="d03c6-118">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
