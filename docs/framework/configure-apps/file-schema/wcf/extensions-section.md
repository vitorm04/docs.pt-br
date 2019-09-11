---
title: <extensions>Section
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 35621acaf96a80ffa3ffe4a3c6605143c48995a5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855361"
---
# <a name="extensions-section"></a><span data-ttu-id="ca4cc-102">\<> seção de extensões</span><span class="sxs-lookup"><span data-stu-id="ca4cc-102">\<extensions> section</span></span>
<span data-ttu-id="ca4cc-103">Esta seção de configuração contém uma coleção de extensões, que permitem ao usuário criar associações definidas pelo usuário, comportamentos e outros aspectos de extensões.</span><span class="sxs-lookup"><span data-stu-id="ca4cc-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="ca4cc-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ca4cc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ca4cc-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ca4cc-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ca4cc-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<extensões >**</span><span class="sxs-lookup"><span data-stu-id="ca4cc-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<extensions>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca4cc-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca4cc-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca4cc-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ca4cc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ca4cc-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ca4cc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca4cc-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ca4cc-110">Attributes</span></span>  
 <span data-ttu-id="ca4cc-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ca4cc-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ca4cc-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ca4cc-112">Child Elements</span></span>  
  
|<span data-ttu-id="ca4cc-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="ca4cc-113">Element</span></span>|<span data-ttu-id="ca4cc-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca4cc-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca4cc-115">\<behaviorExtensions></span><span class="sxs-lookup"><span data-stu-id="ca4cc-115">\<behaviorExtensions></span></span>](behaviorextensions.md)|<span data-ttu-id="ca4cc-116">Esta seção contém elementos filho que especificam extensões de comportamento, que permitem ao usuário personalizar comportamentos de serviço ou ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ca4cc-116">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="ca4cc-117">\<bindingElementExtensions></span><span class="sxs-lookup"><span data-stu-id="ca4cc-117">\<bindingElementExtensions></span></span>](bindingelementextensions.md)|<span data-ttu-id="ca4cc-118">Esta seção habilita o uso de um elemento de associação personalizado de um computador ou arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ca4cc-118">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="ca4cc-119">\<bindingExtensions></span><span class="sxs-lookup"><span data-stu-id="ca4cc-119">\<bindingExtensions></span></span>](bindingextensions.md)|<span data-ttu-id="ca4cc-120">Esta seção contém elementos filho que especificam extensões de associação, que permitem ao usuário personalizar associações.</span><span class="sxs-lookup"><span data-stu-id="ca4cc-120">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="ca4cc-121">\<endpointExtensions></span><span class="sxs-lookup"><span data-stu-id="ca4cc-121">\<endpointExtensions></span></span>](endpointextensions.md)|<span data-ttu-id="ca4cc-122">Esta seção contém elementos filho que registram pontos de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="ca4cc-122">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca4cc-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ca4cc-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ca4cc-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="ca4cc-124">Element</span></span>|<span data-ttu-id="ca4cc-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca4cc-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca4cc-126">sistema.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ca4cc-126">system.ServiceModel</span></span>|<span data-ttu-id="ca4cc-127">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="ca4cc-127">The root element of all WCF configuration elements.</span></span>|
