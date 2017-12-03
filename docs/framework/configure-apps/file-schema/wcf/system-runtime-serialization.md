---
title: '&lt;Serialization&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a6eb2b152f2ab11bbe0e08ff1ad22f94d45057e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltsystemruntimeserializationgt"></a><span data-ttu-id="f1a72-102">&lt;Serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="f1a72-102">&lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="f1a72-103">Representa o elemento raiz para o <xref:System.Runtime.Serialization> seção de namespace e contém elementos para configurar as opções do <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f1a72-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="f1a72-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="f1a72-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1a72-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1a72-105">Syntax</span></span>  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer ignoreExtensionDataObject="Boolean"  
      maxItemsInObjectGraph="Integer">  
      <declaredTypes>  
        <add type="String ">  
          <knownType type="String">  
             <parameter index="Integer"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1a72-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f1a72-106">Attributes and Elements</span></span>  
 <span data-ttu-id="f1a72-107">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="f1a72-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1a72-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="f1a72-108">Attributes</span></span>  
 <span data-ttu-id="f1a72-109">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f1a72-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f1a72-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f1a72-110">Child Elements</span></span>  
  
|<span data-ttu-id="f1a72-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="f1a72-111">Element</span></span>|<span data-ttu-id="f1a72-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1a72-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1a72-113">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="f1a72-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="f1a72-114">Permite a adição de tipos conhecidos a serem usados quando a desserialização.</span><span class="sxs-lookup"><span data-stu-id="f1a72-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f1a72-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f1a72-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f1a72-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="f1a72-116">Element</span></span>|<span data-ttu-id="f1a72-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1a72-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1a72-118">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="f1a72-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="f1a72-119">O elemento de nível superior para a configuração.</span><span class="sxs-lookup"><span data-stu-id="f1a72-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1a72-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1a72-120">See Also</span></span>  
 <xref:System.Runtime.Serialization>  
 [<span data-ttu-id="f1a72-121">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="f1a72-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="f1a72-122">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="f1a72-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
