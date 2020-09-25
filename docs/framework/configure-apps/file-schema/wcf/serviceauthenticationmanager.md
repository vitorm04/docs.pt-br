---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: a7c1e06c74bd3ba62d52ef833b8ffb6a8fd594fb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167165"
---
# \<serviceAuthenticationManager>

<span data-ttu-id="504a4-101">Fornece um elemento de configuração de fluxo de trabalho que estabelece, no nível de serviço, a validade de uma transmissão, mensagem ou originador.</span><span class="sxs-lookup"><span data-stu-id="504a4-101">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="504a4-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="504a4-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="504a4-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="504a4-103">Attributes and Elements</span></span>  

 <span data-ttu-id="504a4-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="504a4-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="504a4-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="504a4-105">Attributes</span></span>  
  
|<span data-ttu-id="504a4-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="504a4-106">Attribute</span></span>|<span data-ttu-id="504a4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="504a4-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="504a4-108">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="504a4-108">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="504a4-109">Uma cadeia de caracteres que especifica o tipo da política de autenticação para o comportamento atual.</span><span class="sxs-lookup"><span data-stu-id="504a4-109">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="504a4-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="504a4-110">Child Elements</span></span>  

 <span data-ttu-id="504a4-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="504a4-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="504a4-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="504a4-112">Parent Elements</span></span>  
  
|<span data-ttu-id="504a4-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="504a4-113">Element</span></span>|<span data-ttu-id="504a4-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="504a4-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="504a4-115">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="504a4-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="504a4-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="504a4-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
