---
title: '&lt;adicionar&gt; &lt;backupList&gt;'
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 4a8eb3df9be6b6b5bfe43aee330f3174ddca66ab
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151469"
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="721c3-102">&lt;adicionar&gt; &lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="721c3-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="721c3-103">Representa um elemento de configuração que define um elemento de ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="721c3-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="721c3-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="721c3-104">\<system.serviceModel></span></span>  
<span data-ttu-id="721c3-105">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="721c3-105">\<routing></span></span>  
<span data-ttu-id="721c3-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="721c3-106">\<backupLists></span></span>  
<span data-ttu-id="721c3-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="721c3-107">\<backupList></span></span>  
<span data-ttu-id="721c3-108">\<add></span><span class="sxs-lookup"><span data-stu-id="721c3-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="721c3-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="721c3-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="721c3-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="721c3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="721c3-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="721c3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="721c3-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="721c3-112">Attributes</span></span>  
  
|<span data-ttu-id="721c3-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="721c3-113">Attribute</span></span>|<span data-ttu-id="721c3-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="721c3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="721c3-115">name</span><span class="sxs-lookup"><span data-stu-id="721c3-115">name</span></span>|<span data-ttu-id="721c3-116">Uma cadeia de caracteres que especifica o nome do ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="721c3-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="721c3-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="721c3-117">Child Elements</span></span>  
 <span data-ttu-id="721c3-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="721c3-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="721c3-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="721c3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="721c3-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="721c3-120">Element</span></span>|<span data-ttu-id="721c3-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="721c3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="721c3-122">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="721c3-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="721c3-123">Contém uma lista de pontos de extremidade que você gostaria que o serviço de roteamento use caso o ponto de extremidade primário não pode ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="721c3-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="721c3-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="721c3-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
