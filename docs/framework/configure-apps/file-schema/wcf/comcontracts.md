---
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: d061d48374a8745dc61e1ca156e4fcbbccee5ef7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69919482"
---
# \<comContracts>
<span data-ttu-id="f4efe-101">A `comContracts` seção de configuração contém elementos que permitem especificar várias propriedades de um contrato de serviço de integração com+.</span><span class="sxs-lookup"><span data-stu-id="f4efe-101">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="f4efe-102">Especificando o namespace e o contrato</span><span class="sxs-lookup"><span data-stu-id="f4efe-102">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="f4efe-103">Os contratos do serviço de integração COM+ estão atualmente restritos ao `http://tempuri.org` namespace e o nome do contrato é derivado da interface com de suporte.</span><span class="sxs-lookup"><span data-stu-id="f4efe-103">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="f4efe-104">No entanto, você pode especificar alternativas usando a `comContracts` seção no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="f4efe-104">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="f4efe-105">Por exemplo, você pode usar a configuração a seguir para especificar o namespace e o nome do contrato do contrato de serviço, bem como uma opção para impor o uso em associações de sessão.</span><span class="sxs-lookup"><span data-stu-id="f4efe-105">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="f4efe-106">Quando o serviço é inicializado, os namespaces e os nomes de contrato especificados são aplicados às descrições de serviço geradas.</span><span class="sxs-lookup"><span data-stu-id="f4efe-106">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="f4efe-107">Quando esta seção estiver vazia, a inicialização do serviço aplicará um namespace padrão e o nome do contrato extraído da ID de interface COM de suporte.</span><span class="sxs-lookup"><span data-stu-id="f4efe-107">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="f4efe-108">Além disso, você pode usar o [\<exposedMethod>](exposedmethod.md) elemento para especificar métodos com+ que são expostos quando a interface em um componente com+ é exposta como um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="f4efe-108">In addition, you can use the [\<exposedMethod>](exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="f4efe-109">Você também pode usar o [\<persistableTypes>](persistabletypes.md) para especificar tipos persistentes usados na integração.</span><span class="sxs-lookup"><span data-stu-id="f4efe-109">You can also use the [\<persistableTypes>](persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="f4efe-110">Por fim, você pode usar o [\<userDefinedType>](userdefinedtype.md) elemento para incluir os UDT (tipos definidos pelo usuário) que devem ser incluídos no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="f4efe-110">Finally, you can use the [\<userDefinedType>](userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4efe-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="f4efe-111">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<exposedMethod>](exposedmethod.md)
- [\<persistableTypes>](persistabletypes.md)
- [\<userDefinedType>](userdefinedtype.md)
- [\<comContract>](comcontract.md)
- [<span data-ttu-id="f4efe-112">Integração com aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="f4efe-112">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="f4efe-113">Como configurar configurações de serviço de COM+</span><span class="sxs-lookup"><span data-stu-id="f4efe-113">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
