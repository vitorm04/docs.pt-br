---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 6ac7ff19c76097cb54e7b77db21cad50b49513c0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55280742"
---
# <a name="backuplists"></a><span data-ttu-id="b4b2e-101">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="b4b2e-101">\<backupLists></span></span>
<span data-ttu-id="b4b2e-102">Representa uma seção de configuração para definir um conjunto de serviços de backup usado no tratamento de erros.</span><span class="sxs-lookup"><span data-stu-id="b4b2e-102">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="b4b2e-103">Cada elemento filho é uma lista de backup que enumera um conjunto de pontos de extremidade que você gostaria que o serviço de roteamento use caso o ponto de extremidade primário não pode ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="b4b2e-103">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="b4b2e-104">Se o primeiro ponto de extremidade na lista estiver inativo, o serviço de roteamento irá automaticamente failover para o próximo na lista.</span><span class="sxs-lookup"><span data-stu-id="b4b2e-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="b4b2e-105">Isso lhe dá uma maneira rápida de adicionar confiabilidade para seu aplicativo sem ter que ensinar o aplicativo cliente como lidar com padrões complexos ou onde todos os seus serviços são implantados.</span><span class="sxs-lookup"><span data-stu-id="b4b2e-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="b4b2e-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b4b2e-106">\<system.serviceModel></span></span>  
<span data-ttu-id="b4b2e-107">\<routing></span><span class="sxs-lookup"><span data-stu-id="b4b2e-107">\<routing></span></span>  
<span data-ttu-id="b4b2e-108">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="b4b2e-108">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4b2e-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4b2e-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4b2e-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b4b2e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b4b2e-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b4b2e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4b2e-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="b4b2e-112">Attributes</span></span>  
 <span data-ttu-id="b4b2e-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b4b2e-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b4b2e-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b4b2e-114">Child Elements</span></span>  
  
|<span data-ttu-id="b4b2e-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="b4b2e-115">Element</span></span>|<span data-ttu-id="b4b2e-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4b2e-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4b2e-117">\<filter></span><span class="sxs-lookup"><span data-stu-id="b4b2e-117">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="b4b2e-118">Contém uma lista de pontos de extremidade que você gostaria que o serviço de roteamento use caso o ponto de extremidade primário não pode ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="b4b2e-118">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="b4b2e-119">.</span><span class="sxs-lookup"><span data-stu-id="b4b2e-119">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b4b2e-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b4b2e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b4b2e-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="b4b2e-121">Element</span></span>|<span data-ttu-id="b4b2e-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4b2e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4b2e-123">\<routing></span><span class="sxs-lookup"><span data-stu-id="b4b2e-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="b4b2e-124">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como roteamento de tabelas que definem os pontos de extremidade de destino para envie mensagens para quando um filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="b4b2e-124">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b4b2e-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4b2e-125">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
