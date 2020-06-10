---
title: Sessões confiáveis
ms.date: 03/30/2017
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
ms.openlocfilehash: 910ad952192243c6aa8a79417ad711d8c2a4ba2e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590534"
---
# <a name="reliable-sessions"></a><span data-ttu-id="a430b-102">Sessões confiáveis</span><span class="sxs-lookup"><span data-stu-id="a430b-102">Reliable Sessions</span></span>

<span data-ttu-id="a430b-103">Esta seção descreve o que é uma sessão confiável do Windows Communication Foundation (WCF), para que ela é usada, como e quando usar uma delas, quais configurações de ligação dão suporte a ela e ponteiros sobre as práticas recomendadas.</span><span class="sxs-lookup"><span data-stu-id="a430b-103">This section describes what a Windows Communication Foundation (WCF) reliable session is, what it's used for, how and when to use one, what binding configurations support it, and pointers on best practices.</span></span> <span data-ttu-id="a430b-104">A tabela a seguir resume os detalhes sobre os pontos essenciais e tópicos relacionados nesta seção.</span><span class="sxs-lookup"><span data-stu-id="a430b-104">The following table summarizes details about the essential points and related topics in this section.</span></span>

<span data-ttu-id="a430b-105">O WCF de sessão confiável fornece recursos que garantem que as mensagens enviadas entre os pontos de extremidade sejam transferidas entre intermediários de transporte ou SOAP e são entregues apenas uma vez e, opcionalmente, na mesma ordem em que foram enviadas.</span><span class="sxs-lookup"><span data-stu-id="a430b-105">The reliable session WCF provides features ensuring that messages sent between endpoints are transferred across SOAP or transport intermediaries and are delivered only once and, optionally, in the same order in which they were sent.</span></span>

<span data-ttu-id="a430b-106">Para usar uma sessão confiável com um aplicativo WCF, use uma das associações fornecidas pelo sistema no WCF que ofereçam suporte a uma sessão confiável por padrão ou como uma opção, ou crie sua própria associação personalizada que dê suporte à sessão.</span><span class="sxs-lookup"><span data-stu-id="a430b-106">To use a reliable session with a WCF application, either use one of the system-provided bindings in WCF that support a reliable session by default or as an option, or create your own custom binding that supports the session.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a430b-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a430b-107">In This Section</span></span>

<span data-ttu-id="a430b-108">[Visão geral de sessões confiáveis](reliable-sessions-overview.md) Descreve as sessões confiáveis, quando usá-las, as diferentes associações que dão suporte a sessões confiáveis e como elas funcionam.</span><span class="sxs-lookup"><span data-stu-id="a430b-108">[Reliable Sessions Overview](reliable-sessions-overview.md) Describes reliable sessions, when to use them, the different bindings that support reliable sessions, and how they work.</span></span>

<span data-ttu-id="a430b-109">[Como: trocar mensagens em uma sessão confiável](how-to-exchange-messages-within-a-reliable-session.md) Descreve como criar uma sessão confiável via HTTP usando uma associação personalizada especificada na configuração.</span><span class="sxs-lookup"><span data-stu-id="a430b-109">[How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md) Describes how to create a reliable session over HTTP using a custom binding specified in the configuration.</span></span>

<span data-ttu-id="a430b-110">[Como: proteger mensagens em sessões confiáveis](how-to-secure-messages-within-reliable-sessions.md) Descreve como proteger uma sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="a430b-110">[How to: Secure Messages within Reliable Sessions](how-to-secure-messages-within-reliable-sessions.md) Describes how to secure a reliable session.</span></span>

<span data-ttu-id="a430b-111">[Como: criar uma associação de sessão confiável personalizada com HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md) Descreve como criar uma sessão confiável por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a430b-111">[How to: Create a Custom Reliable Session Binding with HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md) Describes how to create a reliable session over HTTPS.</span></span>

<span data-ttu-id="a430b-112">[Práticas recomendadas para sessões confiáveis](best-practices-for-reliable-sessions.md) Descreve algumas das práticas recomendadas associadas ao uso de uma sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="a430b-112">[Best Practices for Reliable Sessions](best-practices-for-reliable-sessions.md) Describes some of the best practices associated with using a reliable session.</span></span>

## <a name="reference"></a><span data-ttu-id="a430b-113">Referência</span><span class="sxs-lookup"><span data-stu-id="a430b-113">Reference</span></span>

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a><span data-ttu-id="a430b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a430b-114">See also</span></span>

- [<span data-ttu-id="a430b-115">Sessões confiáveis e filas</span><span class="sxs-lookup"><span data-stu-id="a430b-115">Queues and Reliable Sessions</span></span>](queues-and-reliable-sessions.md)
- [<span data-ttu-id="a430b-116">Sessões, instanciação e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="a430b-116">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)
