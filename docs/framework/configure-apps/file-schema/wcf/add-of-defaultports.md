---
title: <add> de <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: f5de2aa897a3bc37d08932451a2c7b94bc603b9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400650"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="08c05-102">\<add> de \<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="08c05-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="08c05-103">Um ponto de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="08c05-103">A default communications endpoint that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultPorts>**](defaultports.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="08c05-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08c05-104">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08c05-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="08c05-105">Attributes and Elements</span></span>  
 <span data-ttu-id="08c05-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="08c05-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08c05-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="08c05-107">Attributes</span></span>  
  
|<span data-ttu-id="08c05-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="08c05-108">Attribute</span></span>|<span data-ttu-id="08c05-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="08c05-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="08c05-110">porta</span><span class="sxs-lookup"><span data-stu-id="08c05-110">port</span></span>|<span data-ttu-id="08c05-111">Um inteiro que especifica o número da porta de comunicação padrão</span><span class="sxs-lookup"><span data-stu-id="08c05-111">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="08c05-112">scheme</span><span class="sxs-lookup"><span data-stu-id="08c05-112">scheme</span></span>|<span data-ttu-id="08c05-113">Uma cadeia de caracteres que especifica o grupo de configurações de protocolo associado a uma porta de comunicação.</span><span class="sxs-lookup"><span data-stu-id="08c05-113">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08c05-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="08c05-114">Child Elements</span></span>  
 <span data-ttu-id="08c05-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="08c05-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08c05-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="08c05-116">Parent Elements</span></span>  
  
|<span data-ttu-id="08c05-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="08c05-117">Element</span></span>|<span data-ttu-id="08c05-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="08c05-118">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="08c05-119">Uma coleção de portas padrão que listam os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="08c05-119">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08c05-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="08c05-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
