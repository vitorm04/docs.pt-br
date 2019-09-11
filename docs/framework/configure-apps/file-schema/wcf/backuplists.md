---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 5f2bb030d13389e15cb44f1ddff3b8168b4f2140
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850263"
---
# <a name="backuplists"></a><span data-ttu-id="edc58-101">\<> backupLists</span><span class="sxs-lookup"><span data-stu-id="edc58-101">\<backupLists></span></span>
<span data-ttu-id="edc58-102">Representa uma seção de configuração para definir um conjunto de serviços de backup usados no tratamento de erros.</span><span class="sxs-lookup"><span data-stu-id="edc58-102">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="edc58-103">Cada elemento filho é uma lista de backup que enumera um conjunto de pontos de extremidade que você deseja que o serviço de roteamento use caso o ponto de extremidade primário não possa ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="edc58-103">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="edc58-104">Se o primeiro ponto de extremidade na lista estiver inativo, o serviço de roteamento fará failover automaticamente para o próximo da lista.</span><span class="sxs-lookup"><span data-stu-id="edc58-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="edc58-105">Isso lhe dá uma maneira rápida de adicionar confiabilidade ao seu aplicativo sem ter que ensinar o aplicativo cliente a lidar com padrões complexos ou onde todos os seus serviços são implantados.</span><span class="sxs-lookup"><span data-stu-id="edc58-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
<span data-ttu-id="edc58-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="edc58-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="edc58-107">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="edc58-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="edc58-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de roteamento**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="edc58-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="edc58-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> backupLists**</span><span class="sxs-lookup"><span data-stu-id="edc58-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupLists>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edc58-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="edc58-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="edc58-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="edc58-111">Attributes and Elements</span></span>  
 <span data-ttu-id="edc58-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="edc58-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="edc58-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="edc58-113">Attributes</span></span>  
 <span data-ttu-id="edc58-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="edc58-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="edc58-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="edc58-115">Child Elements</span></span>  
  
|<span data-ttu-id="edc58-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="edc58-116">Element</span></span>|<span data-ttu-id="edc58-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="edc58-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="edc58-118">\<filter></span><span class="sxs-lookup"><span data-stu-id="edc58-118">\<filter></span></span>](filter.md)|<span data-ttu-id="edc58-119">Contém uma lista de pontos de extremidade que você deseja que o serviço de roteamento use caso o ponto de extremidade primário não possa ser acessado.</span><span class="sxs-lookup"><span data-stu-id="edc58-119">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="edc58-120">.</span><span class="sxs-lookup"><span data-stu-id="edc58-120">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="edc58-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="edc58-121">Parent Elements</span></span>  
  
|<span data-ttu-id="edc58-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="edc58-122">Element</span></span>|<span data-ttu-id="edc58-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="edc58-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="edc58-124">\<routing></span><span class="sxs-lookup"><span data-stu-id="edc58-124">\<routing></span></span>](routing.md)|<span data-ttu-id="edc58-125">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) a ser usado ao avaliar mensagens de entrada, bem como tabelas de roteamento que definem os pontos de extremidade de destino para enviar mensagens para quando um filtro corresponder.</span><span class="sxs-lookup"><span data-stu-id="edc58-125">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="edc58-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="edc58-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
