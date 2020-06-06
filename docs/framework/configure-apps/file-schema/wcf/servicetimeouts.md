---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 801a7aaf1f0d0fa267fa8cca3d2e7fd02919c475
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399556"
---
# \<serviceTimeouts>
<span data-ttu-id="a898a-101">Especifica o tempo limite para um serviço.</span><span class="sxs-lookup"><span data-stu-id="a898a-101">Specifies the timeout for a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTimeouts>**  
  
## <a name="syntax"></a><span data-ttu-id="a898a-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a898a-102">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="a898a-103">Type</span><span class="sxs-lookup"><span data-stu-id="a898a-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a898a-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a898a-104">Attributes and Elements</span></span>  
 <span data-ttu-id="a898a-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a898a-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a898a-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="a898a-106">Attributes</span></span>  
  
|<span data-ttu-id="a898a-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="a898a-107">Attribute</span></span>|<span data-ttu-id="a898a-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="a898a-108">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="a898a-109">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo que uma transação deve fluir do cliente para o servidor.</span><span class="sxs-lookup"><span data-stu-id="a898a-109">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="a898a-110">O padrão é "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="a898a-110">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a898a-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a898a-111">Child Elements</span></span>  
 <span data-ttu-id="a898a-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a898a-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a898a-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a898a-113">Parent Elements</span></span>  
  
|<span data-ttu-id="a898a-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="a898a-114">Element</span></span>|<span data-ttu-id="a898a-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a898a-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="a898a-116">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="a898a-116">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a898a-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="a898a-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
