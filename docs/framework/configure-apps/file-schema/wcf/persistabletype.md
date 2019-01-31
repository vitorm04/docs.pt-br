---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 3ea99d360ceb1e3fe6e97cbf9c8827dd7c853f63
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256518"
---
# <a name="persistabletype"></a><span data-ttu-id="3dab7-101">\<persistableType></span><span class="sxs-lookup"><span data-stu-id="3dab7-101">\<persistableType></span></span>
<span data-ttu-id="3dab7-102">Especifica todos os tipos persistentes.</span><span class="sxs-lookup"><span data-stu-id="3dab7-102">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="3dab7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3dab7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="3dab7-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="3dab7-104">\<comContracts></span></span>  
<span data-ttu-id="3dab7-105">\<comContract></span><span class="sxs-lookup"><span data-stu-id="3dab7-105">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dab7-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3dab7-106">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="type"></a><span data-ttu-id="3dab7-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="3dab7-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3dab7-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3dab7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3dab7-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3dab7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3dab7-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="3dab7-110">Attributes</span></span>  
  
|<span data-ttu-id="3dab7-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="3dab7-111">Attribute</span></span>|<span data-ttu-id="3dab7-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3dab7-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3dab7-113">id</span><span class="sxs-lookup"><span data-stu-id="3dab7-113">id</span></span>|<span data-ttu-id="3dab7-114">Um atributo necessário que contém uma cadeia de caracteres que especifica um identificador exclusivo para um tipo persistente.</span><span class="sxs-lookup"><span data-stu-id="3dab7-114">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="3dab7-115">name</span><span class="sxs-lookup"><span data-stu-id="3dab7-115">name</span></span>|<span data-ttu-id="3dab7-116">Um atributo opcional que contém uma cadeia de caracteres que especifica o nome do tipo persistente.</span><span class="sxs-lookup"><span data-stu-id="3dab7-116">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3dab7-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3dab7-117">Child Elements</span></span>  
 <span data-ttu-id="3dab7-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3dab7-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3dab7-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3dab7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3dab7-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="3dab7-120">Element</span></span>|<span data-ttu-id="3dab7-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="3dab7-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3dab7-122">\<persistableTypes></span><span class="sxs-lookup"><span data-stu-id="3dab7-122">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="3dab7-123">Uma coleção de elementos `persistableType`.</span><span class="sxs-lookup"><span data-stu-id="3dab7-123">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3dab7-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3dab7-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="3dab7-125">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="3dab7-125">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="3dab7-126">Integração de aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="3dab7-126">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="3dab7-127">Como: Definir as configurações de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="3dab7-127">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
