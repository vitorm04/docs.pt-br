---
title: "Falhas de autenticação e validação de segurança"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c52b54d2be2e824de478e0ee9ec2452c57e181b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="security-validation-and-authentication-failures"></a><span data-ttu-id="fc25a-102">Falhas de autenticação e validação de segurança</span><span class="sxs-lookup"><span data-stu-id="fc25a-102">Security Validation and Authentication Failures</span></span>
<span data-ttu-id="fc25a-103">Nome do contador: falhas de autenticação e validação de segurança</span><span class="sxs-lookup"><span data-stu-id="fc25a-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="fc25a-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc25a-104">Description</span></span>  
 <span data-ttu-id="fc25a-105">Esse contador é incrementado sempre que uma mensagem foi rejeitada devido a um problema de segurança não coberto pelo contador "Chamadas de segurança não autorizado".</span><span class="sxs-lookup"><span data-stu-id="fc25a-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="fc25a-106">Esses problemas incluem:</span><span class="sxs-lookup"><span data-stu-id="fc25a-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="fc25a-107">Não é possível ler o token de cliente da mensagem.</span><span class="sxs-lookup"><span data-stu-id="fc25a-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="fc25a-108">Token de cliente falha na autenticação (por exemplo, senha incorreta).</span><span class="sxs-lookup"><span data-stu-id="fc25a-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="fc25a-109">Falha na verificação de assinatura (por exemplo, a mensagem foi violada).</span><span class="sxs-lookup"><span data-stu-id="fc25a-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="fc25a-110">A mensagem é uma duplicata da anterior, o que pode ocorrer durante um ataque de repetição.</span><span class="sxs-lookup"><span data-stu-id="fc25a-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="fc25a-111">Ocorreu uma falha de descriptografia.</span><span class="sxs-lookup"><span data-stu-id="fc25a-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="fc25a-112">Alguns necessários faltam elementos (por exemplo, timestamp ausente ou bloquear os dados criptografados) da mensagem.</span><span class="sxs-lookup"><span data-stu-id="fc25a-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="fc25a-113">Ocorreram erros durante o handshake TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="fc25a-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
