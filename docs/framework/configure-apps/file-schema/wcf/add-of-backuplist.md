---
title: <add> de <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: c590dbd671807b32e08ad5d871d376a0dc51e611
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926870"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="cb7c5-102">\<Adicionar > de \<BackupList ></span><span class="sxs-lookup"><span data-stu-id="cb7c5-102">\<add> of \<backupList></span></span>
<span data-ttu-id="cb7c5-103">Representa um elemento de configuração que define um elemento de ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="cb7c5-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="cb7c5-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cb7c5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="cb7c5-105">\<> de roteamento</span><span class="sxs-lookup"><span data-stu-id="cb7c5-105">\<routing></span></span>  
<span data-ttu-id="cb7c5-106">\<> backupLists</span><span class="sxs-lookup"><span data-stu-id="cb7c5-106">\<backupLists></span></span>  
<span data-ttu-id="cb7c5-107">\<> de BackupList</span><span class="sxs-lookup"><span data-stu-id="cb7c5-107">\<backupList></span></span>  
<span data-ttu-id="cb7c5-108">\<add></span><span class="sxs-lookup"><span data-stu-id="cb7c5-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb7c5-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb7c5-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb7c5-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cb7c5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cb7c5-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cb7c5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb7c5-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="cb7c5-112">Attributes</span></span>  
  
|<span data-ttu-id="cb7c5-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="cb7c5-113">Attribute</span></span>|<span data-ttu-id="cb7c5-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb7c5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cb7c5-115">name</span><span class="sxs-lookup"><span data-stu-id="cb7c5-115">name</span></span>|<span data-ttu-id="cb7c5-116">Uma cadeia de caracteres que especifica o nome do ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="cb7c5-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb7c5-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cb7c5-117">Child Elements</span></span>  
 <span data-ttu-id="cb7c5-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="cb7c5-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb7c5-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cb7c5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="cb7c5-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="cb7c5-120">Element</span></span>|<span data-ttu-id="cb7c5-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb7c5-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb7c5-122">\<routing></span><span class="sxs-lookup"><span data-stu-id="cb7c5-122">\<routing></span></span>](routing.md)|<span data-ttu-id="cb7c5-123">Contém uma lista de pontos de extremidade que você deseja que o serviço de roteamento use caso o ponto de extremidade primário não possa ser acessado.</span><span class="sxs-lookup"><span data-stu-id="cb7c5-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cb7c5-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb7c5-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
