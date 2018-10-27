---
title: Falhas de autenticação e validação de segurança por segundo
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
ms.openlocfilehash: e3db8cb20399bdff9b73a428ea2a53909da4eee1
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50088761"
---
# <a name="security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="af683-102">Falhas de autenticação e validação de segurança por segundo</span><span class="sxs-lookup"><span data-stu-id="af683-102">Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="af683-103">Nome do contador: validação de segurança e autenticação de falhas por segundo.</span><span class="sxs-lookup"><span data-stu-id="af683-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="af683-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="af683-104">Description</span></span>  
 <span data-ttu-id="af683-105">Esse contador é incrementado sempre que uma mensagem foi rejeitada devido a um problema de segurança não coberto pelo contador "Chamadas de segurança não autorizado".</span><span class="sxs-lookup"><span data-stu-id="af683-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="af683-106">Esses problemas incluem:</span><span class="sxs-lookup"><span data-stu-id="af683-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="af683-107">Não é possível ler o token de cliente da mensagem.</span><span class="sxs-lookup"><span data-stu-id="af683-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="af683-108">Token de cliente falha na autenticação (por exemplo, senha incorreta).</span><span class="sxs-lookup"><span data-stu-id="af683-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="af683-109">Falha na verificação de assinatura (por exemplo, a mensagem foi violada).</span><span class="sxs-lookup"><span data-stu-id="af683-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="af683-110">A mensagem é uma duplicata da anterior, o que pode ocorrer durante um ataque de repetição.</span><span class="sxs-lookup"><span data-stu-id="af683-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="af683-111">Ocorreu uma falha de descriptografia.</span><span class="sxs-lookup"><span data-stu-id="af683-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="af683-112">Alguns necessários elementos (por exemplo, carimbo de hora ausente ou bloquear os dados criptografados) estão ausentes da mensagem.</span><span class="sxs-lookup"><span data-stu-id="af683-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="af683-113">Ocorreram erros durante o handshake TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="af683-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="af683-114">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir:</span><span class="sxs-lookup"><span data-stu-id="af683-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="af683-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="af683-115">(N1-N0)/((D1-D0)/F)</span></span>
