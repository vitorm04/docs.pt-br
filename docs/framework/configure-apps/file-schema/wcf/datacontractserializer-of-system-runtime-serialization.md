---
title: '&lt;dataContractSerializer&gt; of &lt;system.runtime.serialization&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e0c8d0e82696935a480935ebbb71530e052f8d8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdatacontractserializergt-of-ltsystemruntimeserializationgt"></a><span data-ttu-id="b016f-102">&lt;dataContractSerializer&gt; of &lt;system.runtime.serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="b016f-102">&lt;dataContractSerializer&gt; of &lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="b016f-103">Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b016f-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="b016f-104">\<Serialization ></span><span class="sxs-lookup"><span data-stu-id="b016f-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="b016f-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="b016f-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b016f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b016f-106">Syntax</span></span>  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer ignoreExtensionDataObject="Boolean"  
            maxItemsInObjectGraph="Integer">  
      <declaredTypes>  
        <add type="String">  
          <knownType type="String">  
             <parameter index="Integer"  
                        type="String" />  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b016f-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b016f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b016f-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b016f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b016f-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b016f-109">Attributes</span></span>  
  
|<span data-ttu-id="b016f-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="b016f-110">Element</span></span>|<span data-ttu-id="b016f-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="b016f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b016f-112">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="b016f-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="b016f-113">Um valor booleano que especifica se deve ignorar os dados fornecidos pelo ponto de extremidade quando ele está sendo serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="b016f-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="b016f-114">Esse atributo é configurável somente no `<dataContractSerializer>` sob o `<behavior>` elemento.</span><span class="sxs-lookup"><span data-stu-id="b016f-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="b016f-115">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="b016f-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="b016f-116">Um inteiro que especifica o número máximo de itens para serializar ou desserializar.</span><span class="sxs-lookup"><span data-stu-id="b016f-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="b016f-117">Esse atributo é 65536.</span><span class="sxs-lookup"><span data-stu-id="b016f-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b016f-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b016f-118">Child Elements</span></span>  
  
|<span data-ttu-id="b016f-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="b016f-119">Element</span></span>|<span data-ttu-id="b016f-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="b016f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b016f-121">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="b016f-121">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="b016f-122">Contém de tipos conhecidos que o <xref:System.Runtime.Serialization.DataContractSerializer> usa durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="b016f-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="b016f-123">Para obter mais informações sobre contratos de dados e tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="b016f-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b016f-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b016f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="b016f-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="b016f-125">Element</span></span>|<span data-ttu-id="b016f-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="b016f-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b016f-127">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="b016f-127">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="b016f-128">Representa o elemento raiz para o <xref:System.Runtime.Serialization> seção de namespace e contém elementos para configurar as opções do <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b016f-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b016f-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="b016f-129">Remarks</span></span>  
 <span data-ttu-id="b016f-130">Para obter mais informações sobre tipos conhecidos, consulte <xref:System.Runtime.Serialization.DataContractSerializer> e [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="b016f-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b016f-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b016f-131">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 [<span data-ttu-id="b016f-132">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="b016f-132">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
