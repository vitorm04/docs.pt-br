---
title: Falhas de Validação e Autenticação de Segurança por Segundo
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
ms.openlocfilehash: 546d81b73e912915d265fb194de4ad9e45d55cea
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163911"
---
# <a name="security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="2b772-102">Falhas de Validação e Autenticação de Segurança por Segundo</span><span class="sxs-lookup"><span data-stu-id="2b772-102">Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="2b772-103">Nome do contador: falhas de validação e autenticação de segurança por segundo.</span><span class="sxs-lookup"><span data-stu-id="2b772-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2b772-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b772-104">Description</span></span>  
 <span data-ttu-id="2b772-105">Esse contador é incrementado sempre que uma mensagem é rejeitada devido a um problema de segurança não coberto pelo contador "chamadas de segurança não autorizadas".</span><span class="sxs-lookup"><span data-stu-id="2b772-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="2b772-106">Esses problemas incluem:</span><span class="sxs-lookup"><span data-stu-id="2b772-106">Such problems include:</span></span>  
  
- <span data-ttu-id="2b772-107">O token do cliente não pode ser lido a partir da mensagem.</span><span class="sxs-lookup"><span data-stu-id="2b772-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="2b772-108">Falha na autenticação do token do cliente (por exemplo, senha inadequada).</span><span class="sxs-lookup"><span data-stu-id="2b772-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="2b772-109">Falha na verificação da assinatura (por exemplo, a mensagem foi violada).</span><span class="sxs-lookup"><span data-stu-id="2b772-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="2b772-110">A mensagem é uma duplicata de uma anterior, o que pode ocorrer durante um ataque de repetição.</span><span class="sxs-lookup"><span data-stu-id="2b772-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="2b772-111">Ocorreu uma falha de descriptografia.</span><span class="sxs-lookup"><span data-stu-id="2b772-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="2b772-112">Alguns elementos necessários (por exemplo, carimbo de data/hora ausente ou bloco de dados criptografados) estão ausentes da mensagem.</span><span class="sxs-lookup"><span data-stu-id="2b772-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="2b772-113">Ocorreram erros durante o handshake TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="2b772-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="2b772-114">Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a seguinte fórmula:</span><span class="sxs-lookup"><span data-stu-id="2b772-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="2b772-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="2b772-115">(N1-N0)/((D1-D0)/F)</span></span>
