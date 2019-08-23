---
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: d061d48374a8745dc61e1ca156e4fcbbccee5ef7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919482"
---
# <a name="comcontracts"></a><span data-ttu-id="e4f94-101">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="e4f94-101">\<comContracts></span></span>
<span data-ttu-id="e4f94-102">A `comContracts` seção de configuração contém elementos que permitem especificar várias propriedades de um contrato de serviço de integração com+.</span><span class="sxs-lookup"><span data-stu-id="e4f94-102">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="e4f94-103">Especificando o namespace e o contrato</span><span class="sxs-lookup"><span data-stu-id="e4f94-103">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="e4f94-104">Os contratos do serviço de `http://tempuri.org` integração com+ estão atualmente restritos ao namespace e o nome do contrato é derivado da interface com de suporte.</span><span class="sxs-lookup"><span data-stu-id="e4f94-104">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="e4f94-105">No entanto, você pode especificar alternativas usando a `comContracts` seção no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="e4f94-105">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="e4f94-106">Por exemplo, você pode usar a configuração a seguir para especificar o namespace e o nome do contrato do contrato de serviço, bem como uma opção para impor o uso em associações de sessão.</span><span class="sxs-lookup"><span data-stu-id="e4f94-106">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="e4f94-107">Quando o serviço é inicializado, os namespaces e os nomes de contrato especificados são aplicados às descrições de serviço geradas.</span><span class="sxs-lookup"><span data-stu-id="e4f94-107">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="e4f94-108">Quando esta seção estiver vazia, a inicialização do serviço aplicará um namespace padrão e o nome do contrato extraído da ID de interface COM de suporte.</span><span class="sxs-lookup"><span data-stu-id="e4f94-108">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="e4f94-109">Além disso, você pode usar o [ \<elemento ExposedMethod >](exposedmethod.md) para especificar métodos com+ que são expostos quando a interface em um componente com+ é exposta como um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="e4f94-109">In addition, you can use the [\<exposedMethod>](exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="e4f94-110">Você também pode usar o [ \<> persistableTypes](persistabletypes.md) para especificar tipos persistentes usados na integração.</span><span class="sxs-lookup"><span data-stu-id="e4f94-110">You can also use the [\<persistableTypes>](persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="e4f94-111">Por fim, você pode usar o elemento [ \<UserDefinedType >](userdefinedtype.md) para incluir os UDT (tipos definidos pelo usuário) que devem ser incluídos no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="e4f94-111">Finally, you can use the [\<userDefinedType>](userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4f94-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4f94-112">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="e4f94-113">\<exposedMethod></span><span class="sxs-lookup"><span data-stu-id="e4f94-113">\<exposedMethod></span></span>](exposedmethod.md)
- [<span data-ttu-id="e4f94-114">\<persistableTypes></span><span class="sxs-lookup"><span data-stu-id="e4f94-114">\<persistableTypes></span></span>](persistabletypes.md)
- [<span data-ttu-id="e4f94-115">\<userDefinedType></span><span class="sxs-lookup"><span data-stu-id="e4f94-115">\<userDefinedType></span></span>](userdefinedtype.md)
- [<span data-ttu-id="e4f94-116">\<comContract></span><span class="sxs-lookup"><span data-stu-id="e4f94-116">\<comContract></span></span>](comcontract.md)
- [<span data-ttu-id="e4f94-117">Integração de aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="e4f94-117">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="e4f94-118">Como: Definir configurações de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="e4f94-118">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
