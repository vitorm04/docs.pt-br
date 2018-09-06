---
title: 'Serviço: falhas de autenticação e validação de segurança por segundo'
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: fb0d4fdebf07dacfa7f33d8645332348270128e4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43884833"
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a>Serviço: falhas de autenticação e validação de segurança por segundo
Nome do contador: validação de segurança e autenticação de falhas por segundo.  
  
## <a name="description"></a>Descrição  
 Esse contador é incrementado sempre que uma mensagem foi rejeitada devido a um problema de segurança não coberto pelo contador "Chamadas de segurança não autorizado". Esses problemas incluem:  
  
-   Não é possível ler o token de cliente da mensagem.  
  
-   Token de cliente falha na autenticação (por exemplo, senha incorreta).  
  
-   Falha na verificação de assinatura (por exemplo, a mensagem foi violada).  
  
-   A mensagem é uma duplicata da anterior, o que pode ocorrer durante um ataque de repetição.  
  
-   Ocorreu uma falha de descriptografia.  
  
-   Alguns necessários elementos (por exemplo, carimbo de hora ausente ou bloquear os dados criptografados) estão ausentes da mensagem.  
  
-   Ocorreram erros durante o handshake TLSNEGO/SPNEGO.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir,  
  
 (N 1 - N 0) / ((1!D 1 - D 0) / F)
