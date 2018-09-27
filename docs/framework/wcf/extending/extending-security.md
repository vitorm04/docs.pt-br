---
title: Segurança estendida
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
author: BrucePerlerMS
ms.openlocfilehash: 3ae41e10a51ba0e4c27bcfbb1eb812e0015e5178
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47397145"
---
# <a name="extending-security"></a>Segurança estendida
Para acomodar novos tipos de declaração e tokens personalizados, você pode estender a infraestrutura de segurança do Windows Communication Foundation (WCF). Os tópicos nesta seção mostram como isso é feito.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Arquitetura de segurança](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)  
 Explica a arquitetura do sistema de segurança do WCF.  
  
 [Credencial personalizada e validação de credenciais](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 Explica como o modelo de identidade é usado ao validar credenciais personalizadas.  
  
 [Tokens personalizados](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 Normalmente, de um Security Token Service (STS) de tokens emitidos são tokens SAML. Este tópico explica como criar um tipo de token personalizado.  
  
 [Autorização personalizada](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 Explica como implementar a autorização personalizada.  
  
 [Substituindo a identidade de um serviço de autenticação](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 Descreve como substituir a identidade de um serviço de autenticação.  
  
 [Como criar um verificador de identidade de cliente personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 Demonstra como validar uma identidade de ponto de extremidade personalizado.  
  
 [Como usar certificados X.509 separados para assinatura e criptografia](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 As mensagens são normalmente assinadas e criptografadas com um único certificado. Este tópico explica como dois certificados pode ser usado quando for necessário.  
  
 [Como alterar o provedor criptográfico para a chave privada de um certificado X.509](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 Explica como alterar o provedor criptográfico usado para fornecer a chave privada de um certificado X.509 e como integrar o provedor a estrutura do Windows Communication Foundation (WCF).  
  
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
