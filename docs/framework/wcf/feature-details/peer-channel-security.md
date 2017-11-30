---
title: "Segurança de canal par"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c59b164-3729-44f0-a967-f247c42de662
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: afe4252a56802ff2796f947afa31a5871f29223e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="peer-channel-security"></a>Segurança de canal par
Canal par permite uma variedade de tipos de aplicativo distribuído que dependem de mensagens entre vários participantes. Alguns exemplos incluem a distribuição de conteúdo de escala da Internet, em que uma fonte confiável distribui o conteúdo (por exemplo, mídia ou atualizações de software), um grupo de amigos do exchange músicas e fotos ou uma equipe de colegas em colaboração editar um documento. Cada um desses cenários exige um modelo de segurança exclusivo. O modelo de segurança de canal par foi desenvolvido para atender a esses cenários e fornece um modelo de segurança para as respectivas necessidades de modelos diferentes de identidade, autenticação e autorização.  
  
## <a name="security-scenarios"></a>Cenários de segurança  
 Um cenário de distribuição de conteúdo requer que cada destinatário conteúdo identificar a origem de conteúdo. Devido à natureza distribuída do cenário, não é sempre possível conhecer e confia os intermediários que as mensagens de processo ou interceptação. Para efetivamente atenuar a ameaça que pode violar um intermediário confiável as mensagens, aplicativos podem proteger a mensagem no remetente, para que todas as tentativas de violação facilmente detectadas. Nesse caso, dependendo da confidencialidade do conteúdo, a criptografia pode ser necessária.  
  
 Cenários de colaboração como grupo colaboração de documentos geralmente requerem que cada membro que participam da sessão ser identificado individualmente e autenticado. Isso significa que um mecanismo para definir grupos de usuário e autenticar em relação a esses grupos é necessário ter uma sessão segura. Além disso, os aplicativos podem exigir rastreamento cada mensagem pela autenticação no nível da mensagem. Esses tipos de aplicativos, o desempenho pode ser sacrificado para um esquema de segurança mais forte.  
  
 Uma sessão de comunicação entre um grupo de usuários casuais pode exigir modelos de segurança informal, como dados de Conhecimento de um segredo comuns entre o grupo. Para esses tipos de aplicativos, com um modelo de segurança que é conveniente para estabelecer e configurar é mais importante do que com a forma mais forte de autenticação ou fornecer medidas de não-repúdio. Nessas situações, um mecanismo de autenticação baseada em senha ajuda a proteger a camada de comunicação enquanto ainda permite que para autenticação de mensagem. Segurança baseada em senha é a configuração padrão de canal par.  
  
## <a name="token-types"></a>Tipos de token  
 Canal par reconhece um único tipo de token para identificação de alta segurança, certificados x. 509, que fornecem um modelo de identidade de alta segurança com base no tipo de autenticação e autorização que pode ser implementada. Integridade e confidencialidade facilmente são fornecidos usando certificados. No entanto, os certificados x. 509 podem ser difícil de usar e implantar.  
  
 Canal par também oferece suporte para aplicativos simples com o uso de senhas. Aplicativos podem optar por configurar grupos de ponto a ponto rápido e simples com base em uma senha fornecida. Nesse caso, um proprietário do grupo decide e a senha, se comunica com membros. Cada membro deve entrar usando essa senha antes que elas possam ingressar a sessão. Senhas podem ser usadas apenas para permitir a entrada para a sessão; eles não podem ser usados para realizar a autenticação de mensagem. Isso ocorre porque um token simétrico que compartilham um grupo de pontos é difícil e inadequada usar para autenticação de origem.  
  
## <a name="security-model"></a>Modelo de segurança  
 Canal par fornece a capacidade de proteger os links individuais entre pares. Isso significa que a mensagem nunca flui em um link inseguro (da perspectiva do aplicativo). Internamente, cada link (um canal de transporte entre dois pontos) é protegida usando a segurança de camada de transporte (TLS). Isso significa que, quando um remetente compõe e envia uma mensagem, ela é enviada por transporte seguro para cada um dos seus pares de imediatos, que a mensagem de acesso e, por sua vez enviar a mensagem para seus colegas imediatas através de conexões seguras. Essa segurança só funciona com transporte nível e é independente dos modelos de segurança de mensagem.  
  
 Canal par também fornece uma maneira de proteger mensagens independentemente a segurança de transporte usado. Neste modelo, a mensagem é protegida na fonte, usando o token de segurança da fonte, embora os certificados x. 509 no momento, somente têm suporte. A mensagem protegida, em seguida, é transmitida pela rede ponto a ponto. Cada ponto de recebimento pode verificar a autenticidade da origem. Observe que a mensagem é protegida para que não podem violar intermediários com ele.  
  
 Para obter a confidencialidade, aplicativos podem empregar segurança de transporte com esquemas de associação de grupo de alta segurança para evitar acesso não autorizado à mensagem.  
  
 Canal par não exigem um modelo de identidade específico como o aplicativo escolhe um dos tipos de token com suporte. Aplicativos possuem completamente o ciclo de vida dessas identidades e decisões de autenticação.  
  
## <a name="see-also"></a>Consulte também  
 [Protegendo aplicativos de canal par](../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [Conceitos de canal par](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)  
 [Criando um aplicativo de canal par](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
