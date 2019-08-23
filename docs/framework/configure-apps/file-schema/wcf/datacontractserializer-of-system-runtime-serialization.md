---
title: <dataContractSerializer>de < System. Runtime. Serialization >
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: 380d9ba5b8407d78b5045fd34fcdf37c0818d6f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919346"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="dec77-102">\<> DataContractSerializer do \<System. Runtime. Serialization ></span><span class="sxs-lookup"><span data-stu-id="dec77-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="dec77-103">Contém dados de configuração para <xref:System.Runtime.Serialization.DataContractSerializer>o.</span><span class="sxs-lookup"><span data-stu-id="dec77-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="dec77-104">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="dec77-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="dec77-105">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="dec77-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dec77-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dec77-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dec77-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dec77-107">Attributes and Elements</span></span>  
 <span data-ttu-id="dec77-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dec77-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dec77-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="dec77-109">Attributes</span></span>  
  
|<span data-ttu-id="dec77-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="dec77-110">Element</span></span>|<span data-ttu-id="dec77-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="dec77-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dec77-112">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="dec77-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="dec77-113">Um valor booliano que especifica se é para ignorar os dados fornecidos pelo ponto de extremidade quando ele está sendo serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="dec77-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="dec77-114">Esse atributo é configurável somente no `<dataContractSerializer>` `<behavior>` elemento abaixo.</span><span class="sxs-lookup"><span data-stu-id="dec77-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="dec77-115">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="dec77-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="dec77-116">Um inteiro que especifica o número máximo de itens a serem serializados ou desserializados.</span><span class="sxs-lookup"><span data-stu-id="dec77-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="dec77-117">Esse atributo é 65536.</span><span class="sxs-lookup"><span data-stu-id="dec77-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dec77-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dec77-118">Child Elements</span></span>  
  
|<span data-ttu-id="dec77-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="dec77-119">Element</span></span>|<span data-ttu-id="dec77-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="dec77-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dec77-121">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="dec77-121">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="dec77-122">Contém os tipos conhecidos que o <xref:System.Runtime.Serialization.DataContractSerializer> usa ao desserializar.</span><span class="sxs-lookup"><span data-stu-id="dec77-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="dec77-123">Para obter mais informações sobre contratos de dados e tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="dec77-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dec77-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dec77-124">Parent Elements</span></span>  
  
|<span data-ttu-id="dec77-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="dec77-125">Element</span></span>|<span data-ttu-id="dec77-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="dec77-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dec77-127">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="dec77-127">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)|<span data-ttu-id="dec77-128">Representa o elemento raiz da <xref:System.Runtime.Serialization> seção namespace e contém elementos para definir as opções <xref:System.Runtime.Serialization.DataContractSerializer>do.</span><span class="sxs-lookup"><span data-stu-id="dec77-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dec77-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="dec77-129">Remarks</span></span>  
 <span data-ttu-id="dec77-130">Para obter mais informações sobre tipos conhecidos, <xref:System.Runtime.Serialization.DataContractSerializer> consulte e [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="dec77-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dec77-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dec77-131">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="dec77-132">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="dec77-132">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
