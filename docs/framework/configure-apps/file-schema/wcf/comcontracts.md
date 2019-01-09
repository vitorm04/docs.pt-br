---
title: '&lt;comContracts&gt;'
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: 26f17a331d69c38d720fcafe65c76f50c67def09
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150780"
---
# <a name="ltcomcontractsgt"></a><span data-ttu-id="b2507-102">&lt;comContracts&gt;</span><span class="sxs-lookup"><span data-stu-id="b2507-102">&lt;comContracts&gt;</span></span>
<span data-ttu-id="b2507-103">O `comContracts` seção de configuração contém elementos que permitem que você especificar várias propriedades de um contrato de serviço de integração COM+.</span><span class="sxs-lookup"><span data-stu-id="b2507-103">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="b2507-104">Especificando o Namespace e um contrato</span><span class="sxs-lookup"><span data-stu-id="b2507-104">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="b2507-105">Contratos de serviço de integração COM+ são atualmente restritos ao `http://tempuri.org` namespace, e o nome do contrato é derivado da interface COM suporte.</span><span class="sxs-lookup"><span data-stu-id="b2507-105">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="b2507-106">No entanto, você pode especificar alternativas usando o `comContracts` seção no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="b2507-106">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="b2507-107">Por exemplo, você pode usar a configuração a seguir para especificar o nome de namespace e o contrato do contrato de serviço, bem como uma opção para impor o uso em associações de sessão.</span><span class="sxs-lookup"><span data-stu-id="b2507-107">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="b2507-108">Quando o serviço é inicializado, os namespaces especificados e os nomes de contrato são aplicados as descrições de serviço gerado.</span><span class="sxs-lookup"><span data-stu-id="b2507-108">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="b2507-109">Quando essa seção está vazia, a inicialização de serviço aplica-se um nome de namespace e contrato padrão obtido a ID de interface COM suporte.</span><span class="sxs-lookup"><span data-stu-id="b2507-109">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="b2507-110">Além disso, você pode usar o [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elemento para especificar métodos COM+ que são expostos quando a interface em um componente COM+ é exposta como um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="b2507-110">In addition, you can use the [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="b2507-111">Você também pode usar o [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) para especificar os tipos persistentes usados na integração.</span><span class="sxs-lookup"><span data-stu-id="b2507-111">You can also use the [\<persistableTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="b2507-112">Por fim, você pode usar o [ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) elemento incluir definido pelo usuário tipos (UDT) que devem ser incluídas no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="b2507-112">Finally, you can use the [\<userDefinedType>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2507-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2507-113">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [<span data-ttu-id="b2507-114">\<exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="b2507-114">\<exposedMethod></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)  
 [<span data-ttu-id="b2507-115">\<persistableTypes></span><span class="sxs-lookup"><span data-stu-id="b2507-115">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)  
 [<span data-ttu-id="b2507-116">\<userDefinedType></span><span class="sxs-lookup"><span data-stu-id="b2507-116">\<userDefinedType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [<span data-ttu-id="b2507-117">\<comContract></span><span class="sxs-lookup"><span data-stu-id="b2507-117">\<comContract></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [<span data-ttu-id="b2507-118">Integração de aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="b2507-118">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="b2507-119">Como: Definir as configurações de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="b2507-119">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
