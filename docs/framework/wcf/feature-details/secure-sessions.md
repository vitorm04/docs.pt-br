---
title: Sessões seguras
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: d511a45d990e441c5dcfd8405794ec937c0278d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966070"
---
# <a name="secure-sessions"></a>Sessões seguras
Um recurso do Windows Communication Foundation (WCF) é uma sessão confiável que garante que as mensagens sejam recebidas na ordem em que foram enviadas. Os tópicos nesta seção discutem as implicações de segurança a serem consideradas ao criar uma sessão confiável. Para obter mais informações sobre sessões confiáveis, consulte [usando sessões](../../../../docs/framework/wcf/using-sessions.md).  
  
> [!NOTE]
> Quando a representação é necessária no Windows XP, use uma sessão segura sem um símbolo de contexto de segurança com estado (SCT). Quando SCTs com estado são usados com representação, <xref:System.InvalidOperationException> um é gerado. Para obter mais informações, consulte [cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="in-this-section"></a>Nesta seção  
  
|||  
|-|-|  
|[Sessões e conversas seguras](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|Conversas seguras e sessões seguras são sinônimos. Este tópico explica como funciona uma conversa segura e quando e por que usar o padrão.|  
|[Como: Criar uma sessão segura](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|Percorre as noções básicas da criação de uma sessão segura.|  
|[Como: Criar um token de contexto de segurança para uma sessão segura](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|Percorre as etapas de criação de um Web farm que manterá o estado e as sessões com clientes.|  
|[Considerações sobre segurança para sessões seguras](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|Descreve considerações especiais para sessões seguras.|  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Sessões, instanciação e simultaneidade](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [Serviços de design e implantação](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a>Consulte também

- [Como: Habilitar detecção de reprodução de mensagem](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)
- [Ataques de reprodução](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [Como: Criar um serviço que requer sessões](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
