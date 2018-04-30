---
title: Sessões seguras e conversas seguras
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
caps.latest.revision: 13
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 502064ce30f6e117168834643a116d3983811fb8
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="secure-conversations-and-secure-sessions"></a><span data-ttu-id="704c4-102">Sessões seguras e conversas seguras</span><span class="sxs-lookup"><span data-stu-id="704c4-102">Secure Conversations and Secure Sessions</span></span>
<span data-ttu-id="704c4-103">Um recurso do [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] é a capacidade de estabelecer sessões seguras entre dois pontos de extremidade que autentiquem uns aos outros e concordem com um processo de criptografia e assinatura digital.</span><span class="sxs-lookup"><span data-stu-id="704c4-103">A feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is the ability to establish secure sessions between two endpoints that authenticate each other and agree upon an encryption and digital signature process.</span></span> <span data-ttu-id="704c4-104">Por exemplo, o ponto de extremidade de serviço pode exigir um ponto de extremidade do cliente para enviar um token de segurança com base em um certificado x. 509 para autenticação.</span><span class="sxs-lookup"><span data-stu-id="704c4-104">For example, the service endpoint might require a client endpoint to send a security token based upon an X.509 certificate for authentication.</span></span> <span data-ttu-id="704c4-105">Depois que o cliente é autenticado, o ponto de extremidade de serviço retorna um token de contexto de segurança (SCT) para o cliente que é usado para proteger todas as mensagens subsequentes na sessão.</span><span class="sxs-lookup"><span data-stu-id="704c4-105">Once the client is authenticated, the service endpoint returns a security context token (SCT) back to the client that is then used to secure all subsequent messages within the session.</span></span> <span data-ttu-id="704c4-106">Estabelecer essa sessão segura permite que o conjunto de mensagens trocadas entre os dois pontos de extremidade para ser mais eficiente, porque o SCT tem uma chave simétrica.</span><span class="sxs-lookup"><span data-stu-id="704c4-106">Establishing this secure session enables the set of messages that are exchanged between the two endpoints to be more efficient, because the SCT has a symmetric key.</span></span> <span data-ttu-id="704c4-107">Chaves assimétricas, os certificados x. 509 se baseiam, exigem mais potência computacional que as chaves simétricas quando gerar uma assinatura digital ou criptografar um conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="704c4-107">Asymmetric keys, which X.509 certificates are based upon, require significantly more computational power than symmetric keys when generating a digital signature or encrypting a set of data.</span></span>  
  
 <span data-ttu-id="704c4-108">A política de inicialização (definidos na seção 6.2.7 o [WS-SecurityPolicy](http://go.microsoft.com/fwlink/?LinkId=99817) padrão) contém as declarações de segurança de mensagem usadas para proteger o canal e autenticar o cliente antes da primeira/SCT e RSTR/SCT troca.</span><span class="sxs-lookup"><span data-stu-id="704c4-108">The bootstrap policy (defined in section 6.2.7 of the [WS-SecurityPolicy](http://go.microsoft.com/fwlink/?LinkId=99817) standard) contains the message security assertions used to secure the channel and authenticate the client prior to the RST/SCT and RSTR/SCT exchange.</span></span> <span data-ttu-id="704c4-109">Determinados [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] associações padrão tem um `Security.Message.EstablishSecurityContext` propriedade que controla se proteger a conversa é usada.</span><span class="sxs-lookup"><span data-stu-id="704c4-109">Certain [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] standard bindings have a `Security.Message.EstablishSecurityContext` property which controls whether secure conversation is used.</span></span> <span data-ttu-id="704c4-110">Ao usar associações personalizadas a inicialização é indicada pelo aninhamento elementos de associação de segurança, por meio de [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) no arquivo de configuração, ou chamando <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> no código.</span><span class="sxs-lookup"><span data-stu-id="704c4-110">When using custom bindings the bootstrap is indicated by nesting security binding elements, either through [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) in the configuration file, or by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> in code.</span></span>  
  
 <span data-ttu-id="704c4-111">Para obter mais informações sobre as sessões, consulte [sessões usando](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="704c4-111">For more information about sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="704c4-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="704c4-112">See Also</span></span>  
 [<span data-ttu-id="704c4-113">Sessões, instanciação e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="704c4-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [<span data-ttu-id="704c4-114">Como criar um serviço que requer sessões</span><span class="sxs-lookup"><span data-stu-id="704c4-114">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
