---
title: <extensions>Section
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 4c8b5fe6eef1863ee3f02cb761a3aac61406e446
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918963"
---
# <a name="extensions-section"></a><span data-ttu-id="22632-102">\<> seção de extensões</span><span class="sxs-lookup"><span data-stu-id="22632-102">\<extensions> section</span></span>
<span data-ttu-id="22632-103">Esta seção de configuração contém uma coleção de extensões, que permitem ao usuário criar associações definidas pelo usuário, comportamentos e outros aspectos de extensões.</span><span class="sxs-lookup"><span data-stu-id="22632-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="22632-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="22632-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22632-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22632-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22632-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="22632-106">Attributes and Elements</span></span>  
 <span data-ttu-id="22632-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="22632-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22632-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="22632-108">Attributes</span></span>  
 <span data-ttu-id="22632-109">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="22632-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="22632-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="22632-110">Child Elements</span></span>  
  
|<span data-ttu-id="22632-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="22632-111">Element</span></span>|<span data-ttu-id="22632-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="22632-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22632-113">\<behaviorExtensions></span><span class="sxs-lookup"><span data-stu-id="22632-113">\<behaviorExtensions></span></span>](behaviorextensions.md)|<span data-ttu-id="22632-114">Esta seção contém elementos filho que especificam extensões de comportamento, que permitem ao usuário personalizar comportamentos de serviço ou ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="22632-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="22632-115">\<bindingElementExtensions></span><span class="sxs-lookup"><span data-stu-id="22632-115">\<bindingElementExtensions></span></span>](bindingelementextensions.md)|<span data-ttu-id="22632-116">Esta seção habilita o uso de um elemento de associação personalizado de um computador ou arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="22632-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="22632-117">\<bindingExtensions></span><span class="sxs-lookup"><span data-stu-id="22632-117">\<bindingExtensions></span></span>](bindingextensions.md)|<span data-ttu-id="22632-118">Esta seção contém elementos filho que especificam extensões de associação, que permitem ao usuário personalizar associações.</span><span class="sxs-lookup"><span data-stu-id="22632-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="22632-119">\<endpointExtensions></span><span class="sxs-lookup"><span data-stu-id="22632-119">\<endpointExtensions></span></span>](endpointextensions.md)|<span data-ttu-id="22632-120">Esta seção contém elementos filho que registram pontos de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="22632-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="22632-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="22632-121">Parent Elements</span></span>  
  
|<span data-ttu-id="22632-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="22632-122">Element</span></span>|<span data-ttu-id="22632-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="22632-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="22632-124">sistema.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="22632-124">system.ServiceModel</span></span>|<span data-ttu-id="22632-125">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="22632-125">The root element of all WCF configuration elements.</span></span>|
