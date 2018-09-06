---
title: 'Serviço: falhas de autenticação e validação de segurança por segundo'
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: fb0d4fdebf07dacfa7f33d8645332348270128e4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43884833"
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="a075f-102">Serviço: falhas de autenticação e validação de segurança por segundo</span><span class="sxs-lookup"><span data-stu-id="a075f-102">Service: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="a075f-103">Nome do contador: validação de segurança e autenticação de falhas por segundo.</span><span class="sxs-lookup"><span data-stu-id="a075f-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a075f-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="a075f-104">Description</span></span>  
 <span data-ttu-id="a075f-105">Esse contador é incrementado sempre que uma mensagem foi rejeitada devido a um problema de segurança não coberto pelo contador "Chamadas de segurança não autorizado".</span><span class="sxs-lookup"><span data-stu-id="a075f-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="a075f-106">Esses problemas incluem:</span><span class="sxs-lookup"><span data-stu-id="a075f-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="a075f-107">Não é possível ler o token de cliente da mensagem.</span><span class="sxs-lookup"><span data-stu-id="a075f-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="a075f-108">Token de cliente falha na autenticação (por exemplo, senha incorreta).</span><span class="sxs-lookup"><span data-stu-id="a075f-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="a075f-109">Falha na verificação de assinatura (por exemplo, a mensagem foi violada).</span><span class="sxs-lookup"><span data-stu-id="a075f-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="a075f-110">A mensagem é uma duplicata da anterior, o que pode ocorrer durante um ataque de repetição.</span><span class="sxs-lookup"><span data-stu-id="a075f-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="a075f-111">Ocorreu uma falha de descriptografia.</span><span class="sxs-lookup"><span data-stu-id="a075f-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="a075f-112">Alguns necessários elementos (por exemplo, carimbo de hora ausente ou bloquear os dados criptografados) estão ausentes da mensagem.</span><span class="sxs-lookup"><span data-stu-id="a075f-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="a075f-113">Ocorreram erros durante o handshake TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="a075f-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="a075f-114">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir,</span><span class="sxs-lookup"><span data-stu-id="a075f-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula,</span></span>  
  
 <span data-ttu-id="a075f-115">(N 1 - N 0) / ((1!D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="a075f-115">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
