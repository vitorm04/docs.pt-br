---
title: 'Serviço: chamadas de segurança não autorizadas por segundo'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
ms.openlocfilehash: 964eff97a58ab7d5a68dbc1891473ae8d04a50ad
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163872"
---
# <a name="service-security-calls-not-authorized-per-second"></a>Serviço: chamadas de segurança não autorizadas por segundo
Nome do contador: chamadas de segurança não autorizadas por segundo  
  
## <a name="description"></a>Descrição  
 Número de mensagens de entrada em um segundo, que são de um usuário válido e protegidas corretamente, mas o usuário não está autorizado a realizar tarefas específicas.  
  
 Esse contador é incrementado quando o método <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retorna `false`.  
  
 Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
