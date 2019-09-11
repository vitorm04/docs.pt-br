---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 478211755b9131c03b72777ee95ff7223b9092c9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850279"
---
# <a name="backuplist"></a><span data-ttu-id="cf9e0-101">\<> de BackupList</span><span class="sxs-lookup"><span data-stu-id="cf9e0-101">\<backupList></span></span>
<span data-ttu-id="cf9e0-102">Representa uma seção de configuração para definir uma lista de backup que enumera um conjunto de pontos de extremidade que você deseja que o serviço de roteamento use caso o ponto de extremidade primário não possa ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="cf9e0-102">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="cf9e0-103">Se o primeiro ponto de extremidade na lista estiver inativo, o serviço de roteamento fará failover automaticamente para o próximo da lista.</span><span class="sxs-lookup"><span data-stu-id="cf9e0-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="cf9e0-104">Isso lhe dá uma maneira rápida de adicionar confiabilidade ao seu aplicativo sem ter que ensinar o aplicativo cliente a lidar com padrões complexos ou onde todos os seus serviços são implantados.</span><span class="sxs-lookup"><span data-stu-id="cf9e0-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
<span data-ttu-id="cf9e0-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cf9e0-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cf9e0-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="cf9e0-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cf9e0-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de roteamento**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="cf9e0-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="cf9e0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> backupLists**](backuplists.md)</span><span class="sxs-lookup"><span data-stu-id="cf9e0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)</span></span>\
<span data-ttu-id="cf9e0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de BackupList**</span><span class="sxs-lookup"><span data-stu-id="cf9e0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupList>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf9e0-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf9e0-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf9e0-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cf9e0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cf9e0-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cf9e0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf9e0-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="cf9e0-113">Attributes</span></span>  
  
|<span data-ttu-id="cf9e0-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="cf9e0-114">Attribute</span></span>|<span data-ttu-id="cf9e0-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf9e0-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cf9e0-116">name</span><span class="sxs-lookup"><span data-stu-id="cf9e0-116">name</span></span>|<span data-ttu-id="cf9e0-117">Uma cadeia de caracteres que especifica o nome usado para identificar esta lista de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="cf9e0-117">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf9e0-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cf9e0-118">Child Elements</span></span>  
  
|<span data-ttu-id="cf9e0-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="cf9e0-119">Element</span></span>|<span data-ttu-id="cf9e0-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf9e0-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf9e0-121">\<filter></span><span class="sxs-lookup"><span data-stu-id="cf9e0-121">\<filter></span></span>](filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="cf9e0-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cf9e0-122">Parent Elements</span></span>  
  
|<span data-ttu-id="cf9e0-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="cf9e0-123">Element</span></span>|<span data-ttu-id="cf9e0-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf9e0-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf9e0-125">\<routing></span><span class="sxs-lookup"><span data-stu-id="cf9e0-125">\<routing></span></span>](routing.md)|<span data-ttu-id="cf9e0-126">Uma lista de pontos de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="cf9e0-126">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf9e0-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="cf9e0-127">Remarks</span></span>  
 <span data-ttu-id="cf9e0-128">Esta seção contém uma coleção ordenada de pontos de extremidade para os quais uma mensagem será transmitida no caso de uma exceção de comunicação ao enviar para o ponto de extremidade primário.</span><span class="sxs-lookup"><span data-stu-id="cf9e0-128">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="cf9e0-129">Se um envio para o ponto de extremidade primário listado `endpointName` no atributo de [ \<Add >](add-of-entries.md) falhar com uma exceção de comunicação, o serviço de roteamento tentará enviar a mensagem para o primeiro ponto de extremidade nesta seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="cf9e0-129">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="cf9e0-130">Se isso também falhar com uma exceção de comunicação, o serviço de roteamento tentará enviar a mensagem para a próxima mensagem contida nesta seção até que a tentativa de envio seja bem-sucedida, retorna uma falha diferente de uma exceção de comunicação ou todos os pontos de extremidade no a coleta retornou uma falha.</span><span class="sxs-lookup"><span data-stu-id="cf9e0-130">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="cf9e0-131">No exemplo a seguir, se um envio para o ponto de extremidade primário chamado "destino" retornar uma exceção de comunicação, o serviço tentará enviar a mensagem para o "alternateServiceQueue".</span><span class="sxs-lookup"><span data-stu-id="cf9e0-131">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="cf9e0-132">Se essa tentativa também retornar uma exceção de comunicação, o serviço de roteamento tentará enviar a mensagem para o próximo ponto de extremidade na coleção.</span><span class="sxs-lookup"><span data-stu-id="cf9e0-132">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cf9e0-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf9e0-133">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
