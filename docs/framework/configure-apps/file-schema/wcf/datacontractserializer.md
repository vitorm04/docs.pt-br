---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: e6524c18780c062c3b5b7dfc2509449cb208e270
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400440"
---
# <a name="datacontractserializer"></a><span data-ttu-id="02fcb-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="02fcb-102">dataContractSerializer</span></span>
<span data-ttu-id="02fcb-103">Contém dados de configuração para <xref:System.Runtime.Serialization.DataContractSerializer>o.</span><span class="sxs-lookup"><span data-stu-id="02fcb-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
<span data-ttu-id="02fcb-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="02fcb-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="02fcb-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="02fcb-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="02fcb-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="02fcb-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="02fcb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="02fcb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="02fcb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="02fcb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="02fcb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> do dataContractSerializer**</span><span class="sxs-lookup"><span data-stu-id="02fcb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02fcb-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02fcb-110">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02fcb-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="02fcb-111">Attributes and Elements</span></span>  
 <span data-ttu-id="02fcb-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="02fcb-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02fcb-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="02fcb-113">Attributes</span></span>  
  
|<span data-ttu-id="02fcb-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="02fcb-114">Element</span></span>|<span data-ttu-id="02fcb-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="02fcb-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="02fcb-116">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="02fcb-116">ignoreExtensionDataObject</span></span>|<span data-ttu-id="02fcb-117">Um valor booliano que especifica se os dados fornecidos pelo ponto de extremidade devem ser ignorados, quando ele está sendo serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="02fcb-117">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="02fcb-118">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="02fcb-118">maxItemsInObjectGraph</span></span>|<span data-ttu-id="02fcb-119">Um inteiro que especifica o número máximo de itens a serem serializados ou desserializados.</span><span class="sxs-lookup"><span data-stu-id="02fcb-119">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02fcb-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="02fcb-120">Child Elements</span></span>  
 <span data-ttu-id="02fcb-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="02fcb-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="02fcb-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="02fcb-122">Parent Elements</span></span>  
  
|<span data-ttu-id="02fcb-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="02fcb-123">Element</span></span>|<span data-ttu-id="02fcb-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="02fcb-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02fcb-125">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="02fcb-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="02fcb-126">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="02fcb-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02fcb-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="02fcb-127">Remarks</span></span>  
 <span data-ttu-id="02fcb-128">Consulte a <xref:System.Runtime.Serialization.DataContractSerializer> documentação para obter mais informações sobre tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="02fcb-128">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="02fcb-129">O `<dataContractSerializer>` elemento Behavior (se presente) sempre deve aparecer antes do `<enableWebScript>` elemento Behavior no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="02fcb-129">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="02fcb-130">Caso contrário, o comportamento resultante será indefinido.</span><span class="sxs-lookup"><span data-stu-id="02fcb-130">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02fcb-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02fcb-131">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="02fcb-132">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="02fcb-132">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="02fcb-133">Serialização e transferência de dados</span><span class="sxs-lookup"><span data-stu-id="02fcb-133">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
