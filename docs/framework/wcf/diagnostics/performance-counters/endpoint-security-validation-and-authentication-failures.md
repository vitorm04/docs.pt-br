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
ms.openlocfilehash: 7d1f05ddc4b0fcf93c87e69932f860f3c7e2ff85
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-security-validation-and-authentication-failures"></a>Ponto de extremidade: falhas de autenticação e validação de segurança
Nome do contador: falhas de autenticação e validação de segurança  
  
## <a name="description"></a>Descrição  
 Esse contador é incrementado sempre que uma mensagem foi rejeitada devido a um problema de segurança não coberto pelo contador "Chamadas de segurança não autorizado". Esses problemas incluem:  
  
-   Não é possível ler o token de cliente da mensagem.  
  
-   Token de cliente falha na autenticação (senha incorreta).  
  
-   Falha na verificação de assinatura (a mensagem foi violada).  
  
-   A mensagem é uma duplicata da anterior, o que pode ocorrer durante um ataque de repetição.  
  
-   Ocorreu uma falha de descriptografia.  
  
-   Alguns elementos necessários (sem o carimbo de hora ou bloco de dados criptografados) estão faltando na mensagem.  
  
-   Ocorreram erros durante o handshake TLSNEGO/SPNEGO.
