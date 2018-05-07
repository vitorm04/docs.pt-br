---
title: Sessões confiáveis
ms.date: 03/30/2017
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
ms.openlocfilehash: 396c76cbdb8eada881a5c87edfc2500dcdab3ad4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="reliable-sessions"></a>Sessões confiáveis

Esta seção descreve quais um Windows Communication Foundation (WCF) é de sessão confiável, a que ela é usada, como e quando usar um, quais configurações de associação dão suporte a ele e ponteiros de práticas recomendadas. A tabela a seguir resume os detalhes sobre os pontos essenciais e tópicos relacionados nesta seção.

A sessão confiável WCF fornece featrues garantem que as mensagens enviadas entre pontos de extremidade são transferidas em SOAP ou transporte intermediários e são entregues somente uma vez e, opcionalmente, na mesma ordem em que foram enviadas.

Para usar uma sessão confiável com um aplicativo WCF, use uma das ligações de fornecido pelo sistema no WCF que dão suporte a uma sessão confiável por padrão ou como uma opção ou criar sua própria associação personalizada que ofereça suporte a sessão.

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
