---
title: 'Serviço: Falhas de Validação e Autenticação de Segurança por Segundo'
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
ms.openlocfilehash: 97752fbd4ff38c40917c132fddfe3798a7ee6766
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998316"
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a>Serviço: Falhas de Validação e Autenticação de Segurança por Segundo
Nome do contador: Validação de segurança e falhas de autenticação por segundo.  
  
## <a name="description"></a>Descrição  
 Esse contador é incrementado sempre que uma mensagem foi rejeitada devido a um problema de segurança não coberto pelo contador "Chamadas de segurança não autorizado". Esses problemas incluem:  
  
- Não é possível ler o token de cliente da mensagem.  
  
- Token de cliente falha na autenticação (por exemplo, senha incorreta).  
  
- Falha na verificação de assinatura (por exemplo, a mensagem foi violada).  
  
- A mensagem é uma duplicata da anterior, o que pode ocorrer durante um ataque de repetição.  
  
- Ocorreu uma falha de descriptografia.  
  
- Alguns necessários elementos (por exemplo, carimbo de hora ausente ou bloquear os dados criptografados) estão ausentes da mensagem.  
  
- Ocorreram erros durante o handshake TLSNEGO/SPNEGO.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir,  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
