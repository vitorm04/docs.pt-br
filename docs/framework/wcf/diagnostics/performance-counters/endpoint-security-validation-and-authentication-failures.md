---
title: 'Ponto de extremidade: falhas de autenticação e validação de segurança'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
author: BrucePerlerMS
ms.openlocfilehash: f7cd2268eefa0176ab71a3d5d3bc82c178664742
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47194031"
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
  
-   Alguns elementos necessários (sem carimbo de hora ou bloco de dados criptografados) estão ausentes da mensagem.  
  
-   Ocorreram erros durante o handshake TLSNEGO/SPNEGO.
