---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 4dc425fa97eaf99664f0d9bbbbc851c462cbf373
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274957"
---
# <a name="services"></a><span data-ttu-id="f553f-101">\<services></span><span class="sxs-lookup"><span data-stu-id="f553f-101">\<services></span></span>
<span data-ttu-id="f553f-102">Os serviços são definidos na `services` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="f553f-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="f553f-103">Cada serviço tem seu próprio `service` seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="f553f-103">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="f553f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f553f-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f553f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f553f-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f553f-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f553f-106">Attributes and Elements</span></span>  
 <span data-ttu-id="f553f-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f553f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f553f-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="f553f-108">Attributes</span></span>  
 <span data-ttu-id="f553f-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f553f-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f553f-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f553f-110">Child Elements</span></span>  
  
|<span data-ttu-id="f553f-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="f553f-111">Element</span></span>|<span data-ttu-id="f553f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f553f-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f553f-113">\<service></span><span class="sxs-lookup"><span data-stu-id="f553f-113">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="f553f-114">Defina o contrato de serviço, o comportamento e os pontos de extremidade do serviço em questão.</span><span class="sxs-lookup"><span data-stu-id="f553f-114">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f553f-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f553f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f553f-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="f553f-116">Element</span></span>|<span data-ttu-id="f553f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="f553f-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f553f-118">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f553f-118">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="f553f-119">O elemento raiz de todos os elementos de configuração do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f553f-119">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f553f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f553f-120">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServicesSection>
