---
title: '&lt;backupList&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e9f8138f2a2448293e1f26da5f7d0562b1338b7d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltbackuplistgt"></a><span data-ttu-id="47eaf-102">&lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="47eaf-102">&lt;backupList&gt;</span></span>
<span data-ttu-id="47eaf-103">Representa uma seção de configuração para definir uma lista de backup que enumera um conjunto de pontos de extremidade que você deseja que o serviço de roteamento para usar no caso do ponto de extremidade primário não pode ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="47eaf-103">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="47eaf-104">Se o primeiro ponto de extremidade na lista estiver inativo, o serviço de roteamento irá automaticamente failover para o próximo na lista.</span><span class="sxs-lookup"><span data-stu-id="47eaf-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="47eaf-105">Isso fornece uma maneira rápida de adicionar confiabilidade para seu aplicativo sem ter que ensinar seu aplicativo cliente como lidar com padrões complexos ou onde todos os serviços são implantados.</span><span class="sxs-lookup"><span data-stu-id="47eaf-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="47eaf-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="47eaf-106">\<system.serviceModel></span></span>  
<span data-ttu-id="47eaf-107">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="47eaf-107">\<routing></span></span>  
<span data-ttu-id="47eaf-108">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="47eaf-108">\<backupLists></span></span>  
<span data-ttu-id="47eaf-109">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="47eaf-109">\<backupList></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47eaf-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47eaf-110">Syntax</span></span>  
  
```xml 
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="47eaf-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="47eaf-111">Attributes and Elements</span></span>  
 <span data-ttu-id="47eaf-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="47eaf-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47eaf-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="47eaf-113">Attributes</span></span>  
  
|<span data-ttu-id="47eaf-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="47eaf-114">Attribute</span></span>|<span data-ttu-id="47eaf-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="47eaf-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="47eaf-116">name</span><span class="sxs-lookup"><span data-stu-id="47eaf-116">name</span></span>|<span data-ttu-id="47eaf-117">Uma cadeia de caracteres que especifica o nome usado para identificar esta lista de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="47eaf-117">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47eaf-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="47eaf-118">Child Elements</span></span>  
  
|<span data-ttu-id="47eaf-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="47eaf-119">Element</span></span>|<span data-ttu-id="47eaf-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="47eaf-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47eaf-121">\<filter></span><span class="sxs-lookup"><span data-stu-id="47eaf-121">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="47eaf-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="47eaf-122">Parent Elements</span></span>  
  
|<span data-ttu-id="47eaf-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="47eaf-123">Element</span></span>|<span data-ttu-id="47eaf-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="47eaf-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47eaf-125">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="47eaf-125">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="47eaf-126">Uma lista de pontos de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="47eaf-126">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47eaf-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="47eaf-127">Remarks</span></span>  
 <span data-ttu-id="47eaf-128">Esta seção contém uma coleção ordenada de pontos de extremidade que uma mensagem será transmitida no caso de uma exceção de comunicação ao enviar para o ponto de extremidade primário.</span><span class="sxs-lookup"><span data-stu-id="47eaf-128">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="47eaf-129">Se um envio para o ponto de extremidade primário é listado no `endpointName` atributo de [ \<Adicionar >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) falhará com uma exceção de comunicação, o serviço de roteamento tentará enviar a mensagem para o primeiro ponto de extremidade na seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="47eaf-129">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="47eaf-130">Se isso também falhará com uma exceção de comunicações, o serviço de roteamento tentará enviar a mensagem para a próxima mensagem contida nesta seção até que a tentativa de envio seja bem-sucedida, retorna uma falha que não seja uma exceção de comunicação ou todos os pontos de extremidade do coleção têm retornou uma falha.</span><span class="sxs-lookup"><span data-stu-id="47eaf-130">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="47eaf-131">No exemplo a seguir, se um envio para o ponto de extremidade primário chamado "Destino" retorna uma exceção de comunicação, o serviço tentará enviar a mensagem para "alternateServiceQueue".</span><span class="sxs-lookup"><span data-stu-id="47eaf-131">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="47eaf-132">Se essa tentativa também retorna uma exceção de comunicação, o serviço de roteamento tentará enviar a mensagem para o próximo ponto de extremidade na coleção.</span><span class="sxs-lookup"><span data-stu-id="47eaf-132">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="MatchAllFilter1" endpointName="Destination" backupList="backupEndpointList"/>  
     </filterTable>  
</filterTables>  
<backupLists>  
     <backupList name="backupEndpointList">  
          <add endpointName="backupServiceQueue" />  
          <add endpointName="alternateServiceQueue" />  
     </backupList>  
</backupLists>  
```  
  
## <a name="see-also"></a><span data-ttu-id="47eaf-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47eaf-133">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
