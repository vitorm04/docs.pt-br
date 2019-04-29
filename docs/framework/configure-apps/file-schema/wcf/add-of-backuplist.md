---
title: <add> de <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 03bf1bbb8156e4722d987e171d9034747ac6bb61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701197"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="7421e-102">\<Adicionar > de \<backupList ></span><span class="sxs-lookup"><span data-stu-id="7421e-102">\<add> of \<backupList></span></span>
<span data-ttu-id="7421e-103">Representa um elemento de configuração que define um elemento de ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="7421e-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="7421e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7421e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7421e-105">\<routing></span><span class="sxs-lookup"><span data-stu-id="7421e-105">\<routing></span></span>  
<span data-ttu-id="7421e-106">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="7421e-106">\<backupLists></span></span>  
<span data-ttu-id="7421e-107">\<backupList></span><span class="sxs-lookup"><span data-stu-id="7421e-107">\<backupList></span></span>  
<span data-ttu-id="7421e-108">\<add></span><span class="sxs-lookup"><span data-stu-id="7421e-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7421e-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7421e-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7421e-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7421e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7421e-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7421e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7421e-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="7421e-112">Attributes</span></span>  
  
|<span data-ttu-id="7421e-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="7421e-113">Attribute</span></span>|<span data-ttu-id="7421e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="7421e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7421e-115">name</span><span class="sxs-lookup"><span data-stu-id="7421e-115">name</span></span>|<span data-ttu-id="7421e-116">Uma cadeia de caracteres que especifica o nome do ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="7421e-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7421e-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7421e-117">Child Elements</span></span>  
 <span data-ttu-id="7421e-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7421e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7421e-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7421e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7421e-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="7421e-120">Element</span></span>|<span data-ttu-id="7421e-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="7421e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7421e-122">\<routing></span><span class="sxs-lookup"><span data-stu-id="7421e-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="7421e-123">Contém uma lista de pontos de extremidade que você gostaria que o serviço de roteamento use caso o ponto de extremidade primário não pode ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="7421e-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7421e-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7421e-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
