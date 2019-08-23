---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: b65cc4d04b5304e93b70509c9db3bc2248accb7f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926429"
---
# <a name="backuplists"></a><span data-ttu-id="26667-101">\<> backupLists</span><span class="sxs-lookup"><span data-stu-id="26667-101">\<backupLists></span></span>
<span data-ttu-id="26667-102">Representa uma seção de configuração para definir um conjunto de serviços de backup usados no tratamento de erros.</span><span class="sxs-lookup"><span data-stu-id="26667-102">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="26667-103">Cada elemento filho é uma lista de backup que enumera um conjunto de pontos de extremidade que você deseja que o serviço de roteamento use caso o ponto de extremidade primário não possa ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="26667-103">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="26667-104">Se o primeiro ponto de extremidade na lista estiver inativo, o serviço de roteamento fará failover automaticamente para o próximo da lista.</span><span class="sxs-lookup"><span data-stu-id="26667-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="26667-105">Isso lhe dá uma maneira rápida de adicionar confiabilidade ao seu aplicativo sem ter que ensinar o aplicativo cliente a lidar com padrões complexos ou onde todos os seus serviços são implantados.</span><span class="sxs-lookup"><span data-stu-id="26667-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="26667-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="26667-106">\<system.serviceModel></span></span>  
<span data-ttu-id="26667-107">\<> de roteamento</span><span class="sxs-lookup"><span data-stu-id="26667-107">\<routing></span></span>  
<span data-ttu-id="26667-108">\<> backupLists</span><span class="sxs-lookup"><span data-stu-id="26667-108">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26667-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26667-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26667-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="26667-110">Attributes and Elements</span></span>  
 <span data-ttu-id="26667-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="26667-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26667-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="26667-112">Attributes</span></span>  
 <span data-ttu-id="26667-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="26667-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="26667-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="26667-114">Child Elements</span></span>  
  
|<span data-ttu-id="26667-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="26667-115">Element</span></span>|<span data-ttu-id="26667-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="26667-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26667-117">\<filter></span><span class="sxs-lookup"><span data-stu-id="26667-117">\<filter></span></span>](filter.md)|<span data-ttu-id="26667-118">Contém uma lista de pontos de extremidade que você deseja que o serviço de roteamento use caso o ponto de extremidade primário não possa ser acessado.</span><span class="sxs-lookup"><span data-stu-id="26667-118">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="26667-119">.</span><span class="sxs-lookup"><span data-stu-id="26667-119">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="26667-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="26667-120">Parent Elements</span></span>  
  
|<span data-ttu-id="26667-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="26667-121">Element</span></span>|<span data-ttu-id="26667-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="26667-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26667-123">\<routing></span><span class="sxs-lookup"><span data-stu-id="26667-123">\<routing></span></span>](routing.md)|<span data-ttu-id="26667-124">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) a ser usado ao avaliar mensagens de entrada, bem como tabelas de roteamento que definem os pontos de extremidade de destino para enviar mensagens para quando um filtro corresponder.</span><span class="sxs-lookup"><span data-stu-id="26667-124">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="26667-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26667-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
