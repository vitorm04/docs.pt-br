---
title: 'Serviço: falhas de autenticação e validação de segurança'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: 399249926bcb1383fd33f60510c2c212c6f4261c
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204575"
---
# <a name="service-security-validation-and-authentication-failures"></a><span data-ttu-id="05118-102">Serviço: falhas de autenticação e validação de segurança</span><span class="sxs-lookup"><span data-stu-id="05118-102">Service: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="05118-103">Nome do contador: falhas de validação e autenticação de segurança</span><span class="sxs-lookup"><span data-stu-id="05118-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="05118-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="05118-104">Description</span></span>  
 <span data-ttu-id="05118-105">Esse contador é incrementado sempre que uma mensagem é rejeitada devido a um problema de segurança não coberto pelo contador "chamadas de segurança não autorizadas".</span><span class="sxs-lookup"><span data-stu-id="05118-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="05118-106">Esses problemas incluem:</span><span class="sxs-lookup"><span data-stu-id="05118-106">Such problems include:</span></span>  
  
- <span data-ttu-id="05118-107">O token do cliente não pode ser lido a partir da mensagem.</span><span class="sxs-lookup"><span data-stu-id="05118-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="05118-108">Falha na autenticação do token do cliente (por exemplo, senha inadequada).</span><span class="sxs-lookup"><span data-stu-id="05118-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="05118-109">Falha na verificação da assinatura (por exemplo, a mensagem foi violada).</span><span class="sxs-lookup"><span data-stu-id="05118-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="05118-110">A mensagem é uma duplicata de uma anterior, o que pode ocorrer durante um ataque de repetição.</span><span class="sxs-lookup"><span data-stu-id="05118-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="05118-111">Ocorreu uma falha de descriptografia.</span><span class="sxs-lookup"><span data-stu-id="05118-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="05118-112">Alguns elementos necessários (por exemplo, carimbo de data/hora ausente ou bloco de dados criptografados) estão ausentes da mensagem.</span><span class="sxs-lookup"><span data-stu-id="05118-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="05118-113">Ocorreram erros durante o handshake TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="05118-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
