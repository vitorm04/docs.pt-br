---
title: <dataContractSerializer> de <System. Runtime. Serialization>
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: a8d379e7a37bca0cdb58836a6afdf814320e2411
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190183"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="c9ad2-102">\<dataContractSerializer> de \<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="c9ad2-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>

<span data-ttu-id="c9ad2-103">Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="c9ad2-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="c9ad2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9ad2-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9ad2-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c9ad2-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c9ad2-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c9ad2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9ad2-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="c9ad2-107">Attributes</span></span>  
  
|<span data-ttu-id="c9ad2-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="c9ad2-108">Element</span></span>|<span data-ttu-id="c9ad2-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9ad2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9ad2-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="c9ad2-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="c9ad2-111">Um valor booliano que especifica se é para ignorar os dados fornecidos pelo ponto de extremidade quando ele está sendo serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="c9ad2-111">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="c9ad2-112">Esse atributo é configurável somente no `<dataContractSerializer>` `<behavior>` elemento abaixo.</span><span class="sxs-lookup"><span data-stu-id="c9ad2-112">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="c9ad2-113">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="c9ad2-113">maxItemsInObjectGraph</span></span>|<span data-ttu-id="c9ad2-114">Um inteiro que especifica o número máximo de itens a serem serializados ou desserializados.</span><span class="sxs-lookup"><span data-stu-id="c9ad2-114">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="c9ad2-115">Esse atributo é 65536.</span><span class="sxs-lookup"><span data-stu-id="c9ad2-115">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9ad2-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c9ad2-116">Child Elements</span></span>  
  
|<span data-ttu-id="c9ad2-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="c9ad2-117">Element</span></span>|<span data-ttu-id="c9ad2-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9ad2-118">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="c9ad2-119">Contém os tipos conhecidos que o <xref:System.Runtime.Serialization.DataContractSerializer> usa ao desserializar.</span><span class="sxs-lookup"><span data-stu-id="c9ad2-119">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="c9ad2-120">Para obter mais informações sobre contratos de dados e tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="c9ad2-120">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c9ad2-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c9ad2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c9ad2-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="c9ad2-122">Element</span></span>|<span data-ttu-id="c9ad2-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9ad2-123">Description</span></span>|  
|-------------|-----------------|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="c9ad2-124">Representa o elemento raiz da <xref:System.Runtime.Serialization> seção namespace e contém elementos para definir as opções do <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="c9ad2-124">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9ad2-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9ad2-125">Remarks</span></span>  

 <span data-ttu-id="c9ad2-126">Para obter mais informações sobre tipos conhecidos, consulte <xref:System.Runtime.Serialization.DataContractSerializer> e [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="c9ad2-126">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9ad2-127">Veja também</span><span class="sxs-lookup"><span data-stu-id="c9ad2-127">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="c9ad2-128">Tipos de contratos de dados conhecidos</span><span class="sxs-lookup"><span data-stu-id="c9ad2-128">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
