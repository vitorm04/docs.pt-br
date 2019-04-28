---
title: Falhas de Validação e Autenticação de Segurança
ms.date: 03/30/2017
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
ms.openlocfilehash: 32a7d41f93dd99f1950a073e1cac1b62177ff6c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916039"
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
