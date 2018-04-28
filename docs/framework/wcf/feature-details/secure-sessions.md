---
title: Sessões seguras
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
caps.latest.revision: 14
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 9506e791cf4da947eaadaff1669e5f2f975431c8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="secure-sessions"></a><span data-ttu-id="38b79-102">Sessões seguras</span><span class="sxs-lookup"><span data-stu-id="38b79-102">Secure Sessions</span></span>
<span data-ttu-id="38b79-103">Um recurso do [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] é sessões confiáveis que garantem que as mensagens são recebidas na ordem em que foram enviadas.</span><span class="sxs-lookup"><span data-stu-id="38b79-103">A feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="38b79-104">Os tópicos nesta seção abordam as implicações de segurança a serem considerados ao criar uma sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="38b79-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="38b79-105"> sessões confiáveis, consulte [sessões usando](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="38b79-105"> reliable sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38b79-106">Quando a representação é necessário no Windows XP, use uma sessão segura sem um token de contexto de segurança com monitoração de estado (SCT).</span><span class="sxs-lookup"><span data-stu-id="38b79-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="38b79-107">Quando SCTs com monitoração de estado são usadas com representação, um <xref:System.InvalidOperationException> é gerada.</span><span class="sxs-lookup"><span data-stu-id="38b79-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="38b79-108">Para obter mais informações, consulte [cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="38b79-108">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="38b79-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="38b79-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="38b79-110">Sessões e conversas seguras</span><span class="sxs-lookup"><span data-stu-id="38b79-110">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|<span data-ttu-id="38b79-111">Sessões seguras e conversas seguras são sinônimos.</span><span class="sxs-lookup"><span data-stu-id="38b79-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="38b79-112">Este tópico explica o funcionamento de uma conversa segura, e quando e por que usar o padrão.</span><span class="sxs-lookup"><span data-stu-id="38b79-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="38b79-113">Como criar uma sessão segura</span><span class="sxs-lookup"><span data-stu-id="38b79-113">How to: Create a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|<span data-ttu-id="38b79-114">Percorre Noções básicas de criação de uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="38b79-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="38b79-115">Como criar um token de contexto de segurança para uma sessão segura</span><span class="sxs-lookup"><span data-stu-id="38b79-115">How to: Create a Security Context Token for a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="38b79-116">Percorra as etapas de criação de uma Web farm que manterá o estado e as sessões com clientes.</span><span class="sxs-lookup"><span data-stu-id="38b79-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="38b79-117">Considerações sobre segurança para sessões seguras</span><span class="sxs-lookup"><span data-stu-id="38b79-117">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|<span data-ttu-id="38b79-118">Descreve as considerações especiais para sessões seguras.</span><span class="sxs-lookup"><span data-stu-id="38b79-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="38b79-119">Referência</span><span class="sxs-lookup"><span data-stu-id="38b79-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="38b79-120">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="38b79-120">Related Sections</span></span>  
 [<span data-ttu-id="38b79-121">Sessões, instanciação e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="38b79-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="38b79-122">Serviços de design e implantação</span><span class="sxs-lookup"><span data-stu-id="38b79-122">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="38b79-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38b79-123">See Also</span></span>  
 [<span data-ttu-id="38b79-124">Como habilitar a detecção de reprodução de mensagem</span><span class="sxs-lookup"><span data-stu-id="38b79-124">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [<span data-ttu-id="38b79-125">Ataques de reprodução</span><span class="sxs-lookup"><span data-stu-id="38b79-125">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [<span data-ttu-id="38b79-126">Como criar um serviço que requer sessões</span><span class="sxs-lookup"><span data-stu-id="38b79-126">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
