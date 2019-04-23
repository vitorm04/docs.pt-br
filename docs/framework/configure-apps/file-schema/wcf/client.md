---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 2e0352efdd5b709984338fe4484b120bddb7d545
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164353"
---
# <a name="client"></a><span data-ttu-id="9f9c1-101">\<client></span><span class="sxs-lookup"><span data-stu-id="9f9c1-101">\<client></span></span>
<span data-ttu-id="9f9c1-102">O `client` elemento define uma lista de pontos de extremidade que um cliente pode se conectar ao.</span><span class="sxs-lookup"><span data-stu-id="9f9c1-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="9f9c1-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9f9c1-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="9f9c1-104">\<client></span><span class="sxs-lookup"><span data-stu-id="9f9c1-104">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f9c1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f9c1-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f9c1-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9f9c1-106">Attributes and Elements</span></span>  
 <span data-ttu-id="9f9c1-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9f9c1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f9c1-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="9f9c1-108">Attributes</span></span>  
 <span data-ttu-id="9f9c1-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9f9c1-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9f9c1-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9f9c1-110">Child Elements</span></span>  
  
|<span data-ttu-id="9f9c1-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="9f9c1-111">Element</span></span>|<span data-ttu-id="9f9c1-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f9c1-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f9c1-113">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="9f9c1-113">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="9f9c1-114">Contém uma coleção de elementos de ponto de extremidade, que especificam os pontos de extremidade que esse cliente pode se conectar ao.</span><span class="sxs-lookup"><span data-stu-id="9f9c1-114">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="9f9c1-115">\<metadata></span><span class="sxs-lookup"><span data-stu-id="9f9c1-115">\<metadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|<span data-ttu-id="9f9c1-116">Contém configurações para metadados de processamento.</span><span class="sxs-lookup"><span data-stu-id="9f9c1-116">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9f9c1-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9f9c1-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9f9c1-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="9f9c1-118">Element</span></span>|<span data-ttu-id="9f9c1-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f9c1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f9c1-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9f9c1-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="9f9c1-121">O elemento raiz de todos os elementos de configuração do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9f9c1-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f9c1-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f9c1-122">Remarks</span></span>  
 <span data-ttu-id="9f9c1-123">O `client` seção define uma lista de pontos de extremidade que um cliente pode se conectar ao.</span><span class="sxs-lookup"><span data-stu-id="9f9c1-123">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="9f9c1-124">Cada ponto de extremidade listado na seção cliente define sua própria associação, o comportamento e o contrato.</span><span class="sxs-lookup"><span data-stu-id="9f9c1-124">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="9f9c1-125">Ele é identificado exclusivamente pela combinação da `name` e `contract` atributos.</span><span class="sxs-lookup"><span data-stu-id="9f9c1-125">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="9f9c1-126">Especifica o código do cliente a `name` para se conectar a um ponto de extremidade para o serviço que implementa o cliente.</span><span class="sxs-lookup"><span data-stu-id="9f9c1-126">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="9f9c1-127">Se o `name` atributo for omitido, o ponto de extremidade atua como o ponto de extremidade padrão para o contrato ele implementa.</span><span class="sxs-lookup"><span data-stu-id="9f9c1-127">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="9f9c1-128">Além disso, esta seção também especifica configurações para metadados de processamento.</span><span class="sxs-lookup"><span data-stu-id="9f9c1-128">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f9c1-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9f9c1-129">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9f9c1-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f9c1-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="9f9c1-131">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="9f9c1-131">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="9f9c1-132">Clientes</span><span class="sxs-lookup"><span data-stu-id="9f9c1-132">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
