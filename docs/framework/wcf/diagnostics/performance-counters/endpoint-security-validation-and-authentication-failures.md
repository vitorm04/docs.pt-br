---
title: 'Ponto de extremidade: Falhas de Validação e Autenticação de Segurança'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
ms.openlocfilehash: 9e0192ea600bb52abd555f2f83cfe8e96d3fe203
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619334"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a>Ponto de extremidade: Falhas de Validação e Autenticação de Segurança
Nome do contador: Falhas de Validação e Autenticação de Segurança  
  
## <a name="description"></a>Descrição  
 Esse contador é incrementado sempre que uma mensagem foi rejeitada devido a um problema de segurança não coberto pelo contador "Chamadas de segurança não autorizado". Esses problemas incluem:  
  
- Não é possível ler o token de cliente da mensagem.  
  
- Token de cliente falha na autenticação (senha incorreta).  
  
- Falha na verificação de assinatura (a mensagem foi violada).  
  
- A mensagem é uma duplicata da anterior, o que pode ocorrer durante um ataque de repetição.  
  
- Ocorreu uma falha de descriptografia.  
  
- Alguns elementos necessários (sem carimbo de hora ou bloco de dados criptografados) estão ausentes da mensagem.  
  
- Ocorreram erros durante o handshake TLSNEGO/SPNEGO.
