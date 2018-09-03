---
title: 'Ponto de extremidade: falhas de autenticação e validação de segurança por segundo'
ms.date: 03/30/2017
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b857a608c6b485c384956e55247b6e02c49a8564
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43465933"
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="b1f4a-102">Ponto de extremidade: falhas de autenticação e validação de segurança por segundo</span><span class="sxs-lookup"><span data-stu-id="b1f4a-102">Endpoint: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="b1f4a-103">Nome do contador: validação de segurança e autenticação de falhas por segundo</span><span class="sxs-lookup"><span data-stu-id="b1f4a-103">Counter name: Security Validation and Authentication Failures Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="b1f4a-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1f4a-104">Description</span></span>  
 <span data-ttu-id="b1f4a-105">Esse contador é incrementado sempre que uma mensagem foi rejeitada devido a um problema de segurança não coberto pelo contador "Chamadas de segurança não autorizado".</span><span class="sxs-lookup"><span data-stu-id="b1f4a-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="b1f4a-106">Esses problemas incluem:</span><span class="sxs-lookup"><span data-stu-id="b1f4a-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="b1f4a-107">Não é possível ler o token de cliente da mensagem.</span><span class="sxs-lookup"><span data-stu-id="b1f4a-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="b1f4a-108">Token de cliente falha na autenticação (por exemplo, senha incorreta).</span><span class="sxs-lookup"><span data-stu-id="b1f4a-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="b1f4a-109">Falha na verificação de assinatura (por exemplo, a mensagem foi violada).</span><span class="sxs-lookup"><span data-stu-id="b1f4a-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="b1f4a-110">A mensagem é uma duplicata da anterior, o que pode ocorrer durante um ataque de repetição.</span><span class="sxs-lookup"><span data-stu-id="b1f4a-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="b1f4a-111">Ocorreu uma falha de descriptografia.</span><span class="sxs-lookup"><span data-stu-id="b1f4a-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="b1f4a-112">Alguns necessários elementos (por exemplo, carimbo de hora ausente ou bloquear os dados criptografados) estão ausentes da mensagem.</span><span class="sxs-lookup"><span data-stu-id="b1f4a-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="b1f4a-113">Ocorreram erros durante o handshake TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="b1f4a-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="b1f4a-114">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir:</span><span class="sxs-lookup"><span data-stu-id="b1f4a-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="b1f4a-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="b1f4a-115">(N1-N0)/((D1-D0)/F)</span></span>
