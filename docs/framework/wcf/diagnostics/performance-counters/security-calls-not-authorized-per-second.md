---
title: Chamadas de Segurança Não Autorizadas por Segundo
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 4d4970c6f6552163114b33a34ae87c6ed56b5e13
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44337584"
---
# <a name="security-calls-not-authorized-per-second"></a>Chamadas de Segurança Não Autorizadas por Segundo
Nome do contador: Chamadas de segurança não autorizadas por segundo.  
  
## <a name="description"></a>Descrição  
 Número de chamadas com falha de autorização nesta operação em um segundo.  
  
 Esse contador é incrementado quando o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retorno do método `false`. Ele indica que a mensagem de entrada é de um usuário válido e protegidas adequadamente, mas o usuário não está autorizado a realizar tarefas específicas.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0) / ((1!D 1 - D 0) / F)
