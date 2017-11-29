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
ms.openlocfilehash: c1d448d709c7ad20e9d08a291f5a38546cd93ce4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="security-validation-and-authentication-failures"></a><span data-ttu-id="b0a30-102">Falhas de autenticação e validação de segurança</span><span class="sxs-lookup"><span data-stu-id="b0a30-102">Security Validation and Authentication Failures</span></span>
<span data-ttu-id="b0a30-103">Nome do contador: falhas de autenticação e validação de segurança</span><span class="sxs-lookup"><span data-stu-id="b0a30-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="b0a30-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0a30-104">Description</span></span>  
 <span data-ttu-id="b0a30-105">Esse contador é incrementado sempre que uma mensagem foi rejeitada devido a um problema de segurança não coberto pelo contador "Chamadas de segurança não autorizado".</span><span class="sxs-lookup"><span data-stu-id="b0a30-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="b0a30-106">Esses problemas incluem:</span><span class="sxs-lookup"><span data-stu-id="b0a30-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="b0a30-107">Não é possível ler o token de cliente da mensagem.</span><span class="sxs-lookup"><span data-stu-id="b0a30-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="b0a30-108">Token de cliente falha na autenticação (por exemplo, senha incorreta).</span><span class="sxs-lookup"><span data-stu-id="b0a30-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="b0a30-109">Falha na verificação de assinatura (por exemplo, a mensagem foi violada).</span><span class="sxs-lookup"><span data-stu-id="b0a30-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="b0a30-110">A mensagem é uma duplicata da anterior, o que pode ocorrer durante um ataque de repetição.</span><span class="sxs-lookup"><span data-stu-id="b0a30-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="b0a30-111">Ocorreu uma falha de descriptografia.</span><span class="sxs-lookup"><span data-stu-id="b0a30-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="b0a30-112">Alguns necessários faltam elementos (por exemplo, timestamp ausente ou bloquear os dados criptografados) da mensagem.</span><span class="sxs-lookup"><span data-stu-id="b0a30-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="b0a30-113">Ocorreram erros durante o handshake TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="b0a30-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
