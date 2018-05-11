---
title: '&lt;backupLists&gt;'
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 5fb89ce5a942db40b07a65f59ddd05ab4cd624aa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltbackuplistsgt"></a><span data-ttu-id="a6018-102">&lt;backupLists&gt;</span><span class="sxs-lookup"><span data-stu-id="a6018-102">&lt;backupLists&gt;</span></span>
<span data-ttu-id="a6018-103">Representa uma seção de configuração para definir um conjunto de serviços de backup usado na manipulação de erro.</span><span class="sxs-lookup"><span data-stu-id="a6018-103">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="a6018-104">Cada elemento filho é uma lista de backup que enumera um conjunto de pontos de extremidade que você deseja que o serviço de roteamento para usar no caso do ponto de extremidade primário não pode ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="a6018-104">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="a6018-105">Se o primeiro ponto de extremidade na lista estiver inativo, o serviço de roteamento irá automaticamente failover para o próximo na lista.</span><span class="sxs-lookup"><span data-stu-id="a6018-105">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="a6018-106">Isso fornece uma maneira rápida de adicionar confiabilidade para seu aplicativo sem ter que ensinar seu aplicativo cliente como lidar com padrões complexos ou onde todos os serviços são implantados.</span><span class="sxs-lookup"><span data-stu-id="a6018-106">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="a6018-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a6018-107">\<system.serviceModel></span></span>  
<span data-ttu-id="a6018-108">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="a6018-108">\<routing></span></span>  
<span data-ttu-id="a6018-109">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="a6018-109">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6018-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6018-110">Syntax</span></span>  
  
```xml
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a6018-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a6018-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a6018-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a6018-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6018-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="a6018-113">Attributes</span></span>  
 <span data-ttu-id="a6018-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a6018-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a6018-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a6018-115">Child Elements</span></span>  
  
|<span data-ttu-id="a6018-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="a6018-116">Element</span></span>|<span data-ttu-id="a6018-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6018-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6018-118">\<filter></span><span class="sxs-lookup"><span data-stu-id="a6018-118">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="a6018-119">Contém uma lista de pontos de extremidade que você deseja que o serviço de roteamento para usar no caso do ponto de extremidade primário não pode ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="a6018-119">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="a6018-120">.</span><span class="sxs-lookup"><span data-stu-id="a6018-120">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a6018-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a6018-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a6018-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="a6018-122">Element</span></span>|<span data-ttu-id="a6018-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6018-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6018-124">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="a6018-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="a6018-125">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como o roteamento de tabelas que definem os pontos de extremidade de destino para envie mensagens para quando houver correspondência de filtro.</span><span class="sxs-lookup"><span data-stu-id="a6018-125">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6018-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6018-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
