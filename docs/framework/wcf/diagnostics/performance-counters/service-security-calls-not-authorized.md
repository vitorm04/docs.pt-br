---
title: 'Serviço: Chamadas de segurança não autorizadas'
ms.date: 03/30/2017
ms.assetid: 3024b20a-5250-4bd1-a38c-c6d79f89610b
ms.openlocfilehash: a38b5e0eb467a5cad698fd6e3e01c0adef825d2f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773303"
---
# <a name="service-security-calls-not-authorized"></a>Serviço: Chamadas de segurança não autorizadas
Nome do contador: Segurança não autorizadas.  
  
## <a name="description"></a>Descrição  
 Esse contador é incrementado quando o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retorno do método `false`. Ele indica que a mensagem de entrada é de um usuário válido e protegidas adequadamente, mas o usuário não está autorizado a realizar tarefas específicas.
