---
title: '&lt;Serialization&gt;'
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: 7cda0918ec14f9065ab1aea2479a14c8d224fcf8
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150546"
---
# <a name="ltsystemruntimeserializationgt"></a><span data-ttu-id="a68df-102">&lt;Serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="a68df-102">&lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="a68df-103">Representa o elemento raiz para o <xref:System.Runtime.Serialization> seção de namespace e contém elementos para configurar as opções do <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="a68df-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="a68df-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="a68df-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a68df-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a68df-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a68df-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a68df-106">Attributes and Elements</span></span>  
 <span data-ttu-id="a68df-107">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="a68df-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a68df-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="a68df-108">Attributes</span></span>  
 <span data-ttu-id="a68df-109">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a68df-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a68df-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a68df-110">Child Elements</span></span>  
  
|<span data-ttu-id="a68df-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="a68df-111">Element</span></span>|<span data-ttu-id="a68df-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a68df-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a68df-113">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="a68df-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="a68df-114">Permite a adição de tipos conhecidos a serem usados quando a desserialização.</span><span class="sxs-lookup"><span data-stu-id="a68df-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a68df-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a68df-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a68df-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="a68df-116">Element</span></span>|<span data-ttu-id="a68df-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="a68df-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a68df-118">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="a68df-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="a68df-119">O elemento de nível superior para a configuração.</span><span class="sxs-lookup"><span data-stu-id="a68df-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a68df-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a68df-120">See Also</span></span>  
 <xref:System.Runtime.Serialization>  
 [<span data-ttu-id="a68df-121">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="a68df-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="a68df-122">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="a68df-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
