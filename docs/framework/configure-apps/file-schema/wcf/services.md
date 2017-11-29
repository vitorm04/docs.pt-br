---
title: "&lt;serviços&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: eb292a62c2b042c387799164ff4cec88bd2ca482
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltservicesgt"></a><span data-ttu-id="c0496-102">&lt;serviços&gt;</span><span class="sxs-lookup"><span data-stu-id="c0496-102">&lt;services&gt;</span></span>
<span data-ttu-id="c0496-103">Os serviços são definidos no `services` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0496-103">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="c0496-104">Cada serviço tem seu próprio `service` seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0496-104">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="c0496-105">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c0496-105">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0496-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0496-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0496-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c0496-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c0496-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c0496-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0496-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="c0496-109">Attributes</span></span>  
 <span data-ttu-id="c0496-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c0496-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c0496-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c0496-111">Child Elements</span></span>  
  
|<span data-ttu-id="c0496-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="c0496-112">Element</span></span>|<span data-ttu-id="c0496-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0496-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0496-114">\<serviço ></span><span class="sxs-lookup"><span data-stu-id="c0496-114">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="c0496-115">Defina o contrato de serviço, o comportamento e os pontos de extremidade do serviço em questão.</span><span class="sxs-lookup"><span data-stu-id="c0496-115">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c0496-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c0496-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c0496-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="c0496-117">Element</span></span>|<span data-ttu-id="c0496-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0496-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0496-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c0496-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="c0496-120">O elemento raiz de todos os elementos de configuração do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c0496-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0496-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0496-121">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServicesSection>
