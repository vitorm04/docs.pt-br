---
title: 'Serviço: falhas de autenticação e validação de segurança por segundo'
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0dadf11888e55a96b15e09d5f4b326e8c5e18a02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="4bd51-102">Serviço: falhas de autenticação e validação de segurança por segundo</span><span class="sxs-lookup"><span data-stu-id="4bd51-102">Service: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="4bd51-103">Nome do contador: validação de segurança e autenticação de falhas por segundo.</span><span class="sxs-lookup"><span data-stu-id="4bd51-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4bd51-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="4bd51-104">Description</span></span>  
 <span data-ttu-id="4bd51-105">Esse contador é incrementado sempre que uma mensagem foi rejeitada devido a um problema de segurança não coberto pelo contador "Chamadas de segurança não autorizado".</span><span class="sxs-lookup"><span data-stu-id="4bd51-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="4bd51-106">Esses problemas incluem:</span><span class="sxs-lookup"><span data-stu-id="4bd51-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="4bd51-107">Não é possível ler o token de cliente da mensagem.</span><span class="sxs-lookup"><span data-stu-id="4bd51-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="4bd51-108">Token de cliente falha na autenticação (por exemplo, senha incorreta).</span><span class="sxs-lookup"><span data-stu-id="4bd51-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="4bd51-109">Falha na verificação de assinatura (por exemplo, a mensagem foi violada).</span><span class="sxs-lookup"><span data-stu-id="4bd51-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="4bd51-110">A mensagem é uma duplicata da anterior, o que pode ocorrer durante um ataque de repetição.</span><span class="sxs-lookup"><span data-stu-id="4bd51-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="4bd51-111">Ocorreu uma falha de descriptografia.</span><span class="sxs-lookup"><span data-stu-id="4bd51-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="4bd51-112">Alguns necessários faltam elementos (por exemplo, timestamp ausente ou bloquear os dados criptografados) da mensagem.</span><span class="sxs-lookup"><span data-stu-id="4bd51-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="4bd51-113">Ocorreram erros durante o handshake TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="4bd51-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="4bd51-114">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a seguinte fórmula:</span><span class="sxs-lookup"><span data-stu-id="4bd51-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula,</span></span>  
  
 <span data-ttu-id="4bd51-115">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="4bd51-115">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
