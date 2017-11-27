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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1475983f7dc54a597198d48a2a404e431ce9c0a0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="01028-102">&lt;adicionar&gt; &lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="01028-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="01028-103">Representa um elemento de configuração que define um elemento de ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="01028-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="01028-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="01028-104">\<system.serviceModel></span></span>  
<span data-ttu-id="01028-105">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="01028-105">\<routing></span></span>  
<span data-ttu-id="01028-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="01028-106">\<backupLists></span></span>  
<span data-ttu-id="01028-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="01028-107">\<backupList></span></span>  
<span data-ttu-id="01028-108">\<add></span><span class="sxs-lookup"><span data-stu-id="01028-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01028-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="01028-109">Syntax</span></span>  
  
```xml  
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01028-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="01028-110">Attributes and Elements</span></span>  
 <span data-ttu-id="01028-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="01028-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01028-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="01028-112">Attributes</span></span>  
  
|<span data-ttu-id="01028-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="01028-113">Attribute</span></span>|<span data-ttu-id="01028-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="01028-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="01028-115">name</span><span class="sxs-lookup"><span data-stu-id="01028-115">name</span></span>|<span data-ttu-id="01028-116">Uma cadeia de caracteres que especifica o nome do ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="01028-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01028-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="01028-117">Child Elements</span></span>  
 <span data-ttu-id="01028-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="01028-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01028-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="01028-119">Parent Elements</span></span>  
  
|<span data-ttu-id="01028-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="01028-120">Element</span></span>|<span data-ttu-id="01028-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="01028-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01028-122">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="01028-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="01028-123">Contém uma lista de pontos de extremidade que você deseja que o serviço de roteamento para usar no caso do ponto de extremidade primário não pode ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="01028-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="01028-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01028-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
