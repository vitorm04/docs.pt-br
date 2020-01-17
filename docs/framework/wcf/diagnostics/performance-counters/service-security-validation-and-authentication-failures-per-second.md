---
title: 'Serviço: falhas de autenticação e validação de segurança por segundo'
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
ms.openlocfilehash: f3f27100afb7390a68d99421cad6f43d9abaccd5
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163859"
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a>Serviço: falhas de autenticação e validação de segurança por segundo
Nome do contador: falhas de validação e autenticação de segurança por segundo.  
  
## <a name="description"></a>Descrição  
 Esse contador é incrementado sempre que uma mensagem é rejeitada devido a um problema de segurança não coberto pelo contador "chamadas de segurança não autorizadas". Esses problemas incluem:  
  
- O token do cliente não pode ser lido a partir da mensagem.  
  
- Falha na autenticação do token do cliente (por exemplo, senha inadequada).  
  
- Falha na verificação da assinatura (por exemplo, a mensagem foi violada).  
  
- A mensagem é uma duplicata de uma anterior, o que pode ocorrer durante um ataque de repetição.  
  
- Ocorreu uma falha de descriptografia.  
  
- Alguns elementos necessários (por exemplo, carimbo de data/hora ausente ou bloco de dados criptografados) estão ausentes da mensagem.  
  
- Ocorreram erros durante o handshake TLSNEGO/SPNEGO.  
  
 Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir,  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
