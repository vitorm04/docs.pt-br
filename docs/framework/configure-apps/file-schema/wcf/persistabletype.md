---
title: '&lt;persistableType&gt;'
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 23724957398ed1ade2c81a3932e9773d7cf4c642
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltpersistabletypegt"></a><span data-ttu-id="65777-102">&lt;persistableType&gt;</span><span class="sxs-lookup"><span data-stu-id="65777-102">&lt;persistableType&gt;</span></span>
<span data-ttu-id="65777-103">Especifica todos os tipos persistentes.</span><span class="sxs-lookup"><span data-stu-id="65777-103">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="65777-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="65777-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="65777-105">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="65777-105">\<comContracts></span></span>  
<span data-ttu-id="65777-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="65777-106">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65777-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65777-107">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="65777-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="65777-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65777-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="65777-109">Attributes and Elements</span></span>  
 <span data-ttu-id="65777-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="65777-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65777-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="65777-111">Attributes</span></span>  
  
|<span data-ttu-id="65777-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="65777-112">Attribute</span></span>|<span data-ttu-id="65777-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="65777-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="65777-114">id</span><span class="sxs-lookup"><span data-stu-id="65777-114">id</span></span>|<span data-ttu-id="65777-115">Um atributo necessário que contém uma cadeia de caracteres que especifica um identificador exclusivo para um tipo persistente.</span><span class="sxs-lookup"><span data-stu-id="65777-115">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="65777-116">name</span><span class="sxs-lookup"><span data-stu-id="65777-116">name</span></span>|<span data-ttu-id="65777-117">Um atributo opcional que contém uma cadeia de caracteres que especifica o nome do tipo persistente.</span><span class="sxs-lookup"><span data-stu-id="65777-117">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65777-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="65777-118">Child Elements</span></span>  
 <span data-ttu-id="65777-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="65777-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="65777-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="65777-120">Parent Elements</span></span>  
  
|<span data-ttu-id="65777-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="65777-121">Element</span></span>|<span data-ttu-id="65777-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="65777-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65777-123">\<persistableTypes></span><span class="sxs-lookup"><span data-stu-id="65777-123">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="65777-124">Uma coleção de elementos `persistableType`.</span><span class="sxs-lookup"><span data-stu-id="65777-124">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65777-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65777-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>  
 [<span data-ttu-id="65777-126">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="65777-126">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="65777-127">Integração de aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="65777-127">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="65777-128">Como definir configurações de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="65777-128">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
