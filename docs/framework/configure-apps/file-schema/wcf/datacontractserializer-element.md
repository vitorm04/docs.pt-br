---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: b635f03d1e4a6628a76d678f7366482717276376
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116383"
---
# <a name="datacontractserializer"></a><span data-ttu-id="5f09c-101">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="5f09c-101">\<dataContractSerializer></span></span>
<span data-ttu-id="5f09c-102">Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5f09c-102">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="5f09c-103">Esse elemento ocorre em duas hierarquias diferentes.</span><span class="sxs-lookup"><span data-stu-id="5f09c-103">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="5f09c-104">Um está listado a seguinte seção de hierarquia de esquema e o outro está listado na seção comentários.</span><span class="sxs-lookup"><span data-stu-id="5f09c-104">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="5f09c-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5f09c-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="5f09c-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="5f09c-106">\<behaviors></span></span>  
<span data-ttu-id="5f09c-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5f09c-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="5f09c-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="5f09c-108">\<behavior></span></span>  
<span data-ttu-id="5f09c-109">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="5f09c-109">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f09c-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f09c-110">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f09c-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5f09c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5f09c-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5f09c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f09c-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="5f09c-113">Attributes</span></span>  
  
|<span data-ttu-id="5f09c-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="5f09c-114">Element</span></span>|<span data-ttu-id="5f09c-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f09c-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5f09c-116">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="5f09c-116">ignoreExtensionDataObject</span></span>|<span data-ttu-id="5f09c-117">Um valor booliano que especifica se deve ignorar os dados fornecidos pelo ponto de extremidade quando ele está sendo serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="5f09c-117">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="5f09c-118">Esse atributo é configurável somente na `<dataContractSerializer>` sob o `<behavior>` elemento.</span><span class="sxs-lookup"><span data-stu-id="5f09c-118">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="5f09c-119">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="5f09c-119">maxItemsInObjectGraph</span></span>|<span data-ttu-id="5f09c-120">Um inteiro que especifica o número máximo de itens para serializar ou desserializar.</span><span class="sxs-lookup"><span data-stu-id="5f09c-120">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="5f09c-121">Esse atributo é 65536.</span><span class="sxs-lookup"><span data-stu-id="5f09c-121">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f09c-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5f09c-122">Child Elements</span></span>  
 <span data-ttu-id="5f09c-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5f09c-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f09c-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5f09c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="5f09c-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="5f09c-125">Element</span></span>|<span data-ttu-id="5f09c-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f09c-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f09c-127">\<behavior></span><span class="sxs-lookup"><span data-stu-id="5f09c-127">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|<span data-ttu-id="5f09c-128">Uma coleção de configurações para o comportamento de um serviço.</span><span class="sxs-lookup"><span data-stu-id="5f09c-128">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="5f09c-129">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="5f09c-129">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="5f09c-130">Representa o elemento raiz para o <xref:System.Runtime.Serialization> seção de namespace e contém elementos para configurar as opções do <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5f09c-130">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f09c-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="5f09c-131">Remarks</span></span>  
 <span data-ttu-id="5f09c-132">Conforme mencionado na introdução deste tópico, isso é a segunda hierarquia na qual o \<X509Extension > elemento ocorre.</span><span class="sxs-lookup"><span data-stu-id="5f09c-132">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="5f09c-133">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="5f09c-133">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [<span data-ttu-id="5f09c-134">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="5f09c-134">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 <span data-ttu-id="5f09c-135">Para obter mais informações sobre tipos conhecidos, consulte <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5f09c-135">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f09c-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f09c-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="5f09c-137">Tipos de contratos de dados conhecidos</span><span class="sxs-lookup"><span data-stu-id="5f09c-137">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="5f09c-138">Serialização e transferência de dados</span><span class="sxs-lookup"><span data-stu-id="5f09c-138">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
