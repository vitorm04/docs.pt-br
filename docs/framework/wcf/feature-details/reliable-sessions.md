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
ms.openlocfilehash: 1d87f6f4d94763dc8f6ac7e929c22b17940097ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735416"
---
# <a name="reliable-sessions"></a>Sessões confiáveis

Esta seção descreve o que um Windows Communication Foundation (WCF) é de sessão confiável, a que ela é usada, como e quando usar um, quais configurações de associação dão suporte a ele e ponteiros de práticas recomendadas. A tabela a seguir resume os detalhes sobre os pontos essenciais e tópicos relacionados nesta seção.

A sessão confiável WCF fornece featrues garantindo que as mensagens enviadas entre pontos de extremidade são transferidas em SOAP ou transporte intermediários e são entregues somente uma vez e, opcionalmente, na mesma ordem em que foram enviadas.

Para usar uma sessão confiável com um aplicativo WCF, use uma das ligações de fornecido pelo sistema no WCF que dão suporte a uma sessão confiável por padrão, ou como uma opção ou criar sua própria associação personalizada que dá suporte a sessão.

## <a name="in-this-section"></a>Nesta seção

[Visão geral de sessões confiáveis](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)   
Descreve sessões confiáveis, quando usá-los, as associações diferentes que dão suporte a sessões confiáveis, e como eles funcionam.

[Como: Troca de mensagens dentro de uma sessão confiável](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)   
Descreve como criar uma sessão confiável via HTTP por meio de uma ligação personalizada especificada na configuração.

[Como: Mensagens seguras em sessões confiáveis](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md)   
Descreve como proteger uma sessão confiável.

[Como: Criar uma associação de sessão confiável personalizada com HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)   
Descreve como criar uma sessão confiável por HTTPS.

[Práticas recomendadas para sessões confiáveis](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md)   
Descreve algumas das práticas recomendadas associadas ao uso de uma sessão confiável.

## <a name="reference"></a>Referência

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a>Consulte também

- [Sessões confiáveis e filas](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
- [Sessões, instanciação e simultaneidade](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
