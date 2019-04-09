---
title: <dataContractSerializer> of <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: c81fdb040f2e0d6c9a3728d8ed3b917443ecb42e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115356"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="f91fd-102">\<dataContractSerializer> of \<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="f91fd-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="f91fd-103">Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f91fd-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="f91fd-104">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="f91fd-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="f91fd-105">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="f91fd-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f91fd-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f91fd-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f91fd-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f91fd-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f91fd-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f91fd-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f91fd-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f91fd-109">Attributes</span></span>  
  
|<span data-ttu-id="f91fd-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="f91fd-110">Element</span></span>|<span data-ttu-id="f91fd-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f91fd-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f91fd-112">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="f91fd-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="f91fd-113">Um valor booliano que especifica se deve ignorar os dados fornecidos pelo ponto de extremidade quando ele está sendo serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="f91fd-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="f91fd-114">Esse atributo é configurável somente na `<dataContractSerializer>` sob o `<behavior>` elemento.</span><span class="sxs-lookup"><span data-stu-id="f91fd-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="f91fd-115">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="f91fd-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="f91fd-116">Um inteiro que especifica o número máximo de itens para serializar ou desserializar.</span><span class="sxs-lookup"><span data-stu-id="f91fd-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="f91fd-117">Esse atributo é 65536.</span><span class="sxs-lookup"><span data-stu-id="f91fd-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f91fd-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f91fd-118">Child Elements</span></span>  
  
|<span data-ttu-id="f91fd-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="f91fd-119">Element</span></span>|<span data-ttu-id="f91fd-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="f91fd-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f91fd-121">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="f91fd-121">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="f91fd-122">Contém tipos conhecidos de que o <xref:System.Runtime.Serialization.DataContractSerializer> usa durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="f91fd-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="f91fd-123">Para obter mais informações sobre contratos de dados e tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="f91fd-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f91fd-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f91fd-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f91fd-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="f91fd-125">Element</span></span>|<span data-ttu-id="f91fd-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="f91fd-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f91fd-127">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="f91fd-127">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="f91fd-128">Representa o elemento raiz para o <xref:System.Runtime.Serialization> seção de namespace e contém elementos para configurar as opções do <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f91fd-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f91fd-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="f91fd-129">Remarks</span></span>  
 <span data-ttu-id="f91fd-130">Para obter mais informações sobre tipos conhecidos, consulte <xref:System.Runtime.Serialization.DataContractSerializer> e [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="f91fd-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f91fd-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f91fd-131">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="f91fd-132">Tipos de contratos de dados conhecidos</span><span class="sxs-lookup"><span data-stu-id="f91fd-132">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
