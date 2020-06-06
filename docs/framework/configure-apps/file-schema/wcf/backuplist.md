---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 478211755b9131c03b72777ee95ff7223b9092c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850279"
---
# \<backupList>
<span data-ttu-id="70e85-101">Representa uma seção de configuração para definir uma lista de backup que enumera um conjunto de pontos de extremidade que você deseja que o serviço de roteamento use caso o ponto de extremidade primário não possa ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="70e85-101">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="70e85-102">Se o primeiro ponto de extremidade na lista estiver inativo, o serviço de roteamento fará failover automaticamente para o próximo da lista.</span><span class="sxs-lookup"><span data-stu-id="70e85-102">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="70e85-103">Isso lhe dá uma maneira rápida de adicionar confiabilidade ao seu aplicativo sem ter que ensinar o aplicativo cliente a lidar com padrões complexos ou onde todos os seus serviços são implantados.</span><span class="sxs-lookup"><span data-stu-id="70e85-103">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupList>**  
  
## <a name="syntax"></a><span data-ttu-id="70e85-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70e85-104">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70e85-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="70e85-105">Attributes and Elements</span></span>  
 <span data-ttu-id="70e85-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="70e85-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70e85-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="70e85-107">Attributes</span></span>  
  
|<span data-ttu-id="70e85-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="70e85-108">Attribute</span></span>|<span data-ttu-id="70e85-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="70e85-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="70e85-110">name</span><span class="sxs-lookup"><span data-stu-id="70e85-110">name</span></span>|<span data-ttu-id="70e85-111">Uma cadeia de caracteres que especifica o nome usado para identificar esta lista de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="70e85-111">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70e85-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="70e85-112">Child Elements</span></span>  
  
|<span data-ttu-id="70e85-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="70e85-113">Element</span></span>|<span data-ttu-id="70e85-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="70e85-114">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="70e85-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="70e85-115">Parent Elements</span></span>  
  
|<span data-ttu-id="70e85-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="70e85-116">Element</span></span>|<span data-ttu-id="70e85-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="70e85-117">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="70e85-118">Uma lista de pontos de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="70e85-118">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70e85-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="70e85-119">Remarks</span></span>  
 <span data-ttu-id="70e85-120">Esta seção contém uma coleção ordenada de pontos de extremidade para os quais uma mensagem será transmitida no caso de uma exceção de comunicação ao enviar para o ponto de extremidade primário.</span><span class="sxs-lookup"><span data-stu-id="70e85-120">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="70e85-121">Se um envio para o ponto de extremidade primário listado no `endpointName` atributo de [\<add>](add-of-entries.md) falhar com uma exceção de comunicação, o serviço de roteamento tentará enviar a mensagem para o primeiro ponto de extremidade nesta seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="70e85-121">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="70e85-122">Se isso também falhar com uma exceção de comunicação, o serviço de roteamento tentará enviar a mensagem para a próxima mensagem contida nesta seção até que a tentativa de envio seja bem-sucedida, retorna uma falha diferente de uma exceção de comunicação ou todos os pontos de extremidade na coleção retornaram uma falha.</span><span class="sxs-lookup"><span data-stu-id="70e85-122">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="70e85-123">No exemplo a seguir, se um envio para o ponto de extremidade primário chamado "destino" retornar uma exceção de comunicação, o serviço tentará enviar a mensagem para o "alternateServiceQueue".</span><span class="sxs-lookup"><span data-stu-id="70e85-123">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="70e85-124">Se essa tentativa também retornar uma exceção de comunicação, o serviço de roteamento tentará enviar a mensagem para o próximo ponto de extremidade na coleção.</span><span class="sxs-lookup"><span data-stu-id="70e85-124">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
```xml  
<filterTables>
  <filterTable name="filterTable1">
    <add filterName="MatchAllFilter1"
         endpointName="Destination"
         backupList="backupEndpointList" />
  </filterTable>
</filterTables>
<backupLists>
  <backupList name="backupEndpointList">
    <add endpointName="backupServiceQueue" />
    <add endpointName="alternateServiceQueue" />
  </backupList>
</backupLists>
```  
  
## <a name="see-also"></a><span data-ttu-id="70e85-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="70e85-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
