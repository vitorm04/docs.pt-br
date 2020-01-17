---
title: 'Ponto de extremidade: chamadas de segurança não autorizadas por segundo'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
ms.openlocfilehash: 8c287ef4c156bb0a76a4b1d08b0d70b40bd76229
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163170"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a>Ponto de extremidade: chamadas de segurança não autorizadas por segundo
Nome do contador: chamadas de segurança não autorizadas por segundo.  
  
## <a name="description"></a>Descrição  
 Número de mensagens de entrada em um segundo que são de um usuário válido e protegidas corretamente, mas o usuário não está autorizado a realizar tarefas específicas.  
  
 Esse contador é incrementado quando o método <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retorna `false`.  
  
 Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
