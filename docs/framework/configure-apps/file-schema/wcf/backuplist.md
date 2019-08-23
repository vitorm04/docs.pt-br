---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: d5feab6cb374f98e683cf15f797de4f478e23131
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919917"
---
# <a name="backuplist"></a><span data-ttu-id="ac912-101">\<> de BackupList</span><span class="sxs-lookup"><span data-stu-id="ac912-101">\<backupList></span></span>
<span data-ttu-id="ac912-102">Representa uma seção de configuração para definir uma lista de backup que enumera um conjunto de pontos de extremidade que você deseja que o serviço de roteamento use caso o ponto de extremidade primário não possa ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="ac912-102">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="ac912-103">Se o primeiro ponto de extremidade na lista estiver inativo, o serviço de roteamento fará failover automaticamente para o próximo da lista.</span><span class="sxs-lookup"><span data-stu-id="ac912-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="ac912-104">Isso lhe dá uma maneira rápida de adicionar confiabilidade ao seu aplicativo sem ter que ensinar o aplicativo cliente a lidar com padrões complexos ou onde todos os seus serviços são implantados.</span><span class="sxs-lookup"><span data-stu-id="ac912-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="ac912-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ac912-105">\<system.serviceModel></span></span>  
<span data-ttu-id="ac912-106">\<> de roteamento</span><span class="sxs-lookup"><span data-stu-id="ac912-106">\<routing></span></span>  
<span data-ttu-id="ac912-107">\<> backupLists</span><span class="sxs-lookup"><span data-stu-id="ac912-107">\<backupLists></span></span>  
<span data-ttu-id="ac912-108">\<> de BackupList</span><span class="sxs-lookup"><span data-stu-id="ac912-108">\<backupList></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac912-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac912-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac912-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ac912-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ac912-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ac912-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac912-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="ac912-112">Attributes</span></span>  
  
|<span data-ttu-id="ac912-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="ac912-113">Attribute</span></span>|<span data-ttu-id="ac912-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac912-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ac912-115">name</span><span class="sxs-lookup"><span data-stu-id="ac912-115">name</span></span>|<span data-ttu-id="ac912-116">Uma cadeia de caracteres que especifica o nome usado para identificar esta lista de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ac912-116">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac912-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ac912-117">Child Elements</span></span>  
  
|<span data-ttu-id="ac912-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="ac912-118">Element</span></span>|<span data-ttu-id="ac912-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac912-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac912-120">\<filter></span><span class="sxs-lookup"><span data-stu-id="ac912-120">\<filter></span></span>](filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="ac912-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ac912-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ac912-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="ac912-122">Element</span></span>|<span data-ttu-id="ac912-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac912-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac912-124">\<routing></span><span class="sxs-lookup"><span data-stu-id="ac912-124">\<routing></span></span>](routing.md)|<span data-ttu-id="ac912-125">Uma lista de pontos de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="ac912-125">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac912-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac912-126">Remarks</span></span>  
 <span data-ttu-id="ac912-127">Esta seção contém uma coleção ordenada de pontos de extremidade para os quais uma mensagem será transmitida no caso de uma exceção de comunicação ao enviar para o ponto de extremidade primário.</span><span class="sxs-lookup"><span data-stu-id="ac912-127">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="ac912-128">Se um envio para o ponto de extremidade primário listado `endpointName` no atributo de [ \<Add >](add-of-entries.md) falhar com uma exceção de comunicação, o serviço de roteamento tentará enviar a mensagem para o primeiro ponto de extremidade nesta seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="ac912-128">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="ac912-129">Se isso também falhar com uma exceção de comunicação, o serviço de roteamento tentará enviar a mensagem para a próxima mensagem contida nesta seção até que a tentativa de envio seja bem-sucedida, retorna uma falha diferente de uma exceção de comunicação ou todos os pontos de extremidade no a coleta retornou uma falha.</span><span class="sxs-lookup"><span data-stu-id="ac912-129">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="ac912-130">No exemplo a seguir, se um envio para o ponto de extremidade primário chamado "destino" retornar uma exceção de comunicação, o serviço tentará enviar a mensagem para o "alternateServiceQueue".</span><span class="sxs-lookup"><span data-stu-id="ac912-130">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="ac912-131">Se essa tentativa também retornar uma exceção de comunicação, o serviço de roteamento tentará enviar a mensagem para o próximo ponto de extremidade na coleção.</span><span class="sxs-lookup"><span data-stu-id="ac912-131">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ac912-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac912-132">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
