---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b09d7fc476d5eed7f7c534fdde46cb18eeac30d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a><span data-ttu-id="1304f-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span><span class="sxs-lookup"><span data-stu-id="1304f-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span></span>
<span data-ttu-id="1304f-103">O handshake de segurança com um potencial neighbor não foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="1304f-103">The security handshake with a potential neighbor was not successful.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1304f-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="1304f-104">Description</span></span>  
 <span data-ttu-id="1304f-105">Este rastreamento ocorre ao tentar estabelecer uma conexão segura vizinho.</span><span class="sxs-lookup"><span data-stu-id="1304f-105">This trace occurs while attempting to establish a secure neighbor connection.</span></span> <span data-ttu-id="1304f-106">Isso pode acontecer devido a credenciais insuficientes ou incorretas.</span><span class="sxs-lookup"><span data-stu-id="1304f-106">This can happen due to insufficient or incorrect credentials.</span></span>  
  
 <span data-ttu-id="1304f-107">PeerChannel reconhece um único tipo de token para identificação de alta segurança, certificados x. 509, que fornecem um modelo de identidade de alta segurança com base no tipo de autenticação e autorização que pode ser implementada.</span><span class="sxs-lookup"><span data-stu-id="1304f-107">PeerChannel recognizes a single token type for strong identification, X.509 certificates, which provide a strong identity model based on the type of authentication and authorization that can be implemented.</span></span> <span data-ttu-id="1304f-108">PeerChannel também oferece suporte para aplicativos simples com o uso de senhas.</span><span class="sxs-lookup"><span data-stu-id="1304f-108">PeerChannel also provides support for simple applications through the use of passwords.</span></span> <span data-ttu-id="1304f-109">Senhas podem ser usadas apenas para permitir a entrada para a sessão; eles não podem ser usados para realizar a autenticação de mensagem.</span><span class="sxs-lookup"><span data-stu-id="1304f-109">Passwords can be used only to allow entry to the session; they cannot be used to perform message authentication.</span></span> <span data-ttu-id="1304f-110">Isso ocorre porque um token simétrico que compartilham um grupo de pontos é difícil e inadequada usar para autenticação de origem.</span><span class="sxs-lookup"><span data-stu-id="1304f-110">This is because a symmetric token that a group of peers share is difficult and inappropriate to use for source authentication.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="1304f-111">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="1304f-111">Troubleshooting</span></span>  
 <span data-ttu-id="1304f-112">Certifique-se de que todos os vizinhos tem as credenciais de segurança apropriadas.</span><span class="sxs-lookup"><span data-stu-id="1304f-112">Ensure that all neighbors have the appropriate security credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1304f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1304f-113">See Also</span></span>  
 [<span data-ttu-id="1304f-114">Segurança de canal par</span><span class="sxs-lookup"><span data-stu-id="1304f-114">Peer Channel Security</span></span>](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [<span data-ttu-id="1304f-115">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="1304f-115">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="1304f-116">Usando o rastreamento para solucionar problemas de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="1304f-116">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 <span data-ttu-id="1304f-117">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)</span><span class="sxs-lookup"><span data-stu-id="1304f-117">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)</span></span>
