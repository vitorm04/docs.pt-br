---
title: '&lt;backupLists&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 437cb1320147d5d76a4df9c3a00b4ee27bf650b0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbackuplistsgt"></a><span data-ttu-id="203ac-102">&lt;backupLists&gt;</span><span class="sxs-lookup"><span data-stu-id="203ac-102">&lt;backupLists&gt;</span></span>
<span data-ttu-id="203ac-103">Representa uma seção de configuração para definir um conjunto de serviços de backup usado na manipulação de erro.</span><span class="sxs-lookup"><span data-stu-id="203ac-103">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="203ac-104">Cada elemento filho é uma lista de backup que enumera um conjunto de pontos de extremidade que você deseja que o serviço de roteamento para usar no caso do ponto de extremidade primário não pode ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="203ac-104">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="203ac-105">Se o primeiro ponto de extremidade na lista estiver inativo, o serviço de roteamento irá automaticamente failover para o próximo na lista.</span><span class="sxs-lookup"><span data-stu-id="203ac-105">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="203ac-106">Isso fornece uma maneira rápida de adicionar confiabilidade para seu aplicativo sem ter que ensinar seu aplicativo cliente como lidar com padrões complexos ou onde todos os serviços são implantados.</span><span class="sxs-lookup"><span data-stu-id="203ac-106">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="203ac-107">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="203ac-107">\<system.serviceModel></span></span>  
<span data-ttu-id="203ac-108">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="203ac-108">\<routing></span></span>  
<span data-ttu-id="203ac-109">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="203ac-109">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="203ac-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="203ac-110">Syntax</span></span>  
  
```xml
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="203ac-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="203ac-111">Attributes and Elements</span></span>  
 <span data-ttu-id="203ac-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="203ac-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="203ac-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="203ac-113">Attributes</span></span>  
 <span data-ttu-id="203ac-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="203ac-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="203ac-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="203ac-115">Child Elements</span></span>  
  
|<span data-ttu-id="203ac-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="203ac-116">Element</span></span>|<span data-ttu-id="203ac-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="203ac-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="203ac-118">\<filter></span><span class="sxs-lookup"><span data-stu-id="203ac-118">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="203ac-119">Contém uma lista de pontos de extremidade que você deseja que o serviço de roteamento para usar no caso do ponto de extremidade primário não pode ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="203ac-119">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="203ac-120">.</span><span class="sxs-lookup"><span data-stu-id="203ac-120">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="203ac-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="203ac-121">Parent Elements</span></span>  
  
|<span data-ttu-id="203ac-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="203ac-122">Element</span></span>|<span data-ttu-id="203ac-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="203ac-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="203ac-124">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="203ac-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="203ac-125">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como o roteamento de tabelas que definem os pontos de extremidade de destino para enviar mensagens quando um corresponde ao filtro.</span><span class="sxs-lookup"><span data-stu-id="203ac-125">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="203ac-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="203ac-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
