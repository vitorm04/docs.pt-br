---
title: '&lt;adicionar&gt; &lt;backupList&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b93b442d21d34eea5031cea565bdcf62139abc81
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="16b6d-102">&lt;adicionar&gt; &lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="16b6d-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="16b6d-103">Representa um elemento de configuração que define um elemento de ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="16b6d-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="16b6d-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="16b6d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="16b6d-105">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="16b6d-105">\<routing></span></span>  
<span data-ttu-id="16b6d-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="16b6d-106">\<backupLists></span></span>  
<span data-ttu-id="16b6d-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="16b6d-107">\<backupList></span></span>  
<span data-ttu-id="16b6d-108">\<add></span><span class="sxs-lookup"><span data-stu-id="16b6d-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16b6d-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16b6d-109">Syntax</span></span>  
  
```xml  
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16b6d-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="16b6d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="16b6d-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="16b6d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16b6d-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="16b6d-112">Attributes</span></span>  
  
|<span data-ttu-id="16b6d-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="16b6d-113">Attribute</span></span>|<span data-ttu-id="16b6d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="16b6d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="16b6d-115">name</span><span class="sxs-lookup"><span data-stu-id="16b6d-115">name</span></span>|<span data-ttu-id="16b6d-116">Uma cadeia de caracteres que especifica o nome do ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="16b6d-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16b6d-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="16b6d-117">Child Elements</span></span>  
 <span data-ttu-id="16b6d-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="16b6d-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16b6d-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="16b6d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="16b6d-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="16b6d-120">Element</span></span>|<span data-ttu-id="16b6d-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="16b6d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16b6d-122">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="16b6d-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="16b6d-123">Contém uma lista de pontos de extremidade que você deseja que o serviço de roteamento para usar no caso do ponto de extremidade primário não pode ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="16b6d-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="16b6d-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16b6d-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
