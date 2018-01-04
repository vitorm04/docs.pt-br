---
title: "Prevenindo ataques por repetição quando um serviço do WCF é hospedado em uma Web Farm"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba1a511442fead369fca7ca1e04a26dfacdde53b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="preventing-replay-attacks-when-a-wcf-service-is-hosted-in-a-web-farm"></a><span data-ttu-id="5e94c-102">Prevenindo ataques por repetição quando um serviço do WCF é hospedado em uma Web Farm</span><span class="sxs-lookup"><span data-stu-id="5e94c-102">Preventing Replay Attacks When a WCF Service is Hosted in a Web Farm</span></span>
<span data-ttu-id="5e94c-103">Quando usar a segurança de mensagem WCF impede ataques por repetição criando um NONCE fora da mensagem de entrada e verificação interna `InMemoryNonceCache` para ver se o NONCE gerado está presente.</span><span class="sxs-lookup"><span data-stu-id="5e94c-103">When using message security WCF prevents replay attacks by creating a NONCE out of the incoming message and checking the internal `InMemoryNonceCache` to see if the generated NONCE is present.</span></span> <span data-ttu-id="5e94c-104">Se for, a mensagem será descartada como uma reprodução.</span><span class="sxs-lookup"><span data-stu-id="5e94c-104">If it is, the message is discarded as a replay.</span></span> <span data-ttu-id="5e94c-105">Quando um serviço WCF é hospedado em um web farm, desde o `InMemoryNonceCache` não é compartilhado entre os nós no farm da web, o serviço está vulnerável a ataques de repetição.</span><span class="sxs-lookup"><span data-stu-id="5e94c-105">When a WCF service is hosted in a web farm, since the `InMemoryNonceCache` is not shared across the nodes in the web farm, the service is vulnerable to replay attacks.</span></span>  <span data-ttu-id="5e94c-106">Para atenuar esse cenário WCF 4.5 fornece um ponto de extensibilidade que permite que você implemente seu próprio cache compartilhado de NONCE derivando uma classe da classe abstrata <xref:System.ServiceModel.Security.NonceCache>.</span><span class="sxs-lookup"><span data-stu-id="5e94c-106">To mitigate this scenario WCF 4.5 provides an extensibility point that allows you to implement your own shared NONCE cache by deriving a class from the abstract class <xref:System.ServiceModel.Security.NonceCache>.</span></span>  
  
## <a name="noncecache-implementation"></a><span data-ttu-id="5e94c-107">Implementação de NonceCache</span><span class="sxs-lookup"><span data-stu-id="5e94c-107">NonceCache Implementation</span></span>  
 <span data-ttu-id="5e94c-108">Para implementar seu próprio cache NONCE compartilhado, derive uma classe de <xref:System.ServiceModel.Security.NonceCache> e substituir o <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> e <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> métodos.</span><span class="sxs-lookup"><span data-stu-id="5e94c-108">To implement your own shared NONCE cache, derive a class from <xref:System.ServiceModel.Security.NonceCache> and override the <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> and <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> methods.</span></span> <span data-ttu-id="5e94c-109"><xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A>verifica se o NONCE especificado existe no cache.</span><span class="sxs-lookup"><span data-stu-id="5e94c-109"><xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> will check to see if the specified NONCE exists in the cache.</span></span> <span data-ttu-id="5e94c-110"><xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A>tenta adicionar um valor de uso único para o cache.</span><span class="sxs-lookup"><span data-stu-id="5e94c-110"><xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> will attempt to add a NONCE to the cache.</span></span> <span data-ttu-id="5e94c-111">Depois que a classe é implementada, você associá-lo criando uma instância e atribuindo-a para <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> detecção de repetição do lado do cliente e <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> detecção de repetição do lado do servidor.</span><span class="sxs-lookup"><span data-stu-id="5e94c-111">Once the class is implemented, you hook it up by instantiating an instance and assigning it to <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> for client-side replay detection and <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> for server-side replay detection.</span></span> <span data-ttu-id="5e94c-112">Não há nenhum limite de suporte a configuração para esse recurso.</span><span class="sxs-lookup"><span data-stu-id="5e94c-112">There is no out of the box configuration support for this feature.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e94c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e94c-113">See Also</span></span>  
 [<span data-ttu-id="5e94c-114">Segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="5e94c-114">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [<span data-ttu-id="5e94c-115">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="5e94c-115">SymmetricSecurityBindingElement</span></span>](../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)
