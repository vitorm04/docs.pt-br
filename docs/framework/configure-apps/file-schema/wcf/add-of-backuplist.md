---
title: <add> de <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 53af01a519c244376b262db1f6515a438dcc554f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663364"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="e64a9-102">\<Adicionar > de \<BackupList ></span><span class="sxs-lookup"><span data-stu-id="e64a9-102">\<add> of \<backupList></span></span>
<span data-ttu-id="e64a9-103">Representa um elemento de configuração que define um elemento de ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="e64a9-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="e64a9-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e64a9-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e64a9-105">\<> de roteamento</span><span class="sxs-lookup"><span data-stu-id="e64a9-105">\<routing></span></span>  
<span data-ttu-id="e64a9-106">\<> backupLists</span><span class="sxs-lookup"><span data-stu-id="e64a9-106">\<backupLists></span></span>  
<span data-ttu-id="e64a9-107">\<> de BackupList</span><span class="sxs-lookup"><span data-stu-id="e64a9-107">\<backupList></span></span>  
<span data-ttu-id="e64a9-108">\<add></span><span class="sxs-lookup"><span data-stu-id="e64a9-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e64a9-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e64a9-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e64a9-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e64a9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e64a9-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e64a9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e64a9-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="e64a9-112">Attributes</span></span>  
  
|<span data-ttu-id="e64a9-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="e64a9-113">Attribute</span></span>|<span data-ttu-id="e64a9-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e64a9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e64a9-115">name</span><span class="sxs-lookup"><span data-stu-id="e64a9-115">name</span></span>|<span data-ttu-id="e64a9-116">Uma cadeia de caracteres que especifica o nome do ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="e64a9-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e64a9-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e64a9-117">Child Elements</span></span>  
 <span data-ttu-id="e64a9-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e64a9-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e64a9-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e64a9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e64a9-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="e64a9-120">Element</span></span>|<span data-ttu-id="e64a9-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="e64a9-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e64a9-122">\<routing></span><span class="sxs-lookup"><span data-stu-id="e64a9-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="e64a9-123">Contém uma lista de pontos de extremidade que você deseja que o serviço de roteamento use caso o ponto de extremidade primário não possa ser acessado.</span><span class="sxs-lookup"><span data-stu-id="e64a9-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e64a9-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e64a9-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
