---
title: 'Ponto de extremidade: mensagens de segurança não autorizadas'
ms.date: 03/30/2017
ms.assetid: d25095ff-9ff0-4c69-a674-4e6a9fe3f4dc
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b449aaad65f01a5f4835f8335543220383543984
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="endpoint-security-calls-not-authorized"></a>Ponto de extremidade: mensagens de segurança não autorizadas
Nome do contador: Chamadas de segurança não autorizadas.  
  
## <a name="description"></a>Descrição  
 Esse contador é incrementado quando o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> método retornará `false`. Ele indica que a mensagem de entrada é de um usuário válido e protegido adequadamente, mas o usuário não está autorizado a realizar tarefas específicas.
