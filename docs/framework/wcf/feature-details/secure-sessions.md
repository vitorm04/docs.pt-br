---
title: Sessões seguras
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: d511a45d990e441c5dcfd8405794ec937c0278d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966070"
---
# <a name="secure-sessions"></a><span data-ttu-id="8c0b9-102">Sessões seguras</span><span class="sxs-lookup"><span data-stu-id="8c0b9-102">Secure Sessions</span></span>
<span data-ttu-id="8c0b9-103">Um recurso do Windows Communication Foundation (WCF) é uma sessão confiável que garante que as mensagens sejam recebidas na ordem em que foram enviadas.</span><span class="sxs-lookup"><span data-stu-id="8c0b9-103">A feature of Windows Communication Foundation (WCF) is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="8c0b9-104">Os tópicos nesta seção discutem as implicações de segurança a serem consideradas ao criar uma sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="8c0b9-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="8c0b9-105">Para obter mais informações sobre sessões confiáveis, consulte [usando sessões](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="8c0b9-105">For more information about reliable sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c0b9-106">Quando a representação é necessária no Windows XP, use uma sessão segura sem um símbolo de contexto de segurança com estado (SCT).</span><span class="sxs-lookup"><span data-stu-id="8c0b9-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="8c0b9-107">Quando SCTs com estado são usados com representação, <xref:System.InvalidOperationException> um é gerado.</span><span class="sxs-lookup"><span data-stu-id="8c0b9-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="8c0b9-108">Para obter mais informações, consulte [cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="8c0b9-108">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8c0b9-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8c0b9-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="8c0b9-110">Sessões e conversas seguras</span><span class="sxs-lookup"><span data-stu-id="8c0b9-110">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|<span data-ttu-id="8c0b9-111">Conversas seguras e sessões seguras são sinônimos.</span><span class="sxs-lookup"><span data-stu-id="8c0b9-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="8c0b9-112">Este tópico explica como funciona uma conversa segura e quando e por que usar o padrão.</span><span class="sxs-lookup"><span data-stu-id="8c0b9-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="8c0b9-113">Como: Criar uma sessão segura</span><span class="sxs-lookup"><span data-stu-id="8c0b9-113">How to: Create a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|<span data-ttu-id="8c0b9-114">Percorre as noções básicas da criação de uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="8c0b9-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="8c0b9-115">Como: Criar um token de contexto de segurança para uma sessão segura</span><span class="sxs-lookup"><span data-stu-id="8c0b9-115">How to: Create a Security Context Token for a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="8c0b9-116">Percorre as etapas de criação de um Web farm que manterá o estado e as sessões com clientes.</span><span class="sxs-lookup"><span data-stu-id="8c0b9-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="8c0b9-117">Considerações sobre segurança para sessões seguras</span><span class="sxs-lookup"><span data-stu-id="8c0b9-117">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|<span data-ttu-id="8c0b9-118">Descreve considerações especiais para sessões seguras.</span><span class="sxs-lookup"><span data-stu-id="8c0b9-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="8c0b9-119">Referência</span><span class="sxs-lookup"><span data-stu-id="8c0b9-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="8c0b9-120">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="8c0b9-120">Related Sections</span></span>  
 [<span data-ttu-id="8c0b9-121">Sessões, instanciação e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="8c0b9-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="8c0b9-122">Serviços de design e implantação</span><span class="sxs-lookup"><span data-stu-id="8c0b9-122">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="8c0b9-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c0b9-123">See also</span></span>

- [<span data-ttu-id="8c0b9-124">Como: Habilitar detecção de reprodução de mensagem</span><span class="sxs-lookup"><span data-stu-id="8c0b9-124">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)
- [<span data-ttu-id="8c0b9-125">Ataques de reprodução</span><span class="sxs-lookup"><span data-stu-id="8c0b9-125">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [<span data-ttu-id="8c0b9-126">Como: Criar um serviço que requer sessões</span><span class="sxs-lookup"><span data-stu-id="8c0b9-126">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
