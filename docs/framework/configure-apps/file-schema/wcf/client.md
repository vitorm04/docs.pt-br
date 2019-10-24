---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 7aa3755be97a839cb576d53852b75cfe50e39276
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773940"
---
# <a name="client"></a><span data-ttu-id="ae1ab-101">\<client ></span><span class="sxs-lookup"><span data-stu-id="ae1ab-101">\<client></span></span>
<span data-ttu-id="ae1ab-102">O elemento `client` define uma lista de pontos de extremidade aos quais um cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="ae1ab-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>

<span data-ttu-id="ae1ab-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ae1ab-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ae1ab-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="ae1ab-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ae1ab-105">&nbsp; &nbsp; &nbsp; &nbsp; **\<client** ></span><span class="sxs-lookup"><span data-stu-id="ae1ab-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ae1ab-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae1ab-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="ae1ab-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ae1ab-107">Attributes and Elements</span></span>
 <span data-ttu-id="ae1ab-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ae1ab-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ae1ab-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="ae1ab-109">Attributes</span></span>
 <span data-ttu-id="ae1ab-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ae1ab-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="ae1ab-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ae1ab-111">Child Elements</span></span>

|<span data-ttu-id="ae1ab-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="ae1ab-112">Element</span></span>|<span data-ttu-id="ae1ab-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae1ab-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ae1ab-114">\<endpoint ></span><span class="sxs-lookup"><span data-stu-id="ae1ab-114">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="ae1ab-115">Contém uma coleção de elementos EndPoint que especificam os pontos de extremidade aos quais este cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="ae1ab-115">Contains a collection of endpoint elements that specify the endpoints that this client can connect to.</span></span>|
|[<span data-ttu-id="ae1ab-116">\<metadata ></span><span class="sxs-lookup"><span data-stu-id="ae1ab-116">\<metadata></span></span>](metadata.md)|<span data-ttu-id="ae1ab-117">Contém configurações para processar metadados.</span><span class="sxs-lookup"><span data-stu-id="ae1ab-117">Contains settings for processing metadata.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ae1ab-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ae1ab-118">Parent Elements</span></span>

|<span data-ttu-id="ae1ab-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="ae1ab-119">Element</span></span>|<span data-ttu-id="ae1ab-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae1ab-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ae1ab-121">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ae1ab-121">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="ae1ab-122">O elemento raiz de todos os elementos de configuração de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ae1ab-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ae1ab-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="ae1ab-123">Remarks</span></span>
 <span data-ttu-id="ae1ab-124">A seção `client` define uma lista de pontos de extremidade aos quais um cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="ae1ab-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="ae1ab-125">Cada ponto de extremidade listado na seção cliente define sua própria associação, comportamento e contrato.</span><span class="sxs-lookup"><span data-stu-id="ae1ab-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="ae1ab-126">Ele é identificado exclusivamente pela combinação dos atributos `name` e `contract`.</span><span class="sxs-lookup"><span data-stu-id="ae1ab-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="ae1ab-127">O código do cliente especifica o `name` para se conectar a um ponto de extremidade para o serviço que o cliente implementa.</span><span class="sxs-lookup"><span data-stu-id="ae1ab-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="ae1ab-128">Se o atributo `name` for omitido, o ponto de extremidade atuará como o ponto de extremidade padrão para o contrato que ele implementa.</span><span class="sxs-lookup"><span data-stu-id="ae1ab-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>

 <span data-ttu-id="ae1ab-129">Além disso, esta seção também especifica configurações para processar metadados.</span><span class="sxs-lookup"><span data-stu-id="ae1ab-129">In addition, this section also specifies settings for processing metadata.</span></span>

## <a name="example"></a><span data-ttu-id="ae1ab-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae1ab-130">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ae1ab-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae1ab-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="ae1ab-132">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="ae1ab-132">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="ae1ab-133">Clientes</span><span class="sxs-lookup"><span data-stu-id="ae1ab-133">Clients</span></span>](../../../wcf/feature-details/clients.md)
