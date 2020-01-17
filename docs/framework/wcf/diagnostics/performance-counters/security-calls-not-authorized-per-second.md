---
title: Chamadas de Segurança Não Autorizadas por Segundo
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
ms.openlocfilehash: 2986ba241ef9b6c110a4742f77320469cdf5f07a
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163924"
---
# <a name="security-calls-not-authorized-per-second"></a>Chamadas de Segurança Não Autorizadas por Segundo
Nome do contador: chamadas de segurança não autorizadas por segundo.  
  
## <a name="description"></a>Descrição  
 Número de chamadas que falharam na autorização nesta operação em um segundo.  
  
 Esse contador é incrementado quando o método <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retorna `false`. Isso indica que a mensagem de entrada é de um usuário válido e protegida corretamente, mas o usuário não está autorizado a realizar tarefas específicas.  
  
 Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
