---
title: '&lt;Cliente&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: b8a006d3dee4149569b3f5b573d9d765504b0d65
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752631"
---
# <a name="ltclientgt"></a><span data-ttu-id="616cd-102">&lt;Cliente&gt;</span><span class="sxs-lookup"><span data-stu-id="616cd-102">&lt;client&gt;</span></span>
<span data-ttu-id="616cd-103">O `client` elemento define uma lista de pontos de extremidade que um cliente pode se conectar ao.</span><span class="sxs-lookup"><span data-stu-id="616cd-103">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="616cd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="616cd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="616cd-105">\<client></span><span class="sxs-lookup"><span data-stu-id="616cd-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="616cd-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="616cd-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="616cd-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="616cd-107">Attributes and Elements</span></span>  
 <span data-ttu-id="616cd-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="616cd-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="616cd-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="616cd-109">Attributes</span></span>  
 <span data-ttu-id="616cd-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="616cd-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="616cd-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="616cd-111">Child Elements</span></span>  
  
|<span data-ttu-id="616cd-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="616cd-112">Element</span></span>|<span data-ttu-id="616cd-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="616cd-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="616cd-114">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="616cd-114">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="616cd-115">Contém uma coleção de elementos de ponto de extremidade, que especificam os pontos de extremidade que esse cliente pode se conectar ao.</span><span class="sxs-lookup"><span data-stu-id="616cd-115">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="616cd-116">\<metadados ></span><span class="sxs-lookup"><span data-stu-id="616cd-116">\<metadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|<span data-ttu-id="616cd-117">Contém configurações para processamento de metadados.</span><span class="sxs-lookup"><span data-stu-id="616cd-117">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="616cd-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="616cd-118">Parent Elements</span></span>  
  
|<span data-ttu-id="616cd-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="616cd-119">Element</span></span>|<span data-ttu-id="616cd-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="616cd-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="616cd-121">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="616cd-121">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="616cd-122">O elemento raiz de todos os elementos de configuração do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="616cd-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="616cd-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="616cd-123">Remarks</span></span>  
 <span data-ttu-id="616cd-124">O `client` seção define uma lista de pontos de extremidade que um cliente pode se conectar ao.</span><span class="sxs-lookup"><span data-stu-id="616cd-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="616cd-125">Cada ponto de extremidade listado na seção de cliente define sua própria associação, o comportamento e o contrato.</span><span class="sxs-lookup"><span data-stu-id="616cd-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="616cd-126">Ela é identificada exclusivamente pela combinação da `name` e `contract` atributos.</span><span class="sxs-lookup"><span data-stu-id="616cd-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="616cd-127">O código do cliente especifica a `name` para se conectar a um ponto de extremidade para o serviço que implementa o cliente.</span><span class="sxs-lookup"><span data-stu-id="616cd-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="616cd-128">Se o `name` atributo for omitido, o ponto de extremidade atua como o ponto de extremidade padrão para o contrato ele implementa.</span><span class="sxs-lookup"><span data-stu-id="616cd-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="616cd-129">Além disso, esta seção também especifica configurações de processamento de metadados.</span><span class="sxs-lookup"><span data-stu-id="616cd-129">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="616cd-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="616cd-130">Example</span></span>  
  
```xml  
<client>  
    <endpoint address="/HelloWorld/"  
              bindingConfiguration="usingDefaults"  
              name="MyBinding"  
              binding="customBinding"  
              contract="HelloWorld">  
    <addressProperties actingAs="http://www.microsoft.com/TestActor"  
             identityData="BasicReadWrite" identityType="Spn" isAddressPrivate="false">  
    </endpoint>  
</client>  
```  
  
## <a name="see-also"></a><span data-ttu-id="616cd-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="616cd-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 [<span data-ttu-id="616cd-132">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="616cd-132">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="616cd-133">Clientes</span><span class="sxs-lookup"><span data-stu-id="616cd-133">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
