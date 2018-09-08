---
title: 'Serviço: chamadas de segurança não autorizadas por segundo'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f2c921991f059d7dfe5661dfe688ec9675d0d5fe
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210631"
---
# <a name="service-security-calls-not-authorized-per-second"></a>Serviço: chamadas de segurança não autorizadas por segundo
Nome do contador: segurança chamadas não autorizadas por segundo  
  
## <a name="description"></a>Descrição  
 Número de mensagens de entrada em um segundo, que são de um usuário válido e protegidas adequadamente, mas o usuário não está autorizado a realizar tarefas específicas.  
  
 Esse contador é incrementado quando o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retorno do método `false`.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkId=94649), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0) / ((1!D 1 - D 0) / F)
