---
title: 'Serviço: Falhas de Validação e Autenticação de Segurança'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: 5843d25eb26bdd9facc324a2af50c6b02c5ad7c8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613595"
---
# <a name="service-security-validation-and-authentication-failures"></a><span data-ttu-id="d5e14-102">Serviço: Falhas de Validação e Autenticação de Segurança</span><span class="sxs-lookup"><span data-stu-id="d5e14-102">Service: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="d5e14-103">Nome do contador: Falhas de Validação e Autenticação de Segurança</span><span class="sxs-lookup"><span data-stu-id="d5e14-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="d5e14-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="d5e14-104">Description</span></span>  
 <span data-ttu-id="d5e14-105">Esse contador é incrementado sempre que uma mensagem foi rejeitada devido a um problema de segurança não coberto pelo contador "Chamadas de segurança não autorizado".</span><span class="sxs-lookup"><span data-stu-id="d5e14-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="d5e14-106">Esses problemas incluem:</span><span class="sxs-lookup"><span data-stu-id="d5e14-106">Such problems include:</span></span>  
  
- <span data-ttu-id="d5e14-107">Não é possível ler o token de cliente da mensagem.</span><span class="sxs-lookup"><span data-stu-id="d5e14-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="d5e14-108">Token de cliente falha na autenticação (por exemplo, senha incorreta).</span><span class="sxs-lookup"><span data-stu-id="d5e14-108">Client token has failed authentication (for example,, bad password).</span></span>  
  
- <span data-ttu-id="d5e14-109">Falha na verificação de assinatura (por exemplo, a mensagem foi violada).</span><span class="sxs-lookup"><span data-stu-id="d5e14-109">Signature verification has failed (for example,, the message has been tampered).</span></span>  
  
- <span data-ttu-id="d5e14-110">A mensagem é uma duplicata da anterior, o que pode ocorrer durante um ataque de repetição.</span><span class="sxs-lookup"><span data-stu-id="d5e14-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="d5e14-111">Ocorreu uma falha de descriptografia.</span><span class="sxs-lookup"><span data-stu-id="d5e14-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="d5e14-112">Alguns necessários elementos (por exemplo, carimbo de hora ausente ou bloquear os dados criptografados) estão ausentes da mensagem.</span><span class="sxs-lookup"><span data-stu-id="d5e14-112">Some required elements (for example,, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="d5e14-113">Ocorreram erros durante o handshake TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="d5e14-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
