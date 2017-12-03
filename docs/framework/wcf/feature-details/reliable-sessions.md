---
title: "Sessões confiáveis"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 53bb63fbbcf92650085514118a5e9464ab2dea30
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="reliable-sessions"></a>Sessões confiáveis

Esta seção descreve o que um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sessão confiável está, que ela é usada, como e quando usar um, quais configurações de associação dão suporte a ele e ponteiros de práticas recomendadas. A tabela a seguir resume os detalhes sobre os pontos essenciais e tópicos relacionados nesta seção.

A sessão confiável [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece featrues garantem que as mensagens enviadas entre pontos de extremidade são transferidas em SOAP ou transporte intermediários e são entregues somente uma vez e, opcionalmente, na mesma ordem em que foram enviadas.

Para usar uma sessão confiável com um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo, use uma das associações fornecidas pelo sistema em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] que oferece suporte a uma sessão confiável por padrão ou como uma opção ou criar sua própria associação personalizada que ofereça suporte a sessão.

## <a name="in-this-section"></a>Nesta seção

[Visão geral de sessões confiáveis](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)   
Descreve sessões confiáveis, quando usá-los, as associações diferentes que dão suporte a sessões confiáveis, e como elas funcionam.

[Como: troca de mensagens dentro de uma sessão confiável](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)   
Descreve como criar uma sessão confiável via HTTP usando uma associação personalizada especificada na configuração.

[Como: proteger mensagens em sessões confiáveis](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md)   
Descreve como proteger uma sessão confiável.

[Como: criar uma associação de sessão confiável personalizada com HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)   
Descreve como criar uma sessão confiável por HTTPS.

[Práticas recomendadas para sessões confiáveis](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md)   
Descreve algumas das práticas recomendadas associadas usando uma sessão confiável.

## <a name="reference"></a>Referência

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a>Consulte também

[Sessões confiáveis e filas](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)   
[Sessões, instanciação e simultaneidade](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
