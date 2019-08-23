---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: 4ec5cd19ccdc5c21a3caf426520d51442dc5ab3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938932"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="fbb53-102">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="fbb53-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="fbb53-103">Representa o elemento raiz da <xref:System.Runtime.Serialization> seção namespace e contém elementos para definir as opções <xref:System.Runtime.Serialization.DataContractSerializer>do.</span><span class="sxs-lookup"><span data-stu-id="fbb53-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="fbb53-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="fbb53-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbb53-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbb53-105">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbb53-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fbb53-106">Attributes and Elements</span></span>  
 <span data-ttu-id="fbb53-107">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="fbb53-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbb53-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="fbb53-108">Attributes</span></span>  
 <span data-ttu-id="fbb53-109">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fbb53-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fbb53-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fbb53-110">Child Elements</span></span>  
  
|<span data-ttu-id="fbb53-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="fbb53-111">Element</span></span>|<span data-ttu-id="fbb53-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="fbb53-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fbb53-113">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="fbb53-113">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="fbb53-114">Permite que a adição de tipos conhecidos seja usada na desserialização.</span><span class="sxs-lookup"><span data-stu-id="fbb53-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fbb53-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fbb53-115">Parent Elements</span></span>  
  
|<span data-ttu-id="fbb53-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="fbb53-116">Element</span></span>|<span data-ttu-id="fbb53-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="fbb53-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fbb53-118">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="fbb53-118">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="fbb53-119">O elemento de nível superior para configuração.</span><span class="sxs-lookup"><span data-stu-id="fbb53-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fbb53-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbb53-120">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="fbb53-121">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="fbb53-121">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="fbb53-122">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="fbb53-122">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
