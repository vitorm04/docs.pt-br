---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: 315122914ebcb3e8e4d72c8d976026a126306168
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218999"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a><span data-ttu-id="96155-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span><span class="sxs-lookup"><span data-stu-id="96155-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span></span>
<span data-ttu-id="96155-103">O handshake de segurança com um vizinho potencial não foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="96155-103">The security handshake with a potential neighbor was not successful.</span></span>  
  
## <a name="description"></a><span data-ttu-id="96155-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="96155-104">Description</span></span>  
 <span data-ttu-id="96155-105">Este rastreamento ocorre ao tentar estabelecer uma conexão segura de vizinho.</span><span class="sxs-lookup"><span data-stu-id="96155-105">This trace occurs while attempting to establish a secure neighbor connection.</span></span> <span data-ttu-id="96155-106">Isso pode acontecer devido a credenciais insuficientes ou incorretas.</span><span class="sxs-lookup"><span data-stu-id="96155-106">This can happen due to insufficient or incorrect credentials.</span></span>  
  
 <span data-ttu-id="96155-107">PeerChannel reconhece um único tipo de token para a identificação de alta segurança, certificados X.509, que fornecem um modelo de identidade forte com base no tipo de autenticação e autorização que pode ser implementada.</span><span class="sxs-lookup"><span data-stu-id="96155-107">PeerChannel recognizes a single token type for strong identification, X.509 certificates, which provide a strong identity model based on the type of authentication and authorization that can be implemented.</span></span> <span data-ttu-id="96155-108">PeerChannel também fornece suporte para aplicativos simples com o uso de senhas.</span><span class="sxs-lookup"><span data-stu-id="96155-108">PeerChannel also provides support for simple applications through the use of passwords.</span></span> <span data-ttu-id="96155-109">Senhas podem ser usadas apenas para permitir a entrada para a sessão; eles não podem ser usados para realizar a autenticação de mensagem.</span><span class="sxs-lookup"><span data-stu-id="96155-109">Passwords can be used only to allow entry to the session; they cannot be used to perform message authentication.</span></span> <span data-ttu-id="96155-110">Isso ocorre porque um token simétrico que compartilham um grupo de pares é difícil e inadequado usar para autenticação de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="96155-110">This is because a symmetric token that a group of peers share is difficult and inappropriate to use for source authentication.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="96155-111">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="96155-111">Troubleshooting</span></span>  
 <span data-ttu-id="96155-112">Certifique-se de que todos os vizinhos tenham as credenciais de segurança apropriadas.</span><span class="sxs-lookup"><span data-stu-id="96155-112">Ensure that all neighbors have the appropriate security credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96155-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96155-113">See also</span></span>

- [<span data-ttu-id="96155-114">Segurança de canal par</span><span class="sxs-lookup"><span data-stu-id="96155-114">Peer Channel Security</span></span>](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [<span data-ttu-id="96155-115">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="96155-115">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="96155-116">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="96155-116">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="96155-117">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="96155-117">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
