---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 02d1d530f37f5082153c9aa6b9993fc4009917f5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854984"
---
# \<services>
<span data-ttu-id="41f45-101">Os serviços são definidos na `services` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="41f45-101">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="41f45-102">Cada serviço tem sua própria `service` seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="41f45-102">Each service has its own `service` configuration section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**  
  
## <a name="syntax"></a><span data-ttu-id="41f45-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41f45-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41f45-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="41f45-104">Attributes and Elements</span></span>  
 <span data-ttu-id="41f45-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="41f45-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41f45-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="41f45-106">Attributes</span></span>  
 <span data-ttu-id="41f45-107">Nenhum</span><span class="sxs-lookup"><span data-stu-id="41f45-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="41f45-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="41f45-108">Child Elements</span></span>  
  
|<span data-ttu-id="41f45-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="41f45-109">Element</span></span>|<span data-ttu-id="41f45-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="41f45-110">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="41f45-111">Defina o contrato de serviço, o comportamento e os pontos de extremidade do serviço específico.</span><span class="sxs-lookup"><span data-stu-id="41f45-111">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="41f45-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="41f45-112">Parent Elements</span></span>  
  
|<span data-ttu-id="41f45-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="41f45-113">Element</span></span>|<span data-ttu-id="41f45-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="41f45-114">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="41f45-115">O elemento raiz de todos os elementos de configuração de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="41f45-115">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41f45-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="41f45-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
