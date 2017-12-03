---
title: '&lt;persistableType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 56443902885e191d93897096e55742f7665ba00a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltpersistabletypegt"></a><span data-ttu-id="026b3-102">&lt;persistableType&gt;</span><span class="sxs-lookup"><span data-stu-id="026b3-102">&lt;persistableType&gt;</span></span>
<span data-ttu-id="026b3-103">Especifica todos os tipos persistentes.</span><span class="sxs-lookup"><span data-stu-id="026b3-103">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="026b3-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="026b3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="026b3-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="026b3-105">\<comContracts></span></span>  
<span data-ttu-id="026b3-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="026b3-106">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="026b3-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="026b3-107">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract>  
      <persistableTypes>  
         <persistableType id="string"  
            name="string">  
         </persistableType>  
      </persistableTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="type"></a><span data-ttu-id="026b3-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="026b3-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="026b3-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="026b3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="026b3-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="026b3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="026b3-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="026b3-111">Attributes</span></span>  
  
|<span data-ttu-id="026b3-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="026b3-112">Attribute</span></span>|<span data-ttu-id="026b3-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="026b3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="026b3-114">id</span><span class="sxs-lookup"><span data-stu-id="026b3-114">id</span></span>|<span data-ttu-id="026b3-115">Um atributo necessário que contém uma cadeia de caracteres que especifica um identificador exclusivo para um tipo persistente.</span><span class="sxs-lookup"><span data-stu-id="026b3-115">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="026b3-116">name</span><span class="sxs-lookup"><span data-stu-id="026b3-116">name</span></span>|<span data-ttu-id="026b3-117">Um atributo opcional que contém uma cadeia de caracteres que especifica o nome do tipo persistente.</span><span class="sxs-lookup"><span data-stu-id="026b3-117">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="026b3-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="026b3-118">Child Elements</span></span>  
 <span data-ttu-id="026b3-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="026b3-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="026b3-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="026b3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="026b3-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="026b3-121">Element</span></span>|<span data-ttu-id="026b3-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="026b3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="026b3-123">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="026b3-123">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="026b3-124">Uma coleção de `persistableType` elementos.</span><span class="sxs-lookup"><span data-stu-id="026b3-124">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="026b3-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="026b3-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>  
 [<span data-ttu-id="026b3-126">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="026b3-126">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="026b3-127">Integrando aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="026b3-127">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="026b3-128">Como: definir configurações de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="026b3-128">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
