---
title: Negociação de segurança e tempo limite
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: a02c9d7b42eadf9a5ce9af8022fe292d6c23249c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748285"
---
# <a name="security-negotiation-and-timeouts"></a>Negociação de segurança e tempo limite
Quando os clientes e serviços de autenticação, o Windows Communication Foundation (WCF) suporta um modo em que a credencial de serviço é negociada como parte da autenticação. Nesses cenários, uma troca potencialmente multi-segmentos ocorre entre o cliente e o serviço para propagar a credencial de serviço ao cliente. O <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> propriedade controla o quanto o exchange multi-segmentos pode demorar para ser concluída. No entanto, esse tempo limite se aplica somente se o exchange, na verdade, demorar mais que uma única solicitação-resposta. Em casos em que a negociação é realizada em uma única ida e volta, o tempo limite não se aplica.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Como: Definir uma distorção máxima do relógio](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
