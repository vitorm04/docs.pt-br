---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 02d1d530f37f5082153c9aa6b9993fc4009917f5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854984"
---
# <a name="services"></a><span data-ttu-id="a45b0-101">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="a45b0-101">\<services></span></span>
<span data-ttu-id="a45b0-102">Os serviços são definidos na `services` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="a45b0-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="a45b0-103">Cada serviço tem sua própria `service` seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="a45b0-103">Each service has its own `service` configuration section.</span></span>  
  
<span data-ttu-id="a45b0-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a45b0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a45b0-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a45b0-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a45b0-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Serviços >**</span><span class="sxs-lookup"><span data-stu-id="a45b0-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a45b0-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a45b0-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a45b0-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a45b0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a45b0-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a45b0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a45b0-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="a45b0-110">Attributes</span></span>  
 <span data-ttu-id="a45b0-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a45b0-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a45b0-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a45b0-112">Child Elements</span></span>  
  
|<span data-ttu-id="a45b0-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="a45b0-113">Element</span></span>|<span data-ttu-id="a45b0-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a45b0-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a45b0-115">\<service></span><span class="sxs-lookup"><span data-stu-id="a45b0-115">\<service></span></span>](service.md)|<span data-ttu-id="a45b0-116">Defina o contrato de serviço, o comportamento e os pontos de extremidade do serviço específico.</span><span class="sxs-lookup"><span data-stu-id="a45b0-116">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a45b0-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a45b0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a45b0-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="a45b0-118">Element</span></span>|<span data-ttu-id="a45b0-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="a45b0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a45b0-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a45b0-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="a45b0-121">O elemento raiz de todos os elementos de configuração de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a45b0-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a45b0-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a45b0-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
