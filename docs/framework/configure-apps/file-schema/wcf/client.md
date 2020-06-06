---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 7aa3755be97a839cb576d53852b75cfe50e39276
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "72773940"
---
# \<client>
<span data-ttu-id="29e8d-101">O `client` elemento define uma lista de pontos de extremidade aos quais um cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="29e8d-101">The `client` element defines a list of endpoints that a client can connect to.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**

## <a name="syntax"></a><span data-ttu-id="29e8d-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29e8d-102">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="29e8d-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="29e8d-103">Attributes and Elements</span></span>
 <span data-ttu-id="29e8d-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="29e8d-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="29e8d-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="29e8d-105">Attributes</span></span>
 <span data-ttu-id="29e8d-106">Nenhum</span><span class="sxs-lookup"><span data-stu-id="29e8d-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="29e8d-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="29e8d-107">Child Elements</span></span>

|<span data-ttu-id="29e8d-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="29e8d-108">Element</span></span>|<span data-ttu-id="29e8d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="29e8d-109">Description</span></span>|
|-------------|-----------------|
|[\<endpoint>](endpoint-of-client.md)|<span data-ttu-id="29e8d-110">Contém uma coleção de elementos EndPoint que especificam os pontos de extremidade aos quais este cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="29e8d-110">Contains a collection of endpoint elements that specify the endpoints that this client can connect to.</span></span>|
|[\<metadata>](metadata.md)|<span data-ttu-id="29e8d-111">Contém configurações para processar metadados.</span><span class="sxs-lookup"><span data-stu-id="29e8d-111">Contains settings for processing metadata.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="29e8d-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="29e8d-112">Parent Elements</span></span>

|<span data-ttu-id="29e8d-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="29e8d-113">Element</span></span>|<span data-ttu-id="29e8d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="29e8d-114">Description</span></span>|
|-------------|-----------------|
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="29e8d-115">O elemento raiz de todos os elementos de configuração de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="29e8d-115">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="29e8d-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="29e8d-116">Remarks</span></span>
 <span data-ttu-id="29e8d-117">A `client` seção define uma lista de pontos de extremidade aos quais um cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="29e8d-117">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="29e8d-118">Cada ponto de extremidade listado na seção cliente define sua própria associação, comportamento e contrato.</span><span class="sxs-lookup"><span data-stu-id="29e8d-118">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="29e8d-119">Ele é identificado exclusivamente pela combinação dos `name` `contract` atributos e.</span><span class="sxs-lookup"><span data-stu-id="29e8d-119">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="29e8d-120">O código do cliente especifica o `name` para se conectar a um ponto de extremidade para o serviço que o cliente implementa.</span><span class="sxs-lookup"><span data-stu-id="29e8d-120">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="29e8d-121">Se o `name` atributo for omitido, o ponto de extremidade atua como o ponto de extremidade padrão para o contrato que ele implementa.</span><span class="sxs-lookup"><span data-stu-id="29e8d-121">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>

 <span data-ttu-id="29e8d-122">Além disso, esta seção também especifica configurações para processar metadados.</span><span class="sxs-lookup"><span data-stu-id="29e8d-122">In addition, this section also specifies settings for processing metadata.</span></span>

## <a name="example"></a><span data-ttu-id="29e8d-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="29e8d-123">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="29e8d-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="29e8d-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="29e8d-125">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="29e8d-125">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="29e8d-126">Clientes</span><span class="sxs-lookup"><span data-stu-id="29e8d-126">Clients</span></span>](../../../wcf/feature-details/clients.md)
