---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: 84ced06691ce3b3c9c9573fc9d114335096a849d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157103"
---
# \<system.runtime.serialization>

<span data-ttu-id="32c34-102">Representa o elemento raiz da <xref:System.Runtime.Serialization> seção namespace e contém elementos para definir as opções do <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="32c34-102">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.serialization>**  
  
## <a name="syntax"></a><span data-ttu-id="32c34-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="32c34-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32c34-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="32c34-104">Attributes and Elements</span></span>  

 <span data-ttu-id="32c34-105">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="32c34-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32c34-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="32c34-106">Attributes</span></span>  

 <span data-ttu-id="32c34-107">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="32c34-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="32c34-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="32c34-108">Child Elements</span></span>  
  
|<span data-ttu-id="32c34-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="32c34-109">Element</span></span>|<span data-ttu-id="32c34-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="32c34-110">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="32c34-111">Permite que a adição de tipos conhecidos seja usada na desserialização.</span><span class="sxs-lookup"><span data-stu-id="32c34-111">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32c34-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="32c34-112">Parent Elements</span></span>  
  
|<span data-ttu-id="32c34-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="32c34-113">Element</span></span>|<span data-ttu-id="32c34-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="32c34-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32c34-115">\<configuration> Elementos</span><span class="sxs-lookup"><span data-stu-id="32c34-115">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="32c34-116">O elemento de nível superior para configuração.</span><span class="sxs-lookup"><span data-stu-id="32c34-116">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32c34-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="32c34-117">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="32c34-118">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="32c34-118">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="32c34-119">Tipos de contratos de dados conhecidos</span><span class="sxs-lookup"><span data-stu-id="32c34-119">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
