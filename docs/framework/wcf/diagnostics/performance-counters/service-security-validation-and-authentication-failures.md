---
title: 'Serviço: Falhas de autenticação e validação de segurança'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: ba8da3ae6be6bd089690359f19e153da1e0b54fc
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150895"
---
# <a name="service-security-validation-and-authentication-failures"></a><span data-ttu-id="97032-102">Serviço: Falhas de autenticação e validação de segurança</span><span class="sxs-lookup"><span data-stu-id="97032-102">Service: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="97032-103">Nome do contador: Falhas de autenticação e validação de segurança</span><span class="sxs-lookup"><span data-stu-id="97032-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="97032-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="97032-104">Description</span></span>  
 <span data-ttu-id="97032-105">Esse contador é incrementado sempre que uma mensagem foi rejeitada devido a um problema de segurança não coberto pelo contador "Chamadas de segurança não autorizado".</span><span class="sxs-lookup"><span data-stu-id="97032-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="97032-106">Esses problemas incluem:</span><span class="sxs-lookup"><span data-stu-id="97032-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="97032-107">Não é possível ler o token de cliente da mensagem.</span><span class="sxs-lookup"><span data-stu-id="97032-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="97032-108">Token de cliente falha na autenticação (por exemplo, senha incorreta).</span><span class="sxs-lookup"><span data-stu-id="97032-108">Client token has failed authentication (for example,, bad password).</span></span>  
  
-   <span data-ttu-id="97032-109">Falha na verificação de assinatura (por exemplo, a mensagem foi violada).</span><span class="sxs-lookup"><span data-stu-id="97032-109">Signature verification has failed (for example,, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="97032-110">A mensagem é uma duplicata da anterior, o que pode ocorrer durante um ataque de repetição.</span><span class="sxs-lookup"><span data-stu-id="97032-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="97032-111">Ocorreu uma falha de descriptografia.</span><span class="sxs-lookup"><span data-stu-id="97032-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="97032-112">Alguns necessários elementos (por exemplo, carimbo de hora ausente ou bloquear os dados criptografados) estão ausentes da mensagem.</span><span class="sxs-lookup"><span data-stu-id="97032-112">Some required elements (for example,, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="97032-113">Ocorreram erros durante o handshake TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="97032-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
