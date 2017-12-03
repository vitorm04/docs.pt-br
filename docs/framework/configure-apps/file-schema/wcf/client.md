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
ms.openlocfilehash: 260408bd168246b67830637ca53e78b78758b849
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltclientgt"></a><span data-ttu-id="a1a55-102">&lt;cliente&gt;</span><span class="sxs-lookup"><span data-stu-id="a1a55-102">&lt;client&gt;</span></span>
<span data-ttu-id="a1a55-103">O `client` elemento define uma lista de pontos de extremidade que um cliente pode se conectar ao.</span><span class="sxs-lookup"><span data-stu-id="a1a55-103">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="a1a55-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a1a55-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a1a55-105">\<cliente ></span><span class="sxs-lookup"><span data-stu-id="a1a55-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1a55-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1a55-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1a55-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a1a55-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a1a55-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a1a55-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1a55-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="a1a55-109">Attributes</span></span>  
 <span data-ttu-id="a1a55-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a1a55-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a1a55-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a1a55-111">Child Elements</span></span>  
  
|<span data-ttu-id="a1a55-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="a1a55-112">Element</span></span>|<span data-ttu-id="a1a55-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1a55-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1a55-114">\<ponto de extremidade ></span><span class="sxs-lookup"><span data-stu-id="a1a55-114">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="a1a55-115">Contém uma coleção de elementos de ponto de extremidade, que especificam os pontos de extremidade que esse cliente pode se conectar ao.</span><span class="sxs-lookup"><span data-stu-id="a1a55-115">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="a1a55-116">\<metadados ></span><span class="sxs-lookup"><span data-stu-id="a1a55-116">\<metadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|<span data-ttu-id="a1a55-117">Contém configurações para processamento de metadados.</span><span class="sxs-lookup"><span data-stu-id="a1a55-117">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a1a55-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a1a55-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a1a55-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="a1a55-119">Element</span></span>|<span data-ttu-id="a1a55-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1a55-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1a55-121">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a1a55-121">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="a1a55-122">O elemento raiz de todos os elementos de configuração do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a1a55-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1a55-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="a1a55-123">Remarks</span></span>  
 <span data-ttu-id="a1a55-124">O `client` seção define uma lista de pontos de extremidade que um cliente pode se conectar ao.</span><span class="sxs-lookup"><span data-stu-id="a1a55-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="a1a55-125">Cada ponto de extremidade listado na seção de cliente define sua própria associação, o comportamento e o contrato.</span><span class="sxs-lookup"><span data-stu-id="a1a55-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="a1a55-126">Ela é identificada exclusivamente pela combinação da `name` e `contract` atributos.</span><span class="sxs-lookup"><span data-stu-id="a1a55-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="a1a55-127">O código do cliente especifica a `name` para se conectar a um ponto de extremidade para o serviço que implementa o cliente.</span><span class="sxs-lookup"><span data-stu-id="a1a55-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="a1a55-128">Se o `name` atributo for omitido, o ponto de extremidade atua como o ponto de extremidade padrão para o contrato ele implementa.</span><span class="sxs-lookup"><span data-stu-id="a1a55-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="a1a55-129">Além disso, esta seção também especifica configurações de processamento de metadados.</span><span class="sxs-lookup"><span data-stu-id="a1a55-129">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1a55-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a1a55-130">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a1a55-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1a55-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 [<span data-ttu-id="a1a55-132">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="a1a55-132">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="a1a55-133">Clientes</span><span class="sxs-lookup"><span data-stu-id="a1a55-133">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
