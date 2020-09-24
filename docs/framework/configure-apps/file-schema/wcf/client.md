---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: b3234bfa60cd1e3c88778951fc27301c615c84ba
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148952"
---
# \<client>

<span data-ttu-id="c718a-101">O `client` elemento define uma lista de pontos de extremidade aos quais um cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="c718a-101">The `client` element defines a list of endpoints that a client can connect to.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**

## <a name="syntax"></a><span data-ttu-id="c718a-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="c718a-102">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="c718a-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c718a-103">Attributes and Elements</span></span>

 <span data-ttu-id="c718a-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c718a-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c718a-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="c718a-105">Attributes</span></span>

 <span data-ttu-id="c718a-106">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c718a-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="c718a-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c718a-107">Child Elements</span></span>

|<span data-ttu-id="c718a-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="c718a-108">Element</span></span>|<span data-ttu-id="c718a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c718a-109">Description</span></span>|
|-------------|-----------------|
|[\<endpoint>](endpoint-of-client.md)|<span data-ttu-id="c718a-110">Contém uma coleção de elementos EndPoint que especificam os pontos de extremidade aos quais este cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="c718a-110">Contains a collection of endpoint elements that specify the endpoints that this client can connect to.</span></span>|
|[\<metadata>](metadata.md)|<span data-ttu-id="c718a-111">Contém configurações para processar metadados.</span><span class="sxs-lookup"><span data-stu-id="c718a-111">Contains settings for processing metadata.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c718a-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c718a-112">Parent Elements</span></span>

|<span data-ttu-id="c718a-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="c718a-113">Element</span></span>|<span data-ttu-id="c718a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c718a-114">Description</span></span>|
|-------------|-----------------|
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="c718a-115">O elemento raiz de todos os elementos de configuração de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c718a-115">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c718a-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="c718a-116">Remarks</span></span>

 <span data-ttu-id="c718a-117">A `client` seção define uma lista de pontos de extremidade aos quais um cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="c718a-117">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="c718a-118">Cada ponto de extremidade listado na seção cliente define sua própria associação, comportamento e contrato.</span><span class="sxs-lookup"><span data-stu-id="c718a-118">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="c718a-119">Ele é identificado exclusivamente pela combinação dos `name` `contract` atributos e.</span><span class="sxs-lookup"><span data-stu-id="c718a-119">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="c718a-120">O código do cliente especifica o `name` para se conectar a um ponto de extremidade para o serviço que o cliente implementa.</span><span class="sxs-lookup"><span data-stu-id="c718a-120">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="c718a-121">Se o `name` atributo for omitido, o ponto de extremidade atua como o ponto de extremidade padrão para o contrato que ele implementa.</span><span class="sxs-lookup"><span data-stu-id="c718a-121">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>

 <span data-ttu-id="c718a-122">Além disso, esta seção também especifica configurações para processar metadados.</span><span class="sxs-lookup"><span data-stu-id="c718a-122">In addition, this section also specifies settings for processing metadata.</span></span>

## <a name="example"></a><span data-ttu-id="c718a-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c718a-123">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c718a-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="c718a-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="c718a-125">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="c718a-125">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="c718a-126">Clientes</span><span class="sxs-lookup"><span data-stu-id="c718a-126">Clients</span></span>](../../../wcf/feature-details/clients.md)
