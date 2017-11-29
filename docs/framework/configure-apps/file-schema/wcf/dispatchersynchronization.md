---
title: '&lt;dispatcherSynchronization&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 24ae6dbf0fb67b5755aca848ea7fce6abda14b0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="c77ef-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="c77ef-102">&lt;dispatcherSynchronization&gt;</span></span>

<span data-ttu-id="c77ef-103">Especifica um comportamento de ponto de extremidade que permite que um serviço enviar respostas de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="c77ef-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>

<span data-ttu-id="c77ef-104">\<System. ServiceModel > \<comportamentos > \<endpointBehaviors > \<comportamento ></span><span class="sxs-lookup"><span data-stu-id="c77ef-104">\<system.serviceModel> \<behaviors> \<endpointBehaviors> \<behavior></span></span>

## <a name="syntax"></a><span data-ttu-id="c77ef-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c77ef-105">Syntax</span></span>

```xml
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean" 
                                   maxPendingReceives="Integer" />
```

## <a name="type"></a><span data-ttu-id="c77ef-106">Tipo</span><span class="sxs-lookup"><span data-stu-id="c77ef-106">Type</span></span>

`Type`

## <a name="attributes-and-elements"></a><span data-ttu-id="c77ef-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c77ef-107">Attributes and elements</span></span>

<span data-ttu-id="c77ef-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c77ef-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c77ef-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="c77ef-109">Attributes</span></span>

| <span data-ttu-id="c77ef-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="c77ef-110">Attribute</span></span>               | <span data-ttu-id="c77ef-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="c77ef-111">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="c77ef-112">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="c77ef-112">asynchronousSendEnabled</span></span> | <span data-ttu-id="c77ef-113">Um valor booleano que especifica se o comportamento de envio assíncrono está habilitado.</span><span class="sxs-lookup"><span data-stu-id="c77ef-113">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="c77ef-114">Um inteiro que especifica que o número de recebimentos concorrentes que pode ser emitido no canal.</span><span class="sxs-lookup"><span data-stu-id="c77ef-114">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="c77ef-115">Esse valor deve ser configurado somente depois que você configurou corretamente o comportamento de limitação de serviço.</span><span class="sxs-lookup"><span data-stu-id="c77ef-115">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="c77ef-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c77ef-116">Child elements</span></span>

<span data-ttu-id="c77ef-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c77ef-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c77ef-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c77ef-118">Parent elements</span></span>

| <span data-ttu-id="c77ef-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="c77ef-119">Element</span></span> | <span data-ttu-id="c77ef-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="c77ef-120">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="c77ef-121">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="c77ef-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="c77ef-122">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="c77ef-122">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="c77ef-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c77ef-123">See also</span></span>

 <span data-ttu-id="c77ef-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span><span class="sxs-lookup"><span data-stu-id="c77ef-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span></span>
