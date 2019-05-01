---
title: 'Serviço: Falhas de Validação e Autenticação de Segurança por Segundo'
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
ms.openlocfilehash: 97752fbd4ff38c40917c132fddfe3798a7ee6766
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998316"
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="992a8-102">Serviço: Falhas de Validação e Autenticação de Segurança por Segundo</span><span class="sxs-lookup"><span data-stu-id="992a8-102">Service: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="992a8-103">Nome do contador: Validação de segurança e falhas de autenticação por segundo.</span><span class="sxs-lookup"><span data-stu-id="992a8-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="992a8-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="992a8-104">Description</span></span>  
 <span data-ttu-id="992a8-105">Esse contador é incrementado sempre que uma mensagem foi rejeitada devido a um problema de segurança não coberto pelo contador "Chamadas de segurança não autorizado".</span><span class="sxs-lookup"><span data-stu-id="992a8-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="992a8-106">Esses problemas incluem:</span><span class="sxs-lookup"><span data-stu-id="992a8-106">Such problems include:</span></span>  
  
- <span data-ttu-id="992a8-107">Não é possível ler o token de cliente da mensagem.</span><span class="sxs-lookup"><span data-stu-id="992a8-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="992a8-108">Token de cliente falha na autenticação (por exemplo, senha incorreta).</span><span class="sxs-lookup"><span data-stu-id="992a8-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="992a8-109">Falha na verificação de assinatura (por exemplo, a mensagem foi violada).</span><span class="sxs-lookup"><span data-stu-id="992a8-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="992a8-110">A mensagem é uma duplicata da anterior, o que pode ocorrer durante um ataque de repetição.</span><span class="sxs-lookup"><span data-stu-id="992a8-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="992a8-111">Ocorreu uma falha de descriptografia.</span><span class="sxs-lookup"><span data-stu-id="992a8-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="992a8-112">Alguns necessários elementos (por exemplo, carimbo de hora ausente ou bloquear os dados criptografados) estão ausentes da mensagem.</span><span class="sxs-lookup"><span data-stu-id="992a8-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="992a8-113">Ocorreram erros durante o handshake TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="992a8-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="992a8-114">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir,</span><span class="sxs-lookup"><span data-stu-id="992a8-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula,</span></span>  
  
 <span data-ttu-id="992a8-115">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="992a8-115">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
