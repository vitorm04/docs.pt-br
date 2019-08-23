---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 7dce5984882e48c3e62efc44ef00b6256d9eb64e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919536"
---
# <a name="client"></a><span data-ttu-id="d1d9f-101">\<client></span><span class="sxs-lookup"><span data-stu-id="d1d9f-101">\<client></span></span>
<span data-ttu-id="d1d9f-102">O `client` elemento define uma lista de pontos de extremidade aos quais um cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="d1d9f-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="d1d9f-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d1d9f-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d1d9f-104">\<client></span><span class="sxs-lookup"><span data-stu-id="d1d9f-104">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1d9f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1d9f-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <client>
    <endpoint>
    </endpoint>
    <metadata>
    </metadata>
  </client>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1d9f-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d1d9f-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d1d9f-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d1d9f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1d9f-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="d1d9f-108">Attributes</span></span>  
 <span data-ttu-id="d1d9f-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d1d9f-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d1d9f-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d1d9f-110">Child Elements</span></span>  
  
|<span data-ttu-id="d1d9f-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="d1d9f-111">Element</span></span>|<span data-ttu-id="d1d9f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d1d9f-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1d9f-113">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="d1d9f-113">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="d1d9f-114">Contém uma coleção de elementos EndPoint, que especificam os pontos de extremidade aos quais esse cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="d1d9f-114">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="d1d9f-115">\<metadata></span><span class="sxs-lookup"><span data-stu-id="d1d9f-115">\<metadata></span></span>](metadata.md)|<span data-ttu-id="d1d9f-116">Contém configurações para processar metadados.</span><span class="sxs-lookup"><span data-stu-id="d1d9f-116">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d1d9f-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d1d9f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d1d9f-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="d1d9f-118">Element</span></span>|<span data-ttu-id="d1d9f-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="d1d9f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1d9f-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d1d9f-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="d1d9f-121">O elemento raiz de todos os elementos de configuração de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d1d9f-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1d9f-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="d1d9f-122">Remarks</span></span>  
 <span data-ttu-id="d1d9f-123">A `client` seção define uma lista de pontos de extremidade aos quais um cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="d1d9f-123">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="d1d9f-124">Cada ponto de extremidade listado na seção cliente define sua própria associação, comportamento e contrato.</span><span class="sxs-lookup"><span data-stu-id="d1d9f-124">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="d1d9f-125">Ele é identificado exclusivamente pela combinação dos `name` atributos e. `contract`</span><span class="sxs-lookup"><span data-stu-id="d1d9f-125">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="d1d9f-126">O código do cliente especifica `name` o para se conectar a um ponto de extremidade para o serviço que o cliente implementa.</span><span class="sxs-lookup"><span data-stu-id="d1d9f-126">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="d1d9f-127">Se o `name` atributo for omitido, o ponto de extremidade atua como o ponto de extremidade padrão para o contrato que ele implementa.</span><span class="sxs-lookup"><span data-stu-id="d1d9f-127">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="d1d9f-128">Além disso, esta seção também especifica configurações para processar metadados.</span><span class="sxs-lookup"><span data-stu-id="d1d9f-128">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1d9f-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d1d9f-129">Example</span></span>  
  
```xml  
<client>
  <endpoint address="/HelloWorld/"
            bindingConfiguration="usingDefaults"
            name="MyBinding"
            binding="customBinding"
            contract="HelloWorld">
    <addressProperties actingAs="http://www.microsoft.com/TestActor"
                       identityData="BasicReadWrite"
                       identityType="Spn"
                       isAddressPrivate="false">
  </endpoint>
</client>
```  
  
## <a name="see-also"></a><span data-ttu-id="d1d9f-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1d9f-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="d1d9f-131">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="d1d9f-131">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="d1d9f-132">Clientes</span><span class="sxs-lookup"><span data-stu-id="d1d9f-132">Clients</span></span>](../../../wcf/feature-details/clients.md)
