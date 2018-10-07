---
title: Sessões seguras
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
author: BrucePerlerMS
ms.openlocfilehash: 09c261afb2c64a46fc1f4619c4ec6b2e87b3fbbf
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847380"
---
# <a name="secure-sessions"></a>Sessões seguras
Um recurso do Windows Communication Foundation (WCF) é sessões confiáveis que garantem que as mensagens são recebidas na ordem em que foram enviadas. Os tópicos nesta seção abordam as implicações de segurança a considerar ao criar uma sessão confiável. Para obter mais informações sobre as sessões confiáveis, consulte [sessões usando](../../../../docs/framework/wcf/using-sessions.md).  
  
> [!NOTE]
>  Quando a representação é necessária no Windows XP, use uma sessão segura sem um token de contexto de segurança com monitoração de estado (SCT). Quando SCTs com monitoração de estado são usados com a representação, um <xref:System.InvalidOperationException> é gerada. Para obter mais informações, consulte [cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="in-this-section"></a>Nesta seção  
  
|||  
|-|-|  
|[Sessões e conversas seguras](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|Sessões seguras e conversas seguras são sinônimos. Este tópico explica o funcionamento de uma conversa segura, e quando e por que usar o padrão.|  
|[Como criar uma sessão segura](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|Explica conceitos básicos da criação de uma sessão segura.|  
|[Como criar um token de contexto de segurança para uma sessão segura](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|Explica as etapas de criação de uma Web farm que manterá o estado e as sessões com clientes.|  
|[Considerações sobre segurança para sessões seguras](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|Descreve considerações especiais para sessões seguras.|  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Sessões, instanciação e simultaneidade](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [Serviços de design e implantação](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a>Consulte também  
 [Como habilitar a detecção de reprodução de mensagem](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [Ataques de reprodução](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [Como criar um serviço que requer sessões](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
