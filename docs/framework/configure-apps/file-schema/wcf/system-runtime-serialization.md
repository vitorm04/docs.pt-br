---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: c34eba2614a354f1753d8da077f8653f2c260a97
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165874"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="d25cf-102">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="d25cf-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="d25cf-103">Representa o elemento raiz para o <xref:System.Runtime.Serialization> seção de namespace e contém elementos para configurar as opções do <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="d25cf-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="d25cf-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="d25cf-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d25cf-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d25cf-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d25cf-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d25cf-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d25cf-107">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="d25cf-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d25cf-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="d25cf-108">Attributes</span></span>  
 <span data-ttu-id="d25cf-109">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d25cf-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d25cf-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d25cf-110">Child Elements</span></span>  
  
|<span data-ttu-id="d25cf-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="d25cf-111">Element</span></span>|<span data-ttu-id="d25cf-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d25cf-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d25cf-113">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="d25cf-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="d25cf-114">Permite a adição de tipos conhecidos a serem usados quando a desserialização.</span><span class="sxs-lookup"><span data-stu-id="d25cf-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d25cf-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d25cf-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d25cf-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="d25cf-116">Element</span></span>|<span data-ttu-id="d25cf-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="d25cf-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d25cf-118">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="d25cf-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="d25cf-119">O elemento de nível superior para a configuração.</span><span class="sxs-lookup"><span data-stu-id="d25cf-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d25cf-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d25cf-120">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="d25cf-121">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="d25cf-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="d25cf-122">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="d25cf-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
