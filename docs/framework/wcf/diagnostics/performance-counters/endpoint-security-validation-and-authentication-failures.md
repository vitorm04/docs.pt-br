---
title: "Ponto de extremidade: falhas de autenticação e validação de segurança"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 5bd38ae0e3506397378b7c59976c6c692045054d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-security-validation-and-authentication-failures"></a><span data-ttu-id="eb606-102">Ponto de extremidade: falhas de autenticação e validação de segurança</span><span class="sxs-lookup"><span data-stu-id="eb606-102">Endpoint: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="eb606-103">Nome do contador: falhas de autenticação e validação de segurança</span><span class="sxs-lookup"><span data-stu-id="eb606-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="eb606-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb606-104">Description</span></span>  
 <span data-ttu-id="eb606-105">Esse contador é incrementado sempre que uma mensagem foi rejeitada devido a um problema de segurança não coberto pelo contador "Chamadas de segurança não autorizado".</span><span class="sxs-lookup"><span data-stu-id="eb606-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="eb606-106">Esses problemas incluem:</span><span class="sxs-lookup"><span data-stu-id="eb606-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="eb606-107">Não é possível ler o token de cliente da mensagem.</span><span class="sxs-lookup"><span data-stu-id="eb606-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="eb606-108">Token de cliente falha na autenticação (senha incorreta).</span><span class="sxs-lookup"><span data-stu-id="eb606-108">Client token has failed authentication (bad password).</span></span>  
  
-   <span data-ttu-id="eb606-109">Falha na verificação de assinatura (a mensagem foi violada).</span><span class="sxs-lookup"><span data-stu-id="eb606-109">Signature verification has failed (the message has been tampered).</span></span>  
  
-   <span data-ttu-id="eb606-110">A mensagem é uma duplicata da anterior, o que pode ocorrer durante um ataque de repetição.</span><span class="sxs-lookup"><span data-stu-id="eb606-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="eb606-111">Ocorreu uma falha de descriptografia.</span><span class="sxs-lookup"><span data-stu-id="eb606-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="eb606-112">Alguns elementos necessários (sem o carimbo de hora ou bloco de dados criptografados) estão faltando na mensagem.</span><span class="sxs-lookup"><span data-stu-id="eb606-112">Some required elements (missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="eb606-113">Ocorreram erros durante o handshake TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="eb606-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
