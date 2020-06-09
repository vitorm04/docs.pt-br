---
title: Considerações de segurança no WCF
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
ms.openlocfilehash: ed0f018e0151e68afeb9a4747bf8a260faa184b1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601030"
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="29081-102">Considerações de segurança no WCF</span><span class="sxs-lookup"><span data-stu-id="29081-102">Security Considerations in WCF</span></span>
<span data-ttu-id="29081-103">Os tópicos nesta seção listam vários itens relacionados à segurança a serem considerados ao criar um aplicativo Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="29081-103">The topics in this section list various security-related items to consider when designing a Windows Communication Foundation (WCF) application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="29081-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="29081-104">In This Section</span></span>  
 [<span data-ttu-id="29081-105">Divulgação de informações</span><span class="sxs-lookup"><span data-stu-id="29081-105">Information Disclosure</span></span>](information-disclosure.md)  
 <span data-ttu-id="29081-106">Discute as várias maneiras pelas quais as informações podem ser divulgadas ou atacadas e como mitigar isso.</span><span class="sxs-lookup"><span data-stu-id="29081-106">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="29081-107">Elevação de privilégio</span><span class="sxs-lookup"><span data-stu-id="29081-107">Elevation of Privilege</span></span>](elevation-of-privilege.md)  
 <span data-ttu-id="29081-108">Discute os efeitos de dar a um invasor permissões de autorização além daquelas inicialmente concedidas e como mitigar isso.</span><span class="sxs-lookup"><span data-stu-id="29081-108">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="29081-109">Negação de serviço</span><span class="sxs-lookup"><span data-stu-id="29081-109">Denial of Service</span></span>](denial-of-service.md)  
 <span data-ttu-id="29081-110">Discute o que acontece quando um sistema não consegue processar mensagens adequadamente e como atenuá-la.</span><span class="sxs-lookup"><span data-stu-id="29081-110">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="29081-111">Adulteração</span><span class="sxs-lookup"><span data-stu-id="29081-111">Tampering</span></span>](tampering.md)  
 <span data-ttu-id="29081-112">Discute a alteração de mensagens ou a entrega de mensagens e como atenuá-la.</span><span class="sxs-lookup"><span data-stu-id="29081-112">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="29081-113">Ataques por repetição</span><span class="sxs-lookup"><span data-stu-id="29081-113">Replay Attacks</span></span>](replay-attacks.md)  
 <span data-ttu-id="29081-114">Discute o que acontece quando um invasor copia um fluxo de mensagens entre duas partes e repete o fluxo para uma ou mais das partes e como mitigar isso.</span><span class="sxs-lookup"><span data-stu-id="29081-114">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="29081-115">Considerações de segurança para sessões seguras</span><span class="sxs-lookup"><span data-stu-id="29081-115">Security Considerations for Secure Sessions</span></span>](security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="29081-116">Discute os itens a seguir que afetam a segurança ao implementar sessões seguras.</span><span class="sxs-lookup"><span data-stu-id="29081-116">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="29081-117">Cenários sem suporte</span><span class="sxs-lookup"><span data-stu-id="29081-117">Unsupported Scenarios</span></span>](unsupported-scenarios.md)  
 <span data-ttu-id="29081-118">Lista vários cenários que não dão suporte a um aspecto específico de segurança e que devem ser evitados ou considerados.</span><span class="sxs-lookup"><span data-stu-id="29081-118">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="29081-119">Referência</span><span class="sxs-lookup"><span data-stu-id="29081-119">Reference</span></span>  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="29081-120">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="29081-120">Related Sections</span></span>  
 [<span data-ttu-id="29081-121">Diretrizes e práticas recomendadas de segurança</span><span class="sxs-lookup"><span data-stu-id="29081-121">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="29081-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29081-122">See also</span></span>

- [<span data-ttu-id="29081-123">Segurança</span><span class="sxs-lookup"><span data-stu-id="29081-123">Security</span></span>](security.md)
