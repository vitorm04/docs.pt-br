---
title: '&lt;dataContractSerializer&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d38e3786c595c3fe6cc9ea54b68784c927901731
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltdatacontractserializergt"></a><span data-ttu-id="28ee3-102">&lt;dataContractSerializer&gt;</span><span class="sxs-lookup"><span data-stu-id="28ee3-102">&lt;dataContractSerializer&gt;</span></span>
<span data-ttu-id="28ee3-103">Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="28ee3-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="28ee3-104">Esse elemento ocorre em duas hierarquias diferentes.</span><span class="sxs-lookup"><span data-stu-id="28ee3-104">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="28ee3-105">Um é listado a seguinte seção de hierarquia de esquema e o outro está listado na seção comentários.</span><span class="sxs-lookup"><span data-stu-id="28ee3-105">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="28ee3-106">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="28ee3-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="28ee3-107">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="28ee3-107">\<behaviors></span></span>  
<span data-ttu-id="28ee3-108">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="28ee3-108">\<serviceBehaviors></span></span>  
<span data-ttu-id="28ee3-109">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="28ee3-109">\<behavior></span></span>  
<span data-ttu-id="28ee3-110">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="28ee3-110">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28ee3-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28ee3-111">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"  
   maxItemsInObjectGraph="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28ee3-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="28ee3-112">Attributes and Elements</span></span>  
 <span data-ttu-id="28ee3-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="28ee3-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28ee3-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="28ee3-114">Attributes</span></span>  
  
|<span data-ttu-id="28ee3-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="28ee3-115">Element</span></span>|<span data-ttu-id="28ee3-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="28ee3-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="28ee3-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="28ee3-117">ignoreExtensionDataObject</span></span>|<span data-ttu-id="28ee3-118">Um valor booleano que especifica se deve ignorar os dados fornecidos pelo ponto de extremidade quando ele está sendo serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="28ee3-118">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="28ee3-119">Esse atributo é configurável somente no `<dataContractSerializer>` sob o `<behavior>` elemento.</span><span class="sxs-lookup"><span data-stu-id="28ee3-119">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="28ee3-120">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="28ee3-120">maxItemsInObjectGraph</span></span>|<span data-ttu-id="28ee3-121">Um inteiro que especifica o número máximo de itens para serializar ou desserializar.</span><span class="sxs-lookup"><span data-stu-id="28ee3-121">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="28ee3-122">Esse atributo é 65536.</span><span class="sxs-lookup"><span data-stu-id="28ee3-122">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28ee3-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="28ee3-123">Child Elements</span></span>  
 <span data-ttu-id="28ee3-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="28ee3-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="28ee3-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="28ee3-125">Parent Elements</span></span>  
  
|<span data-ttu-id="28ee3-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="28ee3-126">Element</span></span>|<span data-ttu-id="28ee3-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="28ee3-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28ee3-128">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="28ee3-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|<span data-ttu-id="28ee3-129">Uma coleção de configurações para o comportamento de um serviço.</span><span class="sxs-lookup"><span data-stu-id="28ee3-129">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="28ee3-130">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="28ee3-130">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="28ee3-131">Representa o elemento raiz para o <xref:System.Runtime.Serialization> seção de namespace e contém elementos para configurar as opções do <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="28ee3-131">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28ee3-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="28ee3-132">Remarks</span></span>  
 <span data-ttu-id="28ee3-133">Conforme mencionado na introdução deste tópico, este é a segunda hierarquia na qual o \<X509Extension > elemento ocorre.</span><span class="sxs-lookup"><span data-stu-id="28ee3-133">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="28ee3-134">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="28ee3-134">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [<span data-ttu-id="28ee3-135">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="28ee3-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 <span data-ttu-id="28ee3-136">Para obter mais informações sobre tipos conhecidos, consulte <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="28ee3-136">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28ee3-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28ee3-137">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [<span data-ttu-id="28ee3-138">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="28ee3-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="28ee3-139">Serialização e transferência de dados</span><span class="sxs-lookup"><span data-stu-id="28ee3-139">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
