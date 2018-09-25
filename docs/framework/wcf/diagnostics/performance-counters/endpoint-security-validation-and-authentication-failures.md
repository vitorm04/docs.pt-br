---
title: 'Ponto de extremidade: falhas de autenticação e validação de segurança'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
author: BrucePerlerMS
ms.openlocfilehash: f7cd2268eefa0176ab71a3d5d3bc82c178664742
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075090"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a><span data-ttu-id="31a16-102">Ponto de extremidade: falhas de autenticação e validação de segurança</span><span class="sxs-lookup"><span data-stu-id="31a16-102">Endpoint: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="31a16-103">Nome do contador: falhas de autenticação e validação de segurança</span><span class="sxs-lookup"><span data-stu-id="31a16-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="31a16-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="31a16-104">Description</span></span>  
 <span data-ttu-id="31a16-105">Esse contador é incrementado sempre que uma mensagem foi rejeitada devido a um problema de segurança não coberto pelo contador "Chamadas de segurança não autorizado".</span><span class="sxs-lookup"><span data-stu-id="31a16-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="31a16-106">Esses problemas incluem:</span><span class="sxs-lookup"><span data-stu-id="31a16-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="31a16-107">Não é possível ler o token de cliente da mensagem.</span><span class="sxs-lookup"><span data-stu-id="31a16-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="31a16-108">Token de cliente falha na autenticação (senha incorreta).</span><span class="sxs-lookup"><span data-stu-id="31a16-108">Client token has failed authentication (bad password).</span></span>  
  
-   <span data-ttu-id="31a16-109">Falha na verificação de assinatura (a mensagem foi violada).</span><span class="sxs-lookup"><span data-stu-id="31a16-109">Signature verification has failed (the message has been tampered).</span></span>  
  
-   <span data-ttu-id="31a16-110">A mensagem é uma duplicata da anterior, o que pode ocorrer durante um ataque de repetição.</span><span class="sxs-lookup"><span data-stu-id="31a16-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="31a16-111">Ocorreu uma falha de descriptografia.</span><span class="sxs-lookup"><span data-stu-id="31a16-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="31a16-112">Alguns elementos necessários (sem carimbo de hora ou bloco de dados criptografados) estão ausentes da mensagem.</span><span class="sxs-lookup"><span data-stu-id="31a16-112">Some required elements (missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="31a16-113">Ocorreram erros durante o handshake TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="31a16-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
