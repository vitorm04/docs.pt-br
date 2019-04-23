---
title: <dataContractSerializer> of <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: c81fdb040f2e0d6c9a3728d8ed3b917443ecb42e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115356"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="57496-102">\<dataContractSerializer> of \<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="57496-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="57496-103">Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="57496-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="57496-104">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="57496-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="57496-105">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="57496-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57496-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57496-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57496-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="57496-107">Attributes and Elements</span></span>  
 <span data-ttu-id="57496-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="57496-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57496-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="57496-109">Attributes</span></span>  
  
|<span data-ttu-id="57496-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="57496-110">Element</span></span>|<span data-ttu-id="57496-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="57496-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57496-112">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="57496-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="57496-113">Um valor booliano que especifica se deve ignorar os dados fornecidos pelo ponto de extremidade quando ele está sendo serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="57496-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="57496-114">Esse atributo é configurável somente na `<dataContractSerializer>` sob o `<behavior>` elemento.</span><span class="sxs-lookup"><span data-stu-id="57496-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="57496-115">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="57496-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="57496-116">Um inteiro que especifica o número máximo de itens para serializar ou desserializar.</span><span class="sxs-lookup"><span data-stu-id="57496-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="57496-117">Esse atributo é 65536.</span><span class="sxs-lookup"><span data-stu-id="57496-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57496-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="57496-118">Child Elements</span></span>  
  
|<span data-ttu-id="57496-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="57496-119">Element</span></span>|<span data-ttu-id="57496-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="57496-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57496-121">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="57496-121">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="57496-122">Contém tipos conhecidos de que o <xref:System.Runtime.Serialization.DataContractSerializer> usa durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="57496-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="57496-123">Para obter mais informações sobre contratos de dados e tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="57496-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57496-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="57496-124">Parent Elements</span></span>  
  
|<span data-ttu-id="57496-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="57496-125">Element</span></span>|<span data-ttu-id="57496-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="57496-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57496-127">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="57496-127">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="57496-128">Representa o elemento raiz para o <xref:System.Runtime.Serialization> seção de namespace e contém elementos para configurar as opções do <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="57496-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57496-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="57496-129">Remarks</span></span>  
 <span data-ttu-id="57496-130">Para obter mais informações sobre tipos conhecidos, consulte <xref:System.Runtime.Serialization.DataContractSerializer> e [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="57496-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57496-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57496-131">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="57496-132">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="57496-132">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
