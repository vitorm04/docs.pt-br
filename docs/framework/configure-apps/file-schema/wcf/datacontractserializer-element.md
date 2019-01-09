---
title: '&lt;DataContractSerializer&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: c79c8e8db2a4ea4526000bcbe336d1e664f9c4c2
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150949"
---
# <a name="ltdatacontractserializergt"></a><span data-ttu-id="21e81-102">&lt;DataContractSerializer&gt;</span><span class="sxs-lookup"><span data-stu-id="21e81-102">&lt;dataContractSerializer&gt;</span></span>
<span data-ttu-id="21e81-103">Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="21e81-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="21e81-104">Esse elemento ocorre em duas hierarquias diferentes.</span><span class="sxs-lookup"><span data-stu-id="21e81-104">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="21e81-105">Um está listado a seguinte seção de hierarquia de esquema e o outro está listado na seção comentários.</span><span class="sxs-lookup"><span data-stu-id="21e81-105">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="21e81-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="21e81-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="21e81-107">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="21e81-107">\<behaviors></span></span>  
<span data-ttu-id="21e81-108">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="21e81-108">\<serviceBehaviors></span></span>  
<span data-ttu-id="21e81-109">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="21e81-109">\<behavior></span></span>  
<span data-ttu-id="21e81-110">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="21e81-110">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21e81-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="21e81-111">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21e81-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="21e81-112">Attributes and Elements</span></span>  
 <span data-ttu-id="21e81-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="21e81-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21e81-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="21e81-114">Attributes</span></span>  
  
|<span data-ttu-id="21e81-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="21e81-115">Element</span></span>|<span data-ttu-id="21e81-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="21e81-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21e81-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="21e81-117">ignoreExtensionDataObject</span></span>|<span data-ttu-id="21e81-118">Um valor booliano que especifica se deve ignorar os dados fornecidos pelo ponto de extremidade quando ele está sendo serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="21e81-118">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="21e81-119">Esse atributo é configurável somente na `<dataContractSerializer>` sob o `<behavior>` elemento.</span><span class="sxs-lookup"><span data-stu-id="21e81-119">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="21e81-120">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="21e81-120">maxItemsInObjectGraph</span></span>|<span data-ttu-id="21e81-121">Um inteiro que especifica o número máximo de itens para serializar ou desserializar.</span><span class="sxs-lookup"><span data-stu-id="21e81-121">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="21e81-122">Esse atributo é 65536.</span><span class="sxs-lookup"><span data-stu-id="21e81-122">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21e81-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="21e81-123">Child Elements</span></span>  
 <span data-ttu-id="21e81-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="21e81-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="21e81-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="21e81-125">Parent Elements</span></span>  
  
|<span data-ttu-id="21e81-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="21e81-126">Element</span></span>|<span data-ttu-id="21e81-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="21e81-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21e81-128">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="21e81-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|<span data-ttu-id="21e81-129">Uma coleção de configurações para o comportamento de um serviço.</span><span class="sxs-lookup"><span data-stu-id="21e81-129">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="21e81-130">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="21e81-130">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="21e81-131">Representa o elemento raiz para o <xref:System.Runtime.Serialization> seção de namespace e contém elementos para configurar as opções do <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="21e81-131">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21e81-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="21e81-132">Remarks</span></span>  
 <span data-ttu-id="21e81-133">Conforme mencionado na introdução deste tópico, isso é a segunda hierarquia na qual o \<X509Extension > elemento ocorre.</span><span class="sxs-lookup"><span data-stu-id="21e81-133">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="21e81-134">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="21e81-134">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [<span data-ttu-id="21e81-135">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="21e81-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 <span data-ttu-id="21e81-136">Para obter mais informações sobre tipos conhecidos, consulte <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="21e81-136">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e81-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21e81-137">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [<span data-ttu-id="21e81-138">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="21e81-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="21e81-139">Serialização e transferência de dados</span><span class="sxs-lookup"><span data-stu-id="21e81-139">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
