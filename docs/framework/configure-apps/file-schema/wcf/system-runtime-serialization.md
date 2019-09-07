---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: b67f51e634d1294830690dad8c8cffb1fc9a6cd2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399457"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="f88f7-102">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="f88f7-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="f88f7-103">Representa o elemento raiz da <xref:System.Runtime.Serialization> seção namespace e contém elementos para definir as opções <xref:System.Runtime.Serialization.DataContractSerializer>do.</span><span class="sxs-lookup"><span data-stu-id="f88f7-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

<span data-ttu-id="f88f7-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f88f7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f88f7-105">&nbsp;&nbsp; **\<> System. Runtime. Serialization**</span><span class="sxs-lookup"><span data-stu-id="f88f7-105">&nbsp;&nbsp;**\<system.runtime.serialization>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f88f7-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f88f7-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f88f7-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f88f7-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f88f7-108">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="f88f7-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f88f7-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f88f7-109">Attributes</span></span>  
 <span data-ttu-id="f88f7-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f88f7-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f88f7-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f88f7-111">Child Elements</span></span>  
  
|<span data-ttu-id="f88f7-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="f88f7-112">Element</span></span>|<span data-ttu-id="f88f7-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f88f7-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f88f7-114">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="f88f7-114">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="f88f7-115">Permite que a adição de tipos conhecidos seja usada na desserialização.</span><span class="sxs-lookup"><span data-stu-id="f88f7-115">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f88f7-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f88f7-116">Parent Elements</span></span>  
  
|<span data-ttu-id="f88f7-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="f88f7-117">Element</span></span>|<span data-ttu-id="f88f7-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="f88f7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f88f7-119">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="f88f7-119">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="f88f7-120">O elemento de nível superior para configuração.</span><span class="sxs-lookup"><span data-stu-id="f88f7-120">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f88f7-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f88f7-121">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="f88f7-122">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="f88f7-122">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="f88f7-123">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="f88f7-123">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
 