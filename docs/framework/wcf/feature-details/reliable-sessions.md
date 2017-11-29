---
title: "Sessões confiáveis"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 659309ff5560480c423fc9b0adab5e93eac05ce5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-sessions"></a><span data-ttu-id="a6d94-102">Sessões confiáveis</span><span class="sxs-lookup"><span data-stu-id="a6d94-102">Reliable Sessions</span></span>

<span data-ttu-id="a6d94-103">Esta seção descreve o que um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sessão confiável está, que ela é usada, como e quando usar um, quais configurações de associação dão suporte a ele e ponteiros de práticas recomendadas.</span><span class="sxs-lookup"><span data-stu-id="a6d94-103">This section describes what a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] reliable session is, what it's used for, how and when to use one, what binding configurations support it, and pointers on best practices.</span></span> <span data-ttu-id="a6d94-104">A tabela a seguir resume os detalhes sobre os pontos essenciais e tópicos relacionados nesta seção.</span><span class="sxs-lookup"><span data-stu-id="a6d94-104">The following table summarizes details about the essential points and related topics in this section.</span></span>

<span data-ttu-id="a6d94-105">A sessão confiável [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece featrues garantem que as mensagens enviadas entre pontos de extremidade são transferidas em SOAP ou transporte intermediários e são entregues somente uma vez e, opcionalmente, na mesma ordem em que foram enviadas.</span><span class="sxs-lookup"><span data-stu-id="a6d94-105">The reliable session [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides featrues ensuring that messages sent between endpoints are transferred across SOAP or transport intermediaries and are delivered only once and, optionally, in the same order in which they were sent.</span></span>

<span data-ttu-id="a6d94-106">Para usar uma sessão confiável com um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo, use uma das associações fornecidas pelo sistema em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] que oferece suporte a uma sessão confiável por padrão ou como uma opção ou criar sua própria associação personalizada que ofereça suporte a sessão.</span><span class="sxs-lookup"><span data-stu-id="a6d94-106">To use a reliable session with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, either use one of the system-provided bindings in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] that support a reliable session by default or as an option, or create your own custom binding that supports the session.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a6d94-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a6d94-107">In This Section</span></span>

<span data-ttu-id="a6d94-108">[Visão geral de sessões confiáveis](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="a6d94-108">[Reliable Sessions Overview](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) </span></span>  
<span data-ttu-id="a6d94-109">Descreve sessões confiáveis, quando usá-los, as associações diferentes que dão suporte a sessões confiáveis, e como elas funcionam.</span><span class="sxs-lookup"><span data-stu-id="a6d94-109">Describes reliable sessions, when to use them, the different bindings that support reliable sessions, and how they work.</span></span>

<span data-ttu-id="a6d94-110">[Como: troca de mensagens dentro de uma sessão confiável](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) </span><span class="sxs-lookup"><span data-stu-id="a6d94-110">[How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) </span></span>  
<span data-ttu-id="a6d94-111">Descreve como criar uma sessão confiável via HTTP usando uma associação personalizada especificada na configuração.</span><span class="sxs-lookup"><span data-stu-id="a6d94-111">Describes how to create a reliable session over HTTP using a custom binding specified in the configuration.</span></span>

<span data-ttu-id="a6d94-112">[Como: proteger mensagens em sessões confiáveis](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="a6d94-112">[How to: Secure Messages within Reliable Sessions](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) </span></span>  
<span data-ttu-id="a6d94-113">Descreve como proteger uma sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="a6d94-113">Describes how to secure a reliable session.</span></span>

<span data-ttu-id="a6d94-114">[Como: criar uma associação de sessão confiável personalizada com HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) </span><span class="sxs-lookup"><span data-stu-id="a6d94-114">[How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) </span></span>  
<span data-ttu-id="a6d94-115">Descreve como criar uma sessão confiável por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a6d94-115">Describes how to create a reliable session over HTTPS.</span></span>

<span data-ttu-id="a6d94-116">[Práticas recomendadas para sessões confiáveis](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="a6d94-116">[Best Practices for Reliable Sessions](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) </span></span>  
<span data-ttu-id="a6d94-117">Descreve algumas das práticas recomendadas associadas usando uma sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="a6d94-117">Describes some of the best practices associated with using a reliable session.</span></span>

## <a name="reference"></a><span data-ttu-id="a6d94-118">Referência</span><span class="sxs-lookup"><span data-stu-id="a6d94-118">Reference</span></span>

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a><span data-ttu-id="a6d94-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6d94-119">See Also</span></span>

<span data-ttu-id="a6d94-120">[Sessões confiáveis e filas](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="a6d94-120">[Queues and Reliable Sessions](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md) </span></span>  
[<span data-ttu-id="a6d94-121">Sessões, instanciação e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="a6d94-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
