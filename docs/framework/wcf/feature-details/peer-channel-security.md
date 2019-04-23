---
title: Segurança de canal par
ms.date: 03/30/2017
ms.assetid: 2c59b164-3729-44f0-a967-f247c42de662
ms.openlocfilehash: bc17c35bf088472cfbf36b2c6d7c868c8cc85f20
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129448"
---
# <a name="peer-channel-security"></a>Segurança de canal par
Canal par permite uma variedade de tipos de aplicativo distribuído que dependem de mensagens entre vários participantes. Alguns exemplos incluem a distribuição de conteúdo de escala da Internet, em que uma fonte confiável distribui o conteúdo (como atualizações de software ou de mídia), um grupo de amigos do exchange músicas e fotos ou uma equipe de colegas colaborativamente editar um documento. Cada um desses cenários exige que um modelo de segurança exclusivo. O modelo de segurança de canal par foi projetado para lidar com esses cenários e fornece um modelo de segurança de som para as respectivas necessidades de diferentes modelos de identidade, autenticação e autorização.  
  
## <a name="security-scenarios"></a>Cenários de segurança  
 Um cenário de distribuição de conteúdo exige que cada destinatário conteúdo identificar a fonte de conteúdo. Devido à natureza distribuída do cenário, ele nem sempre é possível saber e os intermediários de confiança que as mensagens de processo ou interceptação. Para efetivamente atenuar a ameaça que um intermediário não confiável pode violar as mensagens, aplicativos podem proteger a mensagem no remetente, para que qualquer tentativa de violação é detectada com facilidade. Nesse caso, dependendo da confidencialidade do conteúdo, a criptografia pode ser necessária.  
  
 Cenários de colaboração, como colaboração de documentos de grupo geralmente requerem que cada membro que participam da sessão ser identificado individualmente e autenticado. Isso significa que um mecanismo para definir grupos de usuários e autenticar em relação a esses grupos é necessário ter uma sessão segura. Além disso, os aplicativos podem exigir o rastreamento de cada mensagem pela autenticação no nível da mensagem. Esses tipos de aplicativos, o desempenho pode ser sacrificado para um esquema de segurança mais forte.  
  
 Modelos de segurança informal, como dados de Conhecimento de um segredo comuns entre o grupo pode exigir que uma sessão de comunicação entre um grupo de usuários casuais. Para esses tipos de aplicativos, ter um modelo de segurança que é conveniente para estabelecer e configurar é mais importante do que ter a forma mais segura de autenticação ou fornecer medidas de não-repúdio. Para esses cenários, um mecanismo de autenticação baseada em senha ajuda a proteger a camada de comunicação e ainda permite a autenticação de mensagens. Segurança baseada em senha é a configuração padrão de canal par.  
  
## <a name="token-types"></a>Tipos de token  
 Canal par reconhece um único tipo de token para a identificação de alta segurança, certificados X.509, que fornecem um modelo de identidade forte com base no tipo de autenticação e autorização que pode ser implementada. Confidencialidade e integridade facilmente são fornecidos usando certificados. No entanto, os certificados x. 509 podem ser difícil de usar e implantar.  
  
 Peer Channel também fornece suporte para aplicativos simples com o uso de senhas. Aplicativos podem optar por configurar grupos de ponto a ponto rápido e simples com base em uma senha fornecida. Nesse caso, um proprietário do grupo decide e comunica-se a senha para os membros. Cada membro deve entrar usando essa senha antes que eles poderão ingressar na sessão. Senhas podem ser usadas apenas para permitir a entrada para a sessão; eles não podem ser usados para realizar a autenticação de mensagem. Isso ocorre porque um token simétrico que compartilham um grupo de pares é difícil e inadequado usar para autenticação de código-fonte.  
  
## <a name="security-model"></a>Modelo de segurança  
 Canal par fornece a capacidade de proteger os links individuais entre pares. Isso significa que a mensagem nunca flui em um link não seguro (da perspectiva do aplicativo). Internamente, cada link (um canal de transporte entre dois pontos) é protegido usando a segurança de camada de transporte (TLS). Isso significa que, quando um remetente compõe e envia uma mensagem, ele é enviado por transporte seguro para cada um dos seus pares de imediatos, o que a mensagem de acesso e, por sua vez enviará a mensagem para seus colegas imediatas através de conexões seguras. Essa segurança funciona apenas no transporte de nível e é independente dos modelos de segurança de mensagem.  
  
 Peer Channel também fornece uma maneira de proteger mensagens independentemente a segurança de transporte usado. Nesse modelo, a mensagem é protegida na fonte, usando o token de segurança do código-fonte, embora no momento, somente os certificados x. 509 têm suporte. A mensagem protegida, em seguida, é transmitida pela rede ponto a ponto. Cada ponto de recebimento pode verificar a autenticidade da origem. Observe que a mensagem é protegida, de modo que intermediários não consegue violar.  
  
 Para alcançar a confidencialidade, aplicativos podem empregar a segurança de transporte com esquemas de associação de grupo forte para evitar acesso não autorizado à mensagem.  
  
 Canal par não requer um modelo de identidade específico, desde que o aplicativo escolhe um dos tipos de token com suporte. Aplicativos completamente possui o ciclo de vida dessas identidades e as decisões de autenticação.  
  
## <a name="see-also"></a>Consulte também

- [Protegendo aplicativos de canal par](../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [Conceitos de canal par](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
- [Compilando um aplicativo de canal par](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
