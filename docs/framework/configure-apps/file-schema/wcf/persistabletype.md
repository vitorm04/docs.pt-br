---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 328caaefe0cc24da45b460cab0a672dc8a6ccce1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855076"
---
# \<persistableType>
<span data-ttu-id="57d97-101">Especifica todos os tipos persistentes.</span><span class="sxs-lookup"><span data-stu-id="57d97-101">Specifies all the persistable types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<persistableTypes>**](persistabletypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistableType>**  
  
## <a name="syntax"></a><span data-ttu-id="57d97-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57d97-102">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="57d97-103">Type</span><span class="sxs-lookup"><span data-stu-id="57d97-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57d97-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="57d97-104">Attributes and Elements</span></span>  
 <span data-ttu-id="57d97-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="57d97-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57d97-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="57d97-106">Attributes</span></span>  
  
|<span data-ttu-id="57d97-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="57d97-107">Attribute</span></span>|<span data-ttu-id="57d97-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="57d97-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="57d97-109">id</span><span class="sxs-lookup"><span data-stu-id="57d97-109">id</span></span>|<span data-ttu-id="57d97-110">Um atributo necessário que contém uma cadeia de caracteres que especifica um identificador exclusivo para um tipo persistente.</span><span class="sxs-lookup"><span data-stu-id="57d97-110">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="57d97-111">name</span><span class="sxs-lookup"><span data-stu-id="57d97-111">name</span></span>|<span data-ttu-id="57d97-112">Um atributo opcional que contém uma cadeia de caracteres que especifica o nome do tipo persistente.</span><span class="sxs-lookup"><span data-stu-id="57d97-112">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57d97-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="57d97-113">Child Elements</span></span>  
 <span data-ttu-id="57d97-114">Nenhum</span><span class="sxs-lookup"><span data-stu-id="57d97-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57d97-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="57d97-115">Parent Elements</span></span>  
  
|<span data-ttu-id="57d97-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="57d97-116">Element</span></span>|<span data-ttu-id="57d97-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="57d97-117">Description</span></span>|  
|-------------|-----------------|  
|[\<persistableTypes>](persistabletypes.md)|<span data-ttu-id="57d97-118">Uma coleção de elementos `persistableType`.</span><span class="sxs-lookup"><span data-stu-id="57d97-118">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57d97-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="57d97-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="57d97-120">Integração com aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="57d97-120">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="57d97-121">Como configurar configurações de serviço de COM+</span><span class="sxs-lookup"><span data-stu-id="57d97-121">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
