---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: 1b4fd959d5e522150751d2e9b8be8c5b2252bf27
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254942"
---
# <a name="datacontractserializer"></a><span data-ttu-id="81b07-101">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="81b07-101">\<dataContractSerializer></span></span>
<span data-ttu-id="81b07-102">Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="81b07-102">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="81b07-103">Esse elemento ocorre em duas hierarquias diferentes.</span><span class="sxs-lookup"><span data-stu-id="81b07-103">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="81b07-104">Um está listado a seguinte seção de hierarquia de esquema e o outro está listado na seção comentários.</span><span class="sxs-lookup"><span data-stu-id="81b07-104">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="81b07-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="81b07-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="81b07-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="81b07-106">\<behaviors></span></span>  
<span data-ttu-id="81b07-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="81b07-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="81b07-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="81b07-108">\<behavior></span></span>  
<span data-ttu-id="81b07-109">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="81b07-109">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81b07-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81b07-110">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81b07-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="81b07-111">Attributes and Elements</span></span>  
 <span data-ttu-id="81b07-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="81b07-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81b07-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="81b07-113">Attributes</span></span>  
  
|<span data-ttu-id="81b07-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="81b07-114">Element</span></span>|<span data-ttu-id="81b07-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="81b07-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81b07-116">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="81b07-116">ignoreExtensionDataObject</span></span>|<span data-ttu-id="81b07-117">Um valor booliano que especifica se deve ignorar os dados fornecidos pelo ponto de extremidade quando ele está sendo serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="81b07-117">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="81b07-118">Esse atributo é configurável somente na `<dataContractSerializer>` sob o `<behavior>` elemento.</span><span class="sxs-lookup"><span data-stu-id="81b07-118">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="81b07-119">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="81b07-119">maxItemsInObjectGraph</span></span>|<span data-ttu-id="81b07-120">Um inteiro que especifica o número máximo de itens para serializar ou desserializar.</span><span class="sxs-lookup"><span data-stu-id="81b07-120">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="81b07-121">Esse atributo é 65536.</span><span class="sxs-lookup"><span data-stu-id="81b07-121">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81b07-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="81b07-122">Child Elements</span></span>  
 <span data-ttu-id="81b07-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="81b07-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81b07-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="81b07-124">Parent Elements</span></span>  
  
|<span data-ttu-id="81b07-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="81b07-125">Element</span></span>|<span data-ttu-id="81b07-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="81b07-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81b07-127">\<behavior></span><span class="sxs-lookup"><span data-stu-id="81b07-127">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|<span data-ttu-id="81b07-128">Uma coleção de configurações para o comportamento de um serviço.</span><span class="sxs-lookup"><span data-stu-id="81b07-128">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="81b07-129">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="81b07-129">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="81b07-130">Representa o elemento raiz para o <xref:System.Runtime.Serialization> seção de namespace e contém elementos para configurar as opções do <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="81b07-130">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81b07-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="81b07-131">Remarks</span></span>  
 <span data-ttu-id="81b07-132">Conforme mencionado na introdução deste tópico, isso é a segunda hierarquia na qual o \<X509Extension > elemento ocorre.</span><span class="sxs-lookup"><span data-stu-id="81b07-132">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="81b07-133">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="81b07-133">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [<span data-ttu-id="81b07-134">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="81b07-134">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 <span data-ttu-id="81b07-135">Para obter mais informações sobre tipos conhecidos, consulte <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="81b07-135">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81b07-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81b07-136">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="81b07-137">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="81b07-137">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="81b07-138">Serialização e transferência de dados</span><span class="sxs-lookup"><span data-stu-id="81b07-138">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
