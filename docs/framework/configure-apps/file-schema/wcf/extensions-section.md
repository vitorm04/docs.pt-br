---
title: <extensions> Seção
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 0f77f621bbf9bbef00b206ef43a174f6f69364d5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268282"
---
# <a name="extensions-section"></a><span data-ttu-id="4069a-102">\<Extensões > seção</span><span class="sxs-lookup"><span data-stu-id="4069a-102">\<extensions> section</span></span>
<span data-ttu-id="4069a-103">Esta seção de configuração contém uma coleção de extensões, que permitem que o usuário crie associações definidas pelo usuário, comportamentos e outros aspectos de extensões.</span><span class="sxs-lookup"><span data-stu-id="4069a-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="4069a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4069a-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4069a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4069a-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4069a-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4069a-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4069a-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4069a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4069a-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="4069a-108">Attributes</span></span>  
 <span data-ttu-id="4069a-109">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4069a-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4069a-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4069a-110">Child Elements</span></span>  
  
|<span data-ttu-id="4069a-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="4069a-111">Element</span></span>|<span data-ttu-id="4069a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="4069a-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4069a-113">\<behaviorExtensions></span><span class="sxs-lookup"><span data-stu-id="4069a-113">\<behaviorExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|<span data-ttu-id="4069a-114">Esta seção contém os elementos filho que especificam extensões de comportamento, que permitem ao usuário personalizar os comportamentos de serviço ou ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="4069a-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="4069a-115">\<bindingElementExtensions></span><span class="sxs-lookup"><span data-stu-id="4069a-115">\<bindingElementExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|<span data-ttu-id="4069a-116">Esta seção permite o uso de um elemento de associação personalizada de um computador ou arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4069a-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="4069a-117">\<bindingExtensions></span><span class="sxs-lookup"><span data-stu-id="4069a-117">\<bindingExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|<span data-ttu-id="4069a-118">Esta seção contém os elementos filho que especificam extensões de associação, que permitem ao usuário personalizar as associações.</span><span class="sxs-lookup"><span data-stu-id="4069a-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="4069a-119">\<endpointExtensions></span><span class="sxs-lookup"><span data-stu-id="4069a-119">\<endpointExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|<span data-ttu-id="4069a-120">Esta seção contém os elementos filho que registra os pontos de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="4069a-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4069a-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4069a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4069a-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="4069a-122">Element</span></span>|<span data-ttu-id="4069a-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="4069a-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4069a-124">sistema.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4069a-124">system.ServiceModel</span></span>|<span data-ttu-id="4069a-125">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="4069a-125">The root element of all WCF configuration elements.</span></span>|
