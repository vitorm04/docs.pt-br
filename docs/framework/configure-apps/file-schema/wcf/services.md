---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 1f9cb6c95fa14a5b8a55cc561699e2a07e1dc80c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399590"
---
# <a name="services"></a><span data-ttu-id="57dca-101">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="57dca-101">\<services></span></span>
<span data-ttu-id="57dca-102">Os serviços são definidos na `services` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="57dca-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="57dca-103">Cada serviço tem sua própria `service` seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="57dca-103">Each service has its own `service` configuration section.</span></span>  
  
<span data-ttu-id="57dca-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="57dca-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="57dca-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="57dca-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="57dca-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Serviços >**</span><span class="sxs-lookup"><span data-stu-id="57dca-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**</span></span>  
## <a name="syntax"></a><span data-ttu-id="57dca-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57dca-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57dca-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="57dca-108">Attributes and Elements</span></span>  
 <span data-ttu-id="57dca-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="57dca-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57dca-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="57dca-110">Attributes</span></span>  
 <span data-ttu-id="57dca-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="57dca-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="57dca-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="57dca-112">Child Elements</span></span>  
  
|<span data-ttu-id="57dca-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="57dca-113">Element</span></span>|<span data-ttu-id="57dca-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="57dca-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57dca-115">\<service></span><span class="sxs-lookup"><span data-stu-id="57dca-115">\<service></span></span>](service.md)|<span data-ttu-id="57dca-116">Defina o contrato de serviço, o comportamento e os pontos de extremidade do serviço específico.</span><span class="sxs-lookup"><span data-stu-id="57dca-116">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57dca-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="57dca-117">Parent Elements</span></span>  
  
|<span data-ttu-id="57dca-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="57dca-118">Element</span></span>|<span data-ttu-id="57dca-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="57dca-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57dca-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="57dca-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="57dca-121">O elemento raiz de todos os elementos de configuração de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="57dca-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57dca-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57dca-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
