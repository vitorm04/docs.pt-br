---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: e24dae47171f741af064ca2eaa822928690acf6e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400446"
---
# <a name="datacontractserializer"></a><span data-ttu-id="105dc-101">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="105dc-101">\<dataContractSerializer></span></span>
<span data-ttu-id="105dc-102">Contém dados de configuração para <xref:System.Runtime.Serialization.DataContractSerializer>o.</span><span class="sxs-lookup"><span data-stu-id="105dc-102">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="105dc-103">Esse elemento ocorre em duas hierarquias diferentes.</span><span class="sxs-lookup"><span data-stu-id="105dc-103">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="105dc-104">Uma é listada na seção hierarquia de esquema a seguir e a outra é listada na seção comentários.</span><span class="sxs-lookup"><span data-stu-id="105dc-104">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
<span data-ttu-id="105dc-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="105dc-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="105dc-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="105dc-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="105dc-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="105dc-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="105dc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="105dc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="105dc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="105dc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="105dc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> do dataContractSerializer**</span><span class="sxs-lookup"><span data-stu-id="105dc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="105dc-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="105dc-111">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="105dc-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="105dc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="105dc-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="105dc-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="105dc-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="105dc-114">Attributes</span></span>  
  
|<span data-ttu-id="105dc-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="105dc-115">Element</span></span>|<span data-ttu-id="105dc-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="105dc-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="105dc-117">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="105dc-117">ignoreExtensionDataObject</span></span>|<span data-ttu-id="105dc-118">Um valor booliano que especifica se é para ignorar os dados fornecidos pelo ponto de extremidade quando ele está sendo serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="105dc-118">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="105dc-119">Esse atributo é configurável somente no `<dataContractSerializer>` `<behavior>` elemento abaixo.</span><span class="sxs-lookup"><span data-stu-id="105dc-119">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="105dc-120">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="105dc-120">maxItemsInObjectGraph</span></span>|<span data-ttu-id="105dc-121">Um inteiro que especifica o número máximo de itens a serem serializados ou desserializados.</span><span class="sxs-lookup"><span data-stu-id="105dc-121">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="105dc-122">Esse atributo é 65536.</span><span class="sxs-lookup"><span data-stu-id="105dc-122">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="105dc-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="105dc-123">Child Elements</span></span>  
 <span data-ttu-id="105dc-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="105dc-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="105dc-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="105dc-125">Parent Elements</span></span>  
  
|<span data-ttu-id="105dc-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="105dc-126">Element</span></span>|<span data-ttu-id="105dc-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="105dc-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="105dc-128">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="105dc-128">\<behavior></span></span>](behavior-of-servicebehaviors.md)|<span data-ttu-id="105dc-129">Uma coleção de configurações para o comportamento de um serviço.</span><span class="sxs-lookup"><span data-stu-id="105dc-129">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="105dc-130">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="105dc-130">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)|<span data-ttu-id="105dc-131">Representa o elemento raiz da <xref:System.Runtime.Serialization> seção namespace e contém elementos para definir as opções <xref:System.Runtime.Serialization.DataContractSerializer>do.</span><span class="sxs-lookup"><span data-stu-id="105dc-131">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="105dc-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="105dc-132">Remarks</span></span>  
 <span data-ttu-id="105dc-133">Conforme indicado na introdução deste tópico, esta é a segunda hierarquia na qual o \<elemento de > X509Extension ocorre.</span><span class="sxs-lookup"><span data-stu-id="105dc-133">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="105dc-134">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="105dc-134">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)  
  
 [<span data-ttu-id="105dc-135">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="105dc-135">\<dataContractSerializer></span></span>](datacontractserializer-element.md)  
  
 <span data-ttu-id="105dc-136">Para obter mais informações sobre tipos conhecidos, <xref:System.Runtime.Serialization.DataContractSerializer>consulte.</span><span class="sxs-lookup"><span data-stu-id="105dc-136">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="105dc-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="105dc-137">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="105dc-138">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="105dc-138">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="105dc-139">Serialização e transferência de dados</span><span class="sxs-lookup"><span data-stu-id="105dc-139">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
