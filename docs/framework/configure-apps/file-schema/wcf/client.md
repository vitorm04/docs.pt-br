---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 6cc8b80edb3206bb2ef3a8a1ffa34ab40af77612
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398147"
---
# <a name="client"></a><span data-ttu-id="43a8f-101">\<client></span><span class="sxs-lookup"><span data-stu-id="43a8f-101">\<client></span></span>
<span data-ttu-id="43a8f-102">O `client` elemento define uma lista de pontos de extremidade aos quais um cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="43a8f-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
<span data-ttu-id="43a8f-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="43a8f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="43a8f-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="43a8f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="43a8f-105">&nbsp;&nbsp;&nbsp;&nbsp; **\<> do cliente**</span><span class="sxs-lookup"><span data-stu-id="43a8f-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43a8f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43a8f-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43a8f-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="43a8f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="43a8f-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="43a8f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43a8f-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="43a8f-109">Attributes</span></span>  
 <span data-ttu-id="43a8f-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="43a8f-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="43a8f-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="43a8f-111">Child Elements</span></span>  
  
|<span data-ttu-id="43a8f-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="43a8f-112">Element</span></span>|<span data-ttu-id="43a8f-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="43a8f-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43a8f-114">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="43a8f-114">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="43a8f-115">Contém uma coleção de elementos EndPoint, que especificam os pontos de extremidade aos quais esse cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="43a8f-115">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="43a8f-116">\<metadata></span><span class="sxs-lookup"><span data-stu-id="43a8f-116">\<metadata></span></span>](metadata.md)|<span data-ttu-id="43a8f-117">Contém configurações para processar metadados.</span><span class="sxs-lookup"><span data-stu-id="43a8f-117">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="43a8f-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="43a8f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="43a8f-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="43a8f-119">Element</span></span>|<span data-ttu-id="43a8f-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="43a8f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43a8f-121">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="43a8f-121">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="43a8f-122">O elemento raiz de todos os elementos de configuração de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="43a8f-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43a8f-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="43a8f-123">Remarks</span></span>  
 <span data-ttu-id="43a8f-124">A `client` seção define uma lista de pontos de extremidade aos quais um cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="43a8f-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="43a8f-125">Cada ponto de extremidade listado na seção cliente define sua própria associação, comportamento e contrato.</span><span class="sxs-lookup"><span data-stu-id="43a8f-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="43a8f-126">Ele é identificado exclusivamente pela combinação dos `name` atributos e. `contract`</span><span class="sxs-lookup"><span data-stu-id="43a8f-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="43a8f-127">O código do cliente especifica `name` o para se conectar a um ponto de extremidade para o serviço que o cliente implementa.</span><span class="sxs-lookup"><span data-stu-id="43a8f-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="43a8f-128">Se o `name` atributo for omitido, o ponto de extremidade atua como o ponto de extremidade padrão para o contrato que ele implementa.</span><span class="sxs-lookup"><span data-stu-id="43a8f-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="43a8f-129">Além disso, esta seção também especifica configurações para processar metadados.</span><span class="sxs-lookup"><span data-stu-id="43a8f-129">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43a8f-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43a8f-130">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43a8f-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43a8f-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="43a8f-132">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="43a8f-132">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="43a8f-133">Clientes</span><span class="sxs-lookup"><span data-stu-id="43a8f-133">Clients</span></span>](../../../wcf/feature-details/clients.md)
