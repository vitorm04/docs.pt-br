---
title: 'Ponto de extremidade: chamadas de segurança não autorizadas por segundo'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 4cefdd7480c7d0e9475b1883e603d9db1f287d4a
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44259737"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a>Ponto de extremidade: chamadas de segurança não autorizadas por segundo
Nome do contador: Chamadas de segurança não autorizadas por segundo.  
  
## <a name="description"></a>Descrição  
 Número de mensagens de entrada em um segundo de um usuário válido e protegidas adequadamente, mas o usuário não está autorizado a realizar tarefas específicas.  
  
 Esse contador é incrementado quando o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retorno do método `false`.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.  
  
 (N 1 - N 0) / ((1!D 1 - D 0) / F)
