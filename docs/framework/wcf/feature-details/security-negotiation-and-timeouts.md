---
title: "Negociação de segurança e tempo limite"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: b4d0b2953a91040c37afe88d9499fd4be1970f31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="security-negotiation-and-timeouts"></a>Negociação de segurança e tempo limite
Quando os clientes e serviços de autenticação, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] suporta o modo em que a credencial de serviço é negociada como parte da autenticação. Nesses cenários, uma troca potencialmente vários trecho ocorre entre o cliente e o serviço para propagar as credenciais do serviço ao cliente. O <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> propriedade controla quanto tempo a troca de multi-segmento de pode demorar para ser concluída. No entanto, esse tempo limite se aplica somente se o exchange leva mais que uma única solicitação-resposta. Em casos onde a negociação é realizada em uma única viagem de ida e, o tempo limite não se aplica.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [Como: definir uma máxima do relógio](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
