---
title: 'Ponto de extremidade: Falhas de Validação e Autenticação de Segurança'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
ms.openlocfilehash: e69549a276e2f9cece966dd44f6a1b3a3d3cb59f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916316"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a><span data-ttu-id="54e9b-102">Ponto de extremidade: Falhas de Validação e Autenticação de Segurança</span><span class="sxs-lookup"><span data-stu-id="54e9b-102">Endpoint: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="54e9b-103">Nome do contador: Falhas de Validação e Autenticação de Segurança</span><span class="sxs-lookup"><span data-stu-id="54e9b-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="54e9b-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="54e9b-104">Description</span></span>  
 <span data-ttu-id="54e9b-105">Esse contador é incrementado sempre que uma mensagem foi rejeitada devido a um problema de segurança não coberto pelo contador "Chamadas de segurança não autorizado".</span><span class="sxs-lookup"><span data-stu-id="54e9b-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="54e9b-106">Esses problemas incluem:</span><span class="sxs-lookup"><span data-stu-id="54e9b-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="54e9b-107">Não é possível ler o token de cliente da mensagem.</span><span class="sxs-lookup"><span data-stu-id="54e9b-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="54e9b-108">Token de cliente falha na autenticação (senha incorreta).</span><span class="sxs-lookup"><span data-stu-id="54e9b-108">Client token has failed authentication (bad password).</span></span>  
  
-   <span data-ttu-id="54e9b-109">Falha na verificação de assinatura (a mensagem foi violada).</span><span class="sxs-lookup"><span data-stu-id="54e9b-109">Signature verification has failed (the message has been tampered).</span></span>  
  
-   <span data-ttu-id="54e9b-110">A mensagem é uma duplicata da anterior, o que pode ocorrer durante um ataque de repetição.</span><span class="sxs-lookup"><span data-stu-id="54e9b-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="54e9b-111">Ocorreu uma falha de descriptografia.</span><span class="sxs-lookup"><span data-stu-id="54e9b-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="54e9b-112">Alguns elementos necessários (sem carimbo de hora ou bloco de dados criptografados) estão ausentes da mensagem.</span><span class="sxs-lookup"><span data-stu-id="54e9b-112">Some required elements (missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="54e9b-113">Ocorreram erros durante o handshake TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="54e9b-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
