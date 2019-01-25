---
title: '&lt;adicionar&gt; &lt;backupList&gt;'
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 2cc7cce62082317bb86218d68bd2881b74649771
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670180"
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="843d5-102">&lt;adicionar&gt; &lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="843d5-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="843d5-103">Representa um elemento de configuração que define um elemento de ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="843d5-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="843d5-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="843d5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="843d5-105">\<routing></span><span class="sxs-lookup"><span data-stu-id="843d5-105">\<routing></span></span>  
<span data-ttu-id="843d5-106">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="843d5-106">\<backupLists></span></span>  
<span data-ttu-id="843d5-107">\<backupList></span><span class="sxs-lookup"><span data-stu-id="843d5-107">\<backupList></span></span>  
<span data-ttu-id="843d5-108">\<add></span><span class="sxs-lookup"><span data-stu-id="843d5-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="843d5-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="843d5-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="843d5-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="843d5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="843d5-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="843d5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="843d5-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="843d5-112">Attributes</span></span>  
  
|<span data-ttu-id="843d5-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="843d5-113">Attribute</span></span>|<span data-ttu-id="843d5-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="843d5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="843d5-115">name</span><span class="sxs-lookup"><span data-stu-id="843d5-115">name</span></span>|<span data-ttu-id="843d5-116">Uma cadeia de caracteres que especifica o nome do ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="843d5-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="843d5-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="843d5-117">Child Elements</span></span>  
 <span data-ttu-id="843d5-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="843d5-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="843d5-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="843d5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="843d5-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="843d5-120">Element</span></span>|<span data-ttu-id="843d5-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="843d5-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="843d5-122">\<routing></span><span class="sxs-lookup"><span data-stu-id="843d5-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="843d5-123">Contém uma lista de pontos de extremidade que você gostaria que o serviço de roteamento use caso o ponto de extremidade primário não pode ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="843d5-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="843d5-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="843d5-124">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
