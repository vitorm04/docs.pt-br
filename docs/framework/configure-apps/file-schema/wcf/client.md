---
title: '&lt;cliente&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7d52d74c36ea1b1d722d781f554f8cc6691d53e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltclientgt"></a><span data-ttu-id="5903e-102">&lt;cliente&gt;</span><span class="sxs-lookup"><span data-stu-id="5903e-102">&lt;client&gt;</span></span>
<span data-ttu-id="5903e-103">O `client` elemento define uma lista de pontos de extremidade que um cliente pode se conectar ao.</span><span class="sxs-lookup"><span data-stu-id="5903e-103">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="5903e-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5903e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5903e-105">\<cliente ></span><span class="sxs-lookup"><span data-stu-id="5903e-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5903e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5903e-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5903e-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5903e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5903e-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5903e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5903e-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="5903e-109">Attributes</span></span>  
 <span data-ttu-id="5903e-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5903e-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5903e-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5903e-111">Child Elements</span></span>  
  
|<span data-ttu-id="5903e-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="5903e-112">Element</span></span>|<span data-ttu-id="5903e-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="5903e-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5903e-114">\<ponto de extremidade ></span><span class="sxs-lookup"><span data-stu-id="5903e-114">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="5903e-115">Contém uma coleção de elementos de ponto de extremidade, que especificam os pontos de extremidade que esse cliente pode se conectar ao.</span><span class="sxs-lookup"><span data-stu-id="5903e-115">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="5903e-116">\<metadados ></span><span class="sxs-lookup"><span data-stu-id="5903e-116">\<metadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|<span data-ttu-id="5903e-117">Contém configurações para processamento de metadados.</span><span class="sxs-lookup"><span data-stu-id="5903e-117">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5903e-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5903e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5903e-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="5903e-119">Element</span></span>|<span data-ttu-id="5903e-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="5903e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5903e-121">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5903e-121">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="5903e-122">O elemento raiz de todos os elementos de configuração do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5903e-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5903e-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="5903e-123">Remarks</span></span>  
 <span data-ttu-id="5903e-124">O `client` seção define uma lista de pontos de extremidade que um cliente pode se conectar ao.</span><span class="sxs-lookup"><span data-stu-id="5903e-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="5903e-125">Cada ponto de extremidade listado na seção de cliente define sua própria associação, o comportamento e o contrato.</span><span class="sxs-lookup"><span data-stu-id="5903e-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="5903e-126">Ela é identificada exclusivamente pela combinação da `name` e `contract` atributos.</span><span class="sxs-lookup"><span data-stu-id="5903e-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="5903e-127">O código do cliente especifica a `name` para se conectar a um ponto de extremidade para o serviço que implementa o cliente.</span><span class="sxs-lookup"><span data-stu-id="5903e-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="5903e-128">Se o `name` atributo for omitido, o ponto de extremidade atua como o ponto de extremidade padrão para o contrato ele implementa.</span><span class="sxs-lookup"><span data-stu-id="5903e-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="5903e-129">Além disso, esta seção também especifica configurações de processamento de metadados.</span><span class="sxs-lookup"><span data-stu-id="5903e-129">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5903e-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5903e-130">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5903e-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5903e-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 [<span data-ttu-id="5903e-132">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="5903e-132">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="5903e-133">Clientes</span><span class="sxs-lookup"><span data-stu-id="5903e-133">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
