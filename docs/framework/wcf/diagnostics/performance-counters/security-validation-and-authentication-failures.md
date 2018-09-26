---
title: Falhas de autenticação e validação de segurança
ms.date: 03/30/2017
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
author: BrucePerlerMS
ms.openlocfilehash: d13e94800d71c6f567c6aab61974e42b1a3f1706
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198183"
---
# <a name="security-validation-and-authentication-failures"></a><span data-ttu-id="aa4c6-102">Falhas de autenticação e validação de segurança</span><span class="sxs-lookup"><span data-stu-id="aa4c6-102">Security Validation and Authentication Failures</span></span>
<span data-ttu-id="aa4c6-103">Nome do contador: falhas de autenticação e validação de segurança</span><span class="sxs-lookup"><span data-stu-id="aa4c6-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="aa4c6-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa4c6-104">Description</span></span>  
 <span data-ttu-id="aa4c6-105">Esse contador é incrementado sempre que uma mensagem foi rejeitada devido a um problema de segurança não coberto pelo contador "Chamadas de segurança não autorizado".</span><span class="sxs-lookup"><span data-stu-id="aa4c6-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="aa4c6-106">Esses problemas incluem:</span><span class="sxs-lookup"><span data-stu-id="aa4c6-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="aa4c6-107">Não é possível ler o token de cliente da mensagem.</span><span class="sxs-lookup"><span data-stu-id="aa4c6-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="aa4c6-108">Token de cliente falha na autenticação (por exemplo, senha incorreta).</span><span class="sxs-lookup"><span data-stu-id="aa4c6-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="aa4c6-109">Falha na verificação de assinatura (por exemplo, a mensagem foi violada).</span><span class="sxs-lookup"><span data-stu-id="aa4c6-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="aa4c6-110">A mensagem é uma duplicata da anterior, o que pode ocorrer durante um ataque de repetição.</span><span class="sxs-lookup"><span data-stu-id="aa4c6-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="aa4c6-111">Ocorreu uma falha de descriptografia.</span><span class="sxs-lookup"><span data-stu-id="aa4c6-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="aa4c6-112">Alguns necessários elementos (por exemplo, carimbo de hora ausente ou bloquear os dados criptografados) estão ausentes da mensagem.</span><span class="sxs-lookup"><span data-stu-id="aa4c6-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="aa4c6-113">Ocorreram erros durante o handshake TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="aa4c6-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
