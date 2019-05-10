---
title: Falhas de Validação e Autenticação de Segurança
ms.date: 03/30/2017
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
ms.openlocfilehash: 0f061e1e12321dbe8034d7619830f71717ca9d1f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664970"
---
# <a name="security-validation-and-authentication-failures"></a>Falhas de Validação e Autenticação de Segurança
Nome do contador: Falhas de Validação e Autenticação de Segurança  
  
## <a name="description"></a>Descrição  
 Esse contador é incrementado sempre que uma mensagem foi rejeitada devido a um problema de segurança não coberto pelo contador "Chamadas de segurança não autorizado". Esses problemas incluem:  
  
- Não é possível ler o token de cliente da mensagem.  
  
- Token de cliente falha na autenticação (por exemplo, senha incorreta).  
  
- Falha na verificação de assinatura (por exemplo, a mensagem foi violada).  
  
- A mensagem é uma duplicata da anterior, o que pode ocorrer durante um ataque de repetição.  
  
- Ocorreu uma falha de descriptografia.  
  
- Alguns necessários elementos (por exemplo, carimbo de hora ausente ou bloquear os dados criptografados) estão ausentes da mensagem.  
  
- Ocorreram erros durante o handshake TLSNEGO/SPNEGO.
