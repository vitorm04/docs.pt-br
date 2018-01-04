---
title: "Recursos de segurança com associações personalizadas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 2f26e68b9654ccd565328003596e324558f7505f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="security-capabilities-with-custom-bindings"></a>Recursos de segurança com associações personalizadas
Você pode executar tarefas mais comuns de segurança usando uma das associações fornecidas pelo sistema. Se você precisar de mais controle, no entanto, você pode criar uma associação personalizada com um <xref:System.ServiceModel.Channels.SecurityBindingElement>, conforme explicado nestes tópicos. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]associações personalizadas, consulte [associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Modos de autenticação de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 Descreve os modos de autenticação que são possíveis com uma associação personalizada.  
  
 [Como criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 Descreve as etapas básicas para criar uma associação personalizada com um elemento de segurança.  
  
 [Como criar um SecurityBindingElement para um modo de autenticação especificado](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 Descreve como criar um elemento de segurança para um modo de autenticação especificado.  
  
 [Como: desabilitar sessões seguras em um WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 Descreve como desabilitar sessões seguras durante a criação de um serviço de Federação.  
  
 [Como habilitar a detecção de reprodução de mensagem](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 Descreve como determinar quando ocorre um ataque de repetição.  
  
 [Como criar uma credencial de suporte](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 Descreve como fornecer uma credencial de suporte a um serviço, se o serviço exigir.  
  
 [Como configurar uma confirmação de assinatura](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 Descreve as etapas para confirmar assinaturas ao assinar digitalmente as mensagens.  
  
 [Como definir uma distorção máxima do relógio](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 Descreve como definir a diferença de tempo máximo permitido entre um serviço e um cliente.  
  
 [Como desabilitar a criptografia de assinaturas digitais](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 Descreve como desabilitar a criptografia de assinaturas digitais que pode ter um benefício de desempenho.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Noções básicas de nível de proteção](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a>Consulte também  
 [Associações e segurança](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Associações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md)
