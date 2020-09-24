---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 92d3de42daf6f7baf288e3e74242381a60e76618
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153593"
---
# \<serviceTimeouts>

<span data-ttu-id="24728-101">Especifica o tempo limite para um serviço.</span><span class="sxs-lookup"><span data-stu-id="24728-101">Specifies the timeout for a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTimeouts>**  
  
## <a name="syntax"></a><span data-ttu-id="24728-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="24728-102">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="24728-103">Tipo</span><span class="sxs-lookup"><span data-stu-id="24728-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24728-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="24728-104">Attributes and Elements</span></span>  

 <span data-ttu-id="24728-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="24728-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24728-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="24728-106">Attributes</span></span>  
  
|<span data-ttu-id="24728-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="24728-107">Attribute</span></span>|<span data-ttu-id="24728-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="24728-108">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="24728-109">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo que uma transação deve fluir do cliente para o servidor.</span><span class="sxs-lookup"><span data-stu-id="24728-109">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="24728-110">O padrão é "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="24728-110">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24728-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="24728-111">Child Elements</span></span>  

 <span data-ttu-id="24728-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="24728-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="24728-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="24728-113">Parent Elements</span></span>  
  
|<span data-ttu-id="24728-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="24728-114">Element</span></span>|<span data-ttu-id="24728-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="24728-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="24728-116">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="24728-116">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="24728-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="24728-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
