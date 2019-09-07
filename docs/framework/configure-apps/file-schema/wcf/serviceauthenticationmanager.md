---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: cc5ebcf36a10e88d48ed14f1f10dac6396d7b242
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399703"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="3bb87-101">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="3bb87-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="3bb87-102">Fornece um elemento de configuração de fluxo de trabalho que estabelece, no nível de serviço, a validade de uma transmissão, mensagem ou originador.</span><span class="sxs-lookup"><span data-stu-id="3bb87-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="3bb87-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3bb87-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3bb87-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3bb87-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3bb87-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="3bb87-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="3bb87-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="3bb87-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="3bb87-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="3bb87-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="3bb87-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de pré-autenticação**</span><span class="sxs-lookup"><span data-stu-id="3bb87-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthenticationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bb87-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3bb87-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3bb87-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3bb87-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3bb87-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3bb87-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3bb87-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="3bb87-112">Attributes</span></span>  
  
|<span data-ttu-id="3bb87-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="3bb87-113">Attribute</span></span>|<span data-ttu-id="3bb87-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3bb87-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3bb87-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="3bb87-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="3bb87-116">Uma cadeia de caracteres que especifica o tipo da política de autenticação para o comportamento atual.</span><span class="sxs-lookup"><span data-stu-id="3bb87-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3bb87-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3bb87-117">Child Elements</span></span>  
 <span data-ttu-id="3bb87-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3bb87-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3bb87-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3bb87-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3bb87-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="3bb87-120">Element</span></span>|<span data-ttu-id="3bb87-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="3bb87-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3bb87-122">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="3bb87-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="3bb87-123">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="3bb87-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3bb87-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3bb87-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
