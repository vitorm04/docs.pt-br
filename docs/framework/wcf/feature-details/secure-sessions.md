---
title: Sessões seguras
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: 8f5cf9a965951bcc1049c2e96ae6cfa80b0113ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59084942"
---
# <a name="secure-sessions"></a><span data-ttu-id="ca0a0-102">Sessões seguras</span><span class="sxs-lookup"><span data-stu-id="ca0a0-102">Secure Sessions</span></span>
<span data-ttu-id="ca0a0-103">Um recurso do Windows Communication Foundation (WCF) é sessões confiáveis que garantem que as mensagens são recebidas na ordem em que foram enviadas.</span><span class="sxs-lookup"><span data-stu-id="ca0a0-103">A feature of Windows Communication Foundation (WCF) is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="ca0a0-104">Os tópicos nesta seção abordam as implicações de segurança a considerar ao criar uma sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="ca0a0-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="ca0a0-105">Para obter mais informações sobre as sessões confiáveis, consulte [sessões usando](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="ca0a0-105">For more information about reliable sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca0a0-106">Quando a representação é necessária no Windows XP, use uma sessão segura sem um token de contexto de segurança com monitoração de estado (SCT).</span><span class="sxs-lookup"><span data-stu-id="ca0a0-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="ca0a0-107">Quando SCTs com monitoração de estado são usados com a representação, um <xref:System.InvalidOperationException> é gerada.</span><span class="sxs-lookup"><span data-stu-id="ca0a0-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="ca0a0-108">Para obter mais informações, consulte [cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="ca0a0-108">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ca0a0-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ca0a0-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="ca0a0-110">Sessões e conversas seguras</span><span class="sxs-lookup"><span data-stu-id="ca0a0-110">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|<span data-ttu-id="ca0a0-111">Sessões seguras e conversas seguras são sinônimos.</span><span class="sxs-lookup"><span data-stu-id="ca0a0-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="ca0a0-112">Este tópico explica o funcionamento de uma conversa segura, e quando e por que usar o padrão.</span><span class="sxs-lookup"><span data-stu-id="ca0a0-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="ca0a0-113">Como: Criar uma sessão segura</span><span class="sxs-lookup"><span data-stu-id="ca0a0-113">How to: Create a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|<span data-ttu-id="ca0a0-114">Explica conceitos básicos da criação de uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="ca0a0-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="ca0a0-115">Como: Criar um contexto de segurança Token para uma sessão segura</span><span class="sxs-lookup"><span data-stu-id="ca0a0-115">How to: Create a Security Context Token for a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="ca0a0-116">Explica as etapas de criação de uma Web farm que manterá o estado e as sessões com clientes.</span><span class="sxs-lookup"><span data-stu-id="ca0a0-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="ca0a0-117">Considerações sobre segurança para sessões seguras</span><span class="sxs-lookup"><span data-stu-id="ca0a0-117">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|<span data-ttu-id="ca0a0-118">Descreve considerações especiais para sessões seguras.</span><span class="sxs-lookup"><span data-stu-id="ca0a0-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="ca0a0-119">Referência</span><span class="sxs-lookup"><span data-stu-id="ca0a0-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="ca0a0-120">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="ca0a0-120">Related Sections</span></span>  
 [<span data-ttu-id="ca0a0-121">Sessões, instanciação e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="ca0a0-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="ca0a0-122">Serviços de design e implantação</span><span class="sxs-lookup"><span data-stu-id="ca0a0-122">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="ca0a0-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca0a0-123">See also</span></span>

- [<span data-ttu-id="ca0a0-124">Como: Habilitar a detecção de reprodução de mensagem</span><span class="sxs-lookup"><span data-stu-id="ca0a0-124">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)
- [<span data-ttu-id="ca0a0-125">Ataques de reprodução</span><span class="sxs-lookup"><span data-stu-id="ca0a0-125">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [<span data-ttu-id="ca0a0-126">Como: Criar um serviço que requer sessões</span><span class="sxs-lookup"><span data-stu-id="ca0a0-126">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
