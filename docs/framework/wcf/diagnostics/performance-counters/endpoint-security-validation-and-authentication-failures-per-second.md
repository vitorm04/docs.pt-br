---
title: "Ponto de extremidade: falhas de autenticação e validação de segurança por segundo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f457a3067a4ada3ea226bf289c9c559ef5e35594
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="fdce4-102">Ponto de extremidade: falhas de autenticação e validação de segurança por segundo</span><span class="sxs-lookup"><span data-stu-id="fdce4-102">Endpoint: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="fdce4-103">Nome do contador: validação de segurança e autenticação de falhas por segundo</span><span class="sxs-lookup"><span data-stu-id="fdce4-103">Counter name: Security Validation and Authentication Failures Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="fdce4-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdce4-104">Description</span></span>  
 <span data-ttu-id="fdce4-105">Esse contador é incrementado sempre que uma mensagem foi rejeitada devido a um problema de segurança não coberto pelo contador "Chamadas de segurança não autorizado".</span><span class="sxs-lookup"><span data-stu-id="fdce4-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="fdce4-106">Esses problemas incluem:</span><span class="sxs-lookup"><span data-stu-id="fdce4-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="fdce4-107">Não é possível ler o token de cliente da mensagem.</span><span class="sxs-lookup"><span data-stu-id="fdce4-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="fdce4-108">Token de cliente falha na autenticação (por exemplo, senha incorreta).</span><span class="sxs-lookup"><span data-stu-id="fdce4-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="fdce4-109">Falha na verificação de assinatura (por exemplo, a mensagem foi violada).</span><span class="sxs-lookup"><span data-stu-id="fdce4-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="fdce4-110">A mensagem é uma duplicata da anterior, o que pode ocorrer durante um ataque de repetição.</span><span class="sxs-lookup"><span data-stu-id="fdce4-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="fdce4-111">Ocorreu uma falha de descriptografia.</span><span class="sxs-lookup"><span data-stu-id="fdce4-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="fdce4-112">Alguns necessários faltam elementos (por exemplo, timestamp ausente ou bloquear os dados criptografados) da mensagem.</span><span class="sxs-lookup"><span data-stu-id="fdce4-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="fdce4-113">Ocorreram erros durante o handshake TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="fdce4-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="fdce4-114">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir:</span><span class="sxs-lookup"><span data-stu-id="fdce4-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="fdce4-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="fdce4-115">(N1-N0)/((D1-D0)/F)</span></span>
