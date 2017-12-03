---
title: "seção de &lt;extensões&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06c8106f004a25f1e4547e9629b881e5bf216490
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltextensionsgt-section"></a><span data-ttu-id="3569f-102">seção de &lt;extensões&gt;</span><span class="sxs-lookup"><span data-stu-id="3569f-102">&lt;extensions&gt; section</span></span>
<span data-ttu-id="3569f-103">Esta seção de configuração contém uma coleção de extensões, que permitem que o usuário crie associações definidas pelo usuário, comportamentos e outros aspectos de extensões.</span><span class="sxs-lookup"><span data-stu-id="3569f-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="3569f-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="3569f-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3569f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3569f-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <extensions>  
    <bindingExtensions>  
    </bindingExtensions>  
    <behaviorExtensions>  
    </behaviorExtensions>  
    <bindingElementExtensions>  
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3569f-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3569f-106">Attributes and Elements</span></span>  
 <span data-ttu-id="3569f-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3569f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3569f-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="3569f-108">Attributes</span></span>  
 <span data-ttu-id="3569f-109">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3569f-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3569f-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3569f-110">Child Elements</span></span>  
  
|<span data-ttu-id="3569f-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="3569f-111">Element</span></span>|<span data-ttu-id="3569f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3569f-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3569f-113">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="3569f-113">\<behaviorExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|<span data-ttu-id="3569f-114">Esta seção contém os elementos filho que especificam extensões de comportamento, que permitem que o usuário personalize os comportamentos de serviço ou o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3569f-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="3569f-115">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="3569f-115">\<bindingElementExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|<span data-ttu-id="3569f-116">Esta seção permite o uso de um elemento de associação personalizada de um computador ou arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3569f-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="3569f-117">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="3569f-117">\<bindingExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|<span data-ttu-id="3569f-118">Esta seção contém os elementos filho que especificam extensões de associação, que permitem que o usuário personalize associações.</span><span class="sxs-lookup"><span data-stu-id="3569f-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="3569f-119">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="3569f-119">\<endpointExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|<span data-ttu-id="3569f-120">Esta seção contém os elementos filho que registra a pontos de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="3569f-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3569f-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3569f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3569f-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="3569f-122">Element</span></span>|<span data-ttu-id="3569f-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="3569f-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3569f-124">sistema.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3569f-124">system.ServiceModel</span></span>|<span data-ttu-id="3569f-125">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="3569f-125">The root element of all WCF configuration elements.</span></span>|
