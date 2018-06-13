---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.date: 03/30/2017
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
ms.openlocfilehash: f79f5703c621951029f3e7f6a36a3d0ebeca58a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33477445"
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a>System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
Falha ao receber uma mensagem por um canal HTTP.  
  
## <a name="description"></a>Descrição  
 Este rastreamento pode ser emitido como um aviso ou erro. Em ambos os casos, o rastreamento é emitido quando um ouvinte compatível não foi encontrado para uma solicitação HTTP de entrada e a solicitação HTTP é descartada. Isso pode acontecer porque o verbo HTTP da solicitação não foi reconhecido por qualquer ouvinte HTTP, ou porque nenhum ouvinte foi escutando no endereço a solicitação foi direcionada para. O rastreamento é emitido como um aviso no caso de auto-hospedado e como um erro quando o serviço é hospedado no IIS.  
  
## <a name="see-also"></a>Consulte também  
 [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
