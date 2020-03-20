---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: c93a1f482882cc8cd9d229d82597efa64ba209bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152964"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="18718-102">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="18718-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="18718-103">Representa o elemento raiz <xref:System.Runtime.Serialization> para a seção namespace <xref:System.Runtime.Serialization.DataContractSerializer>e contém elementos para definir as opções do .</span><span class="sxs-lookup"><span data-stu-id="18718-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

<span data-ttu-id="18718-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="18718-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="18718-105">&nbsp;&nbsp;**\<system.runtime.serialização>**</span><span class="sxs-lookup"><span data-stu-id="18718-105">&nbsp;&nbsp;**\<system.runtime.serialization>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18718-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="18718-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18718-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="18718-107">Attributes and Elements</span></span>  
 <span data-ttu-id="18718-108">As seções a seguir descrevem atributos, elementos da criança e elementos dos pais</span><span class="sxs-lookup"><span data-stu-id="18718-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18718-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="18718-109">Attributes</span></span>  
 <span data-ttu-id="18718-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="18718-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="18718-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="18718-111">Child Elements</span></span>  
  
|<span data-ttu-id="18718-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="18718-112">Element</span></span>|<span data-ttu-id="18718-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="18718-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18718-114">\<>de dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="18718-114">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="18718-115">Permite que a adição de tipos conhecidos seja usada quando a desserialização.</span><span class="sxs-lookup"><span data-stu-id="18718-115">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="18718-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="18718-116">Parent Elements</span></span>  
  
|<span data-ttu-id="18718-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="18718-117">Element</span></span>|<span data-ttu-id="18718-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="18718-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18718-119">\<elemento> de configuração</span><span class="sxs-lookup"><span data-stu-id="18718-119">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="18718-120">O elemento de nível superior para configuração.</span><span class="sxs-lookup"><span data-stu-id="18718-120">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="18718-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="18718-121">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="18718-122">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="18718-122">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="18718-123">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="18718-123">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
