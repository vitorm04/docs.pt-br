---
title: "Segurança estendida"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
caps.latest.revision: 
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: cdd9b91ba7ff9b1e431f7d9107e72df084ba8af3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="extending-security"></a>Segurança estendida
Para acomodar novos tipos de declaração e tokens personalizados, você pode estender a infraestrutura de segurança de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Os tópicos nesta seção mostram como fazer isso.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Arquitetura de segurança](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)  
 Explica a arquitetura do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sistema de segurança.  
  
 [Credencial personalizada e validação de credenciais](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 Explica como o modelo de identidade é usado ao validar credenciais personalizadas.  
  
 [Tokens personalizados](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 Tokens emitidos de um Token de segurança Service (STS) normalmente são tokens SAML. Este tópico explica como criar um tipo de token personalizado.  
  
 [Autorização personalizada](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 Explica como implementar a autorização personalizada.  
  
 [Substituindo a identidade de um serviço de autenticação](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 Descreve como substituir a identidade de um serviço para autenticação.  
  
 [Como criar um verificador de identidade de cliente personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 Demonstra como validar uma identidade de ponto de extremidade personalizado.  
  
 [Como usar certificados X.509 separados para assinatura e criptografia](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 As mensagens são normalmente assinadas e criptografadas com um único certificado. Este tópico explica como dois certificados podem ser usados, quando necessário.  
  
 [Como alterar o provedor criptográfico para a chave privada de um certificado X.509](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 Explica como alterar o provedor de criptografia usado para fornecer a chave privada de um certificado x. 509 e como integrar o provedor para o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] framework.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Segurança](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [Programação básica do WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)
