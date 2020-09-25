---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 940bf28958251e7257b2cc19a9c5ff0059411bcd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201545"
---
# \<backupLists>

<span data-ttu-id="4bd67-101">Representa uma seção de configuração para definir um conjunto de serviços de backup usados no tratamento de erros.</span><span class="sxs-lookup"><span data-stu-id="4bd67-101">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="4bd67-102">Cada elemento filho é uma lista de backup que enumera um conjunto de pontos de extremidade que você deseja que o serviço de roteamento use caso o ponto de extremidade primário não possa ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="4bd67-102">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="4bd67-103">Se o primeiro ponto de extremidade na lista estiver inativo, o serviço de roteamento fará failover automaticamente para o próximo da lista.</span><span class="sxs-lookup"><span data-stu-id="4bd67-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="4bd67-104">Isso lhe dá uma maneira rápida de adicionar confiabilidade ao seu aplicativo sem ter que ensinar o aplicativo cliente a lidar com padrões complexos ou onde todos os seus serviços são implantados.</span><span class="sxs-lookup"><span data-stu-id="4bd67-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupLists>**  
  
## <a name="syntax"></a><span data-ttu-id="4bd67-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4bd67-105">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4bd67-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4bd67-106">Attributes and Elements</span></span>  

 <span data-ttu-id="4bd67-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4bd67-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4bd67-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="4bd67-108">Attributes</span></span>  

 <span data-ttu-id="4bd67-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="4bd67-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4bd67-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4bd67-110">Child Elements</span></span>  
  
|<span data-ttu-id="4bd67-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="4bd67-111">Element</span></span>|<span data-ttu-id="4bd67-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="4bd67-112">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter.md)|<span data-ttu-id="4bd67-113">Contém uma lista de pontos de extremidade que você deseja que o serviço de roteamento use caso o ponto de extremidade primário não possa ser acessado.</span><span class="sxs-lookup"><span data-stu-id="4bd67-113">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="4bd67-114">.</span><span class="sxs-lookup"><span data-stu-id="4bd67-114">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4bd67-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4bd67-115">Parent Elements</span></span>  
  
|<span data-ttu-id="4bd67-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="4bd67-116">Element</span></span>|<span data-ttu-id="4bd67-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="4bd67-117">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="4bd67-118">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usado ao avaliar mensagens de entrada, bem como tabelas de roteamento que definem os pontos de extremidade de destino para envio de mensagens quando um filtro é correspondente.</span><span class="sxs-lookup"><span data-stu-id="4bd67-118">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4bd67-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="4bd67-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
