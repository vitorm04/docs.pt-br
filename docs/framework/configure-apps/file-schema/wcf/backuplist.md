---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: b0a6c604b5741c1355c35fca510cd10544dab9f3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704421"
---
# <a name="backuplist"></a><span data-ttu-id="0910e-101">\<backupList></span><span class="sxs-lookup"><span data-stu-id="0910e-101">\<backupList></span></span>
<span data-ttu-id="0910e-102">Representa uma seção de configuração para definir uma lista de backup que enumera um conjunto de pontos de extremidade que você gostaria que o serviço de roteamento use caso o ponto de extremidade primário não pode ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="0910e-102">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="0910e-103">Se o primeiro ponto de extremidade na lista estiver inativo, o serviço de roteamento irá automaticamente failover para o próximo na lista.</span><span class="sxs-lookup"><span data-stu-id="0910e-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="0910e-104">Isso lhe dá uma maneira rápida de adicionar confiabilidade para seu aplicativo sem ter que ensinar o aplicativo cliente como lidar com padrões complexos ou onde todos os seus serviços são implantados.</span><span class="sxs-lookup"><span data-stu-id="0910e-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="0910e-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0910e-105">\<system.serviceModel></span></span>  
<span data-ttu-id="0910e-106">\<routing></span><span class="sxs-lookup"><span data-stu-id="0910e-106">\<routing></span></span>  
<span data-ttu-id="0910e-107">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="0910e-107">\<backupLists></span></span>  
<span data-ttu-id="0910e-108">\<backupList></span><span class="sxs-lookup"><span data-stu-id="0910e-108">\<backupList></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0910e-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0910e-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0910e-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0910e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0910e-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0910e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0910e-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="0910e-112">Attributes</span></span>  
  
|<span data-ttu-id="0910e-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="0910e-113">Attribute</span></span>|<span data-ttu-id="0910e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="0910e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0910e-115">name</span><span class="sxs-lookup"><span data-stu-id="0910e-115">name</span></span>|<span data-ttu-id="0910e-116">Uma cadeia de caracteres que especifica o nome usado para identificar esta lista de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="0910e-116">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0910e-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0910e-117">Child Elements</span></span>  
  
|<span data-ttu-id="0910e-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="0910e-118">Element</span></span>|<span data-ttu-id="0910e-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="0910e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0910e-120">\<filter></span><span class="sxs-lookup"><span data-stu-id="0910e-120">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="0910e-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0910e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0910e-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="0910e-122">Element</span></span>|<span data-ttu-id="0910e-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="0910e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0910e-124">\<routing></span><span class="sxs-lookup"><span data-stu-id="0910e-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="0910e-125">Uma lista de pontos de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="0910e-125">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0910e-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="0910e-126">Remarks</span></span>  
 <span data-ttu-id="0910e-127">Esta seção contém uma coleção ordenada de pontos de extremidade que uma mensagem será transmitida no caso de uma exceção de comunicação ao enviar para o ponto de extremidade primário.</span><span class="sxs-lookup"><span data-stu-id="0910e-127">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="0910e-128">Se um envio para o ponto de extremidade primário é listado na `endpointName` atributo de [ \<Adicionar >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) falhar com uma exceção de comunicação, o serviço de roteamento tentará enviar a mensagem para o primeiro ponto de extremidade neste seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="0910e-128">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="0910e-129">Se isso também falhar com uma exceção de comunicação, o serviço de roteamento tentará enviar a mensagem para a próxima mensagem contida nesta seção até que a tentativa de envio for bem-sucedido, retornará uma falha que não seja uma exceção de comunicação ou todos os pontos de extremidade no coleção ter retornou uma falha.</span><span class="sxs-lookup"><span data-stu-id="0910e-129">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="0910e-130">No exemplo a seguir, se um envio para o ponto de extremidade primário chamado "Destino" retorna uma exceção de comunicação, o serviço tentará enviar a mensagem para "alternateServiceQueue".</span><span class="sxs-lookup"><span data-stu-id="0910e-130">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="0910e-131">Se essa tentativa também retorna uma exceção de comunicação, o serviço de roteamento tentará enviar a mensagem para o próximo ponto de extremidade na coleção.</span><span class="sxs-lookup"><span data-stu-id="0910e-131">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0910e-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0910e-132">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
