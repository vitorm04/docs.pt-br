---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: b95f25217c2a3558846cc7a0ef43e21aacd2ee2a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398009"
---
# \<dispatcherSynchronization>
  
<span data-ttu-id="02dbf-101">Especifica um comportamento de ponto de extremidade que permite que um serviço envie respostas de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="02dbf-101">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dispatcherSynchronization>**  
  
## <a name="syntax"></a><span data-ttu-id="02dbf-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02dbf-102">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="02dbf-103">Type</span><span class="sxs-lookup"><span data-stu-id="02dbf-103">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02dbf-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="02dbf-104">Attributes and elements</span></span>  
  
<span data-ttu-id="02dbf-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="02dbf-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02dbf-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="02dbf-106">Attributes</span></span>

| <span data-ttu-id="02dbf-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="02dbf-107">Attribute</span></span>               | <span data-ttu-id="02dbf-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="02dbf-108">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="02dbf-109">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="02dbf-109">asynchronousSendEnabled</span></span> | <span data-ttu-id="02dbf-110">Um booliano que especifica se o comportamento de envio assíncrono está habilitado.</span><span class="sxs-lookup"><span data-stu-id="02dbf-110">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="02dbf-111">Um inteiro que especifica o número de recebimentos simultâneos que podem ser emitidos no canal.</span><span class="sxs-lookup"><span data-stu-id="02dbf-111">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="02dbf-112">Esse valor deve ser configurado somente depois que você tiver configurado corretamente o comportamento de limitação de serviço.</span><span class="sxs-lookup"><span data-stu-id="02dbf-112">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="02dbf-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="02dbf-113">Child elements</span></span>

<span data-ttu-id="02dbf-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="02dbf-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="02dbf-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="02dbf-115">Parent elements</span></span>

| <span data-ttu-id="02dbf-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="02dbf-116">Element</span></span> | <span data-ttu-id="02dbf-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="02dbf-117">Description</span></span> |  
| ------- | ----------- |  
| [\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="02dbf-118">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="02dbf-118">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="02dbf-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="02dbf-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
