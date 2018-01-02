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
ms.workload: dotnet
ms.openlocfilehash: 786620b0daf1cd22a95f9d0c94b7fc3d17c1a2c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="88e0c-102">&lt;adicionar&gt; &lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="88e0c-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="88e0c-103">Representa um elemento de configuração que define um elemento de ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="88e0c-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="88e0c-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="88e0c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="88e0c-105">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="88e0c-105">\<routing></span></span>  
<span data-ttu-id="88e0c-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="88e0c-106">\<backupLists></span></span>  
<span data-ttu-id="88e0c-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="88e0c-107">\<backupList></span></span>  
<span data-ttu-id="88e0c-108">\<add></span><span class="sxs-lookup"><span data-stu-id="88e0c-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88e0c-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88e0c-109">Syntax</span></span>  
  
```xml  
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88e0c-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="88e0c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="88e0c-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="88e0c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88e0c-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="88e0c-112">Attributes</span></span>  
  
|<span data-ttu-id="88e0c-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="88e0c-113">Attribute</span></span>|<span data-ttu-id="88e0c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="88e0c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="88e0c-115">name</span><span class="sxs-lookup"><span data-stu-id="88e0c-115">name</span></span>|<span data-ttu-id="88e0c-116">Uma cadeia de caracteres que especifica o nome do ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="88e0c-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88e0c-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="88e0c-117">Child Elements</span></span>  
 <span data-ttu-id="88e0c-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="88e0c-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88e0c-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="88e0c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="88e0c-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="88e0c-120">Element</span></span>|<span data-ttu-id="88e0c-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="88e0c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88e0c-122">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="88e0c-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="88e0c-123">Contém uma lista de pontos de extremidade que você deseja que o serviço de roteamento para usar no caso do ponto de extremidade primário não pode ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="88e0c-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="88e0c-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88e0c-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
