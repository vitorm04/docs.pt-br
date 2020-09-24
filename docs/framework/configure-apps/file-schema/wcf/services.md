---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: b8cb5075ba41bed5a22b152a231c7213b326a62f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153710"
---
# \<services>

<span data-ttu-id="4fb39-101">Os serviços são definidos na `services` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="4fb39-101">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="4fb39-102">Cada serviço tem sua própria `service` seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="4fb39-102">Each service has its own `service` configuration section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**  
  
## <a name="syntax"></a><span data-ttu-id="4fb39-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="4fb39-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fb39-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4fb39-104">Attributes and Elements</span></span>  

 <span data-ttu-id="4fb39-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4fb39-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fb39-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="4fb39-106">Attributes</span></span>  

 <span data-ttu-id="4fb39-107">Nenhum</span><span class="sxs-lookup"><span data-stu-id="4fb39-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4fb39-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4fb39-108">Child Elements</span></span>  
  
|<span data-ttu-id="4fb39-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="4fb39-109">Element</span></span>|<span data-ttu-id="4fb39-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="4fb39-110">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="4fb39-111">Defina o contrato de serviço, o comportamento e os pontos de extremidade do serviço específico.</span><span class="sxs-lookup"><span data-stu-id="4fb39-111">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4fb39-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4fb39-112">Parent Elements</span></span>  
  
|<span data-ttu-id="4fb39-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="4fb39-113">Element</span></span>|<span data-ttu-id="4fb39-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="4fb39-114">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="4fb39-115">O elemento raiz de todos os elementos de configuração de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4fb39-115">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4fb39-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="4fb39-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
