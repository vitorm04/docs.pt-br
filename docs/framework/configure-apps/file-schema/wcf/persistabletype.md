---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 328caaefe0cc24da45b460cab0a672dc8a6ccce1
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855076"
---
# <a name="persistabletype"></a><span data-ttu-id="9bcaa-101">\<> persistableType</span><span class="sxs-lookup"><span data-stu-id="9bcaa-101">\<persistableType></span></span>
<span data-ttu-id="9bcaa-102">Especifica todos os tipos persistentes.</span><span class="sxs-lookup"><span data-stu-id="9bcaa-102">Specifies all the persistable types.</span></span>  
  
<span data-ttu-id="9bcaa-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9bcaa-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9bcaa-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9bcaa-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9bcaa-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de com-contratos**](comcontracts.md)</span><span class="sxs-lookup"><span data-stu-id="9bcaa-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)</span></span>\
<span data-ttu-id="9bcaa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de descontrato**](comcontract.md)</span><span class="sxs-lookup"><span data-stu-id="9bcaa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)</span></span>\
<span data-ttu-id="9bcaa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> persistableTypes**](persistabletypes.md)</span><span class="sxs-lookup"><span data-stu-id="9bcaa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<persistableTypes>**](persistabletypes.md)</span></span>\
<span data-ttu-id="9bcaa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> persistableType**</span><span class="sxs-lookup"><span data-stu-id="9bcaa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistableType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bcaa-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bcaa-109">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="9bcaa-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="9bcaa-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bcaa-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9bcaa-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9bcaa-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9bcaa-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bcaa-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="9bcaa-113">Attributes</span></span>  
  
|<span data-ttu-id="9bcaa-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="9bcaa-114">Attribute</span></span>|<span data-ttu-id="9bcaa-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bcaa-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9bcaa-116">id</span><span class="sxs-lookup"><span data-stu-id="9bcaa-116">id</span></span>|<span data-ttu-id="9bcaa-117">Um atributo necessário que contém uma cadeia de caracteres que especifica um identificador exclusivo para um tipo persistente.</span><span class="sxs-lookup"><span data-stu-id="9bcaa-117">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="9bcaa-118">name</span><span class="sxs-lookup"><span data-stu-id="9bcaa-118">name</span></span>|<span data-ttu-id="9bcaa-119">Um atributo opcional que contém uma cadeia de caracteres que especifica o nome do tipo persistente.</span><span class="sxs-lookup"><span data-stu-id="9bcaa-119">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9bcaa-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9bcaa-120">Child Elements</span></span>  
 <span data-ttu-id="9bcaa-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9bcaa-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9bcaa-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9bcaa-122">Parent Elements</span></span>  
  
|<span data-ttu-id="9bcaa-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="9bcaa-123">Element</span></span>|<span data-ttu-id="9bcaa-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bcaa-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9bcaa-125">\<persistableTypes></span><span class="sxs-lookup"><span data-stu-id="9bcaa-125">\<persistableTypes></span></span>](persistabletypes.md)|<span data-ttu-id="9bcaa-126">Uma coleção de elementos `persistableType`.</span><span class="sxs-lookup"><span data-stu-id="9bcaa-126">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9bcaa-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bcaa-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="9bcaa-128">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="9bcaa-128">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="9bcaa-129">Integração de aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="9bcaa-129">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="9bcaa-130">Como: Definir configurações de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="9bcaa-130">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
