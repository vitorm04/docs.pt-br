---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: e1b40718638ded54e59743730159ea6e65a51a57
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398191"
---
# \<callbackTimeouts>
<span data-ttu-id="44fcf-101">Especifica o valor de tempo limite ao fluir transações do servidor para client.in um cenário de contrato de retorno de chamada duplex.</span><span class="sxs-lookup"><span data-stu-id="44fcf-101">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackTimeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="44fcf-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44fcf-102">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="44fcf-103">Type</span><span class="sxs-lookup"><span data-stu-id="44fcf-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44fcf-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="44fcf-104">Attributes and Elements</span></span>  
 <span data-ttu-id="44fcf-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="44fcf-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44fcf-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="44fcf-106">Attributes</span></span>  
  
|<span data-ttu-id="44fcf-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="44fcf-107">Attribute</span></span>|<span data-ttu-id="44fcf-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="44fcf-108">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="44fcf-109">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo dentro do qual as transações devem ser concluídas ou encerradas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="44fcf-109">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="44fcf-110">O padrão é "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="44fcf-110">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44fcf-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="44fcf-111">Child Elements</span></span>  
 <span data-ttu-id="44fcf-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="44fcf-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44fcf-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="44fcf-113">Parent Elements</span></span>  
  
|<span data-ttu-id="44fcf-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="44fcf-114">Element</span></span>|<span data-ttu-id="44fcf-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="44fcf-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="44fcf-116">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="44fcf-116">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44fcf-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="44fcf-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
