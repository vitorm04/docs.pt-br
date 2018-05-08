---
title: Negociação de segurança e tempo limite
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 508d648acf148f13076327bb312d0a0b08471ac1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="security-negotiation-and-timeouts"></a>Negociação de segurança e tempo limite
Ao autenticam clientes e serviços, Windows Communication Foundation (WCF) suporta o modo em que a credencial de serviço é negociada como parte da autenticação. Nesses cenários, uma troca potencialmente vários trecho ocorre entre o cliente e o serviço para propagar as credenciais do serviço ao cliente. O <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> propriedade controla quanto tempo a troca de multi-segmento de pode demorar para ser concluída. No entanto, esse tempo limite se aplica somente se o exchange leva mais que uma única solicitação-resposta. Em casos onde a negociação é realizada em uma única viagem de ida e, o tempo limite não se aplica.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [Como definir uma distorção máxima do relógio](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
