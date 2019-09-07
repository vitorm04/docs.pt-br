---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: e1b40718638ded54e59743730159ea6e65a51a57
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398191"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="b88b6-101">\<callbackTimeouts></span><span class="sxs-lookup"><span data-stu-id="b88b6-101">\<callbackTimeouts></span></span>
<span data-ttu-id="b88b6-102">Especifica o valor de tempo limite ao fluir transações do servidor para client.in um cenário de contrato de retorno de chamada duplex.</span><span class="sxs-lookup"><span data-stu-id="b88b6-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
<span data-ttu-id="b88b6-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b88b6-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b88b6-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b88b6-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b88b6-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b88b6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="b88b6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b88b6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="b88b6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b88b6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="b88b6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> callbackTimeOuts**</span><span class="sxs-lookup"><span data-stu-id="b88b6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackTimeOuts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b88b6-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b88b6-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="b88b6-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="b88b6-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b88b6-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b88b6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b88b6-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b88b6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b88b6-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="b88b6-113">Attributes</span></span>  
  
|<span data-ttu-id="b88b6-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="b88b6-114">Attribute</span></span>|<span data-ttu-id="b88b6-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="b88b6-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="b88b6-116">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo dentro do qual as transações devem ser concluídas ou encerradas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b88b6-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="b88b6-117">O padrão é "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="b88b6-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b88b6-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b88b6-118">Child Elements</span></span>  
 <span data-ttu-id="b88b6-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b88b6-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b88b6-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b88b6-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b88b6-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="b88b6-121">Element</span></span>|<span data-ttu-id="b88b6-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="b88b6-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b88b6-123">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="b88b6-123">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="b88b6-124">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b88b6-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b88b6-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b88b6-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
