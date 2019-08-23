---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: c00d5fe3e8b2ba05843e09aca6aaa79386541bad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937196"
---
# <a name="services"></a><span data-ttu-id="6adef-101">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="6adef-101">\<services></span></span>
<span data-ttu-id="6adef-102">Os serviços são definidos na `services` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="6adef-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="6adef-103">Cada serviço tem sua própria `service` seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="6adef-103">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="6adef-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6adef-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6adef-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6adef-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6adef-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6adef-106">Attributes and Elements</span></span>  
 <span data-ttu-id="6adef-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6adef-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6adef-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="6adef-108">Attributes</span></span>  
 <span data-ttu-id="6adef-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="6adef-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6adef-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6adef-110">Child Elements</span></span>  
  
|<span data-ttu-id="6adef-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="6adef-111">Element</span></span>|<span data-ttu-id="6adef-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="6adef-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6adef-113">\<service></span><span class="sxs-lookup"><span data-stu-id="6adef-113">\<service></span></span>](service.md)|<span data-ttu-id="6adef-114">Defina o contrato de serviço, o comportamento e os pontos de extremidade do serviço específico.</span><span class="sxs-lookup"><span data-stu-id="6adef-114">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6adef-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6adef-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6adef-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="6adef-116">Element</span></span>|<span data-ttu-id="6adef-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="6adef-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6adef-118">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6adef-118">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="6adef-119">O elemento raiz de todos os elementos de configuração de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6adef-119">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6adef-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6adef-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
