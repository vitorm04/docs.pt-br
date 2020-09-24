---
title: <add> de <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 2c6b5de51e6508965daf6022a47d12d8d73f2a4d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149121"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="bc068-102">\<add> de \<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="bc068-102">\<add> of \<defaultPorts></span></span>

<span data-ttu-id="bc068-103">Um ponto de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="bc068-103">A default communications endpoint that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultPorts>**](defaultports.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="bc068-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="bc068-104">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc068-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bc068-105">Attributes and Elements</span></span>  

 <span data-ttu-id="bc068-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bc068-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc068-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="bc068-107">Attributes</span></span>  
  
|<span data-ttu-id="bc068-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="bc068-108">Attribute</span></span>|<span data-ttu-id="bc068-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc068-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bc068-110">porta</span><span class="sxs-lookup"><span data-stu-id="bc068-110">port</span></span>|<span data-ttu-id="bc068-111">Um inteiro que especifica o número da porta de comunicação padrão</span><span class="sxs-lookup"><span data-stu-id="bc068-111">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="bc068-112">scheme</span><span class="sxs-lookup"><span data-stu-id="bc068-112">scheme</span></span>|<span data-ttu-id="bc068-113">Uma cadeia de caracteres que especifica o grupo de configurações de protocolo associado a uma porta de comunicação.</span><span class="sxs-lookup"><span data-stu-id="bc068-113">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc068-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bc068-114">Child Elements</span></span>  

 <span data-ttu-id="bc068-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="bc068-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc068-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bc068-116">Parent Elements</span></span>  
  
|<span data-ttu-id="bc068-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="bc068-117">Element</span></span>|<span data-ttu-id="bc068-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc068-118">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="bc068-119">Uma coleção de portas padrão que listam os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="bc068-119">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc068-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="bc068-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
