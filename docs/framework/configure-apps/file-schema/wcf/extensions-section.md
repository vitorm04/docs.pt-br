---
title: <extensions>Section
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 35621acaf96a80ffa3ffe4a3c6605143c48995a5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855361"
---
# <a name="extensions-section"></a><span data-ttu-id="64537-102">\<extensions>Section</span><span class="sxs-lookup"><span data-stu-id="64537-102">\<extensions> section</span></span>
<span data-ttu-id="64537-103">Esta seção de configuração contém uma coleção de extensões, que permitem ao usuário criar associações definidas pelo usuário, comportamentos e outros aspectos de extensões.</span><span class="sxs-lookup"><span data-stu-id="64537-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<extensions>**  
  
## <a name="syntax"></a><span data-ttu-id="64537-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64537-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64537-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="64537-105">Attributes and Elements</span></span>  
 <span data-ttu-id="64537-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="64537-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64537-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="64537-107">Attributes</span></span>  
 <span data-ttu-id="64537-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="64537-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="64537-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="64537-109">Child Elements</span></span>  
  
|<span data-ttu-id="64537-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="64537-110">Element</span></span>|<span data-ttu-id="64537-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="64537-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviorExtensions>](behaviorextensions.md)|<span data-ttu-id="64537-112">Esta seção contém elementos filho que especificam extensões de comportamento, que permitem ao usuário personalizar comportamentos de serviço ou ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="64537-112">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[\<bindingElementExtensions>](bindingelementextensions.md)|<span data-ttu-id="64537-113">Esta seção habilita o uso de um elemento de associação personalizado de um computador ou arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="64537-113">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[\<bindingExtensions>](bindingextensions.md)|<span data-ttu-id="64537-114">Esta seção contém elementos filho que especificam extensões de associação, que permitem ao usuário personalizar associações.</span><span class="sxs-lookup"><span data-stu-id="64537-114">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[\<endpointExtensions>](endpointextensions.md)|<span data-ttu-id="64537-115">Esta seção contém elementos filho que registram pontos de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="64537-115">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="64537-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="64537-116">Parent Elements</span></span>  
  
|<span data-ttu-id="64537-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="64537-117">Element</span></span>|<span data-ttu-id="64537-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="64537-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="64537-119">sistema.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="64537-119">system.ServiceModel</span></span>|<span data-ttu-id="64537-120">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="64537-120">The root element of all WCF configuration elements.</span></span>|
