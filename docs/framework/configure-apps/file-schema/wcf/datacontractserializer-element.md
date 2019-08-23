---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: 7e440810fee1dddb7025d1385b1edb4838d98a39
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925920"
---
# <a name="datacontractserializer"></a><span data-ttu-id="832f8-101">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="832f8-101">\<dataContractSerializer></span></span>
<span data-ttu-id="832f8-102">Contém dados de configuração para <xref:System.Runtime.Serialization.DataContractSerializer>o.</span><span class="sxs-lookup"><span data-stu-id="832f8-102">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="832f8-103">Esse elemento ocorre em duas hierarquias diferentes.</span><span class="sxs-lookup"><span data-stu-id="832f8-103">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="832f8-104">Uma é listada na seção hierarquia de esquema a seguir e a outra é listada na seção comentários.</span><span class="sxs-lookup"><span data-stu-id="832f8-104">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="832f8-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="832f8-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="832f8-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="832f8-106">\<behaviors></span></span>  
<span data-ttu-id="832f8-107">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="832f8-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="832f8-108">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="832f8-108">\<behavior></span></span>  
<span data-ttu-id="832f8-109">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="832f8-109">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="832f8-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="832f8-110">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="832f8-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="832f8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="832f8-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="832f8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="832f8-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="832f8-113">Attributes</span></span>  
  
|<span data-ttu-id="832f8-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="832f8-114">Element</span></span>|<span data-ttu-id="832f8-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="832f8-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="832f8-116">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="832f8-116">ignoreExtensionDataObject</span></span>|<span data-ttu-id="832f8-117">Um valor booliano que especifica se é para ignorar os dados fornecidos pelo ponto de extremidade quando ele está sendo serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="832f8-117">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="832f8-118">Esse atributo é configurável somente no `<dataContractSerializer>` `<behavior>` elemento abaixo.</span><span class="sxs-lookup"><span data-stu-id="832f8-118">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="832f8-119">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="832f8-119">maxItemsInObjectGraph</span></span>|<span data-ttu-id="832f8-120">Um inteiro que especifica o número máximo de itens a serem serializados ou desserializados.</span><span class="sxs-lookup"><span data-stu-id="832f8-120">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="832f8-121">Esse atributo é 65536.</span><span class="sxs-lookup"><span data-stu-id="832f8-121">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="832f8-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="832f8-122">Child Elements</span></span>  
 <span data-ttu-id="832f8-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="832f8-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="832f8-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="832f8-124">Parent Elements</span></span>  
  
|<span data-ttu-id="832f8-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="832f8-125">Element</span></span>|<span data-ttu-id="832f8-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="832f8-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="832f8-127">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="832f8-127">\<behavior></span></span>](behavior-of-servicebehaviors.md)|<span data-ttu-id="832f8-128">Uma coleção de configurações para o comportamento de um serviço.</span><span class="sxs-lookup"><span data-stu-id="832f8-128">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="832f8-129">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="832f8-129">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)|<span data-ttu-id="832f8-130">Representa o elemento raiz da <xref:System.Runtime.Serialization> seção namespace e contém elementos para definir as opções <xref:System.Runtime.Serialization.DataContractSerializer>do.</span><span class="sxs-lookup"><span data-stu-id="832f8-130">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="832f8-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="832f8-131">Remarks</span></span>  
 <span data-ttu-id="832f8-132">Conforme indicado na introdução deste tópico, esta é a segunda hierarquia na qual o \<elemento de > X509Extension ocorre.</span><span class="sxs-lookup"><span data-stu-id="832f8-132">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="832f8-133">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="832f8-133">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)  
  
 [<span data-ttu-id="832f8-134">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="832f8-134">\<dataContractSerializer></span></span>](datacontractserializer-element.md)  
  
 <span data-ttu-id="832f8-135">Para obter mais informações sobre tipos conhecidos, <xref:System.Runtime.Serialization.DataContractSerializer>consulte.</span><span class="sxs-lookup"><span data-stu-id="832f8-135">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="832f8-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="832f8-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="832f8-137">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="832f8-137">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="832f8-138">Serialização e transferência de dados</span><span class="sxs-lookup"><span data-stu-id="832f8-138">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
