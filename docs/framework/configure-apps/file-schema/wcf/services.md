---
title: '&lt;Serviços&gt;'
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 789fc52f628174ef61a9c7169cb0cae0f1ba8e31
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749225"
---
# <a name="ltservicesgt"></a><span data-ttu-id="7dc66-102">&lt;Serviços&gt;</span><span class="sxs-lookup"><span data-stu-id="7dc66-102">&lt;services&gt;</span></span>
<span data-ttu-id="7dc66-103">Os serviços são definidos no `services` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="7dc66-103">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="7dc66-104">Cada serviço tem seu próprio `service` seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="7dc66-104">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="7dc66-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7dc66-105">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dc66-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7dc66-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7dc66-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7dc66-107">Attributes and Elements</span></span>  
 <span data-ttu-id="7dc66-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7dc66-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7dc66-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="7dc66-109">Attributes</span></span>  
 <span data-ttu-id="7dc66-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7dc66-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7dc66-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7dc66-111">Child Elements</span></span>  
  
|<span data-ttu-id="7dc66-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="7dc66-112">Element</span></span>|<span data-ttu-id="7dc66-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="7dc66-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7dc66-114">\<service></span><span class="sxs-lookup"><span data-stu-id="7dc66-114">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="7dc66-115">Defina o contrato de serviço, o comportamento e os pontos de extremidade do serviço em questão.</span><span class="sxs-lookup"><span data-stu-id="7dc66-115">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7dc66-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7dc66-116">Parent Elements</span></span>  
  
|<span data-ttu-id="7dc66-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="7dc66-117">Element</span></span>|<span data-ttu-id="7dc66-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="7dc66-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7dc66-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7dc66-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="7dc66-120">O elemento raiz de todos os elementos de configuração do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7dc66-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7dc66-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7dc66-121">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServicesSection>
