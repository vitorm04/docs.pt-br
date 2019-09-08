---
title: Segurança estendida
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
ms.openlocfilehash: 45216493a3afa23f24a085964a2c43e19b197d4b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797124"
---
# <a name="extending-security"></a>Segurança estendida
Para acomodar novos tipos de declaração e tokens personalizados, você pode estender a infraestrutura de segurança do Windows Communication Foundation (WCF). Os tópicos nesta seção mostram como isso é feito.  
  
## <a name="in-this-section"></a>Nesta seção  
  
 [Credencial personalizada e validação de credenciais](custom-credential-and-credential-validation.md)  
 Explica como o modelo de identidade é usado ao validar credenciais personalizadas.  
  
 [Tokens personalizados](custom-tokens.md)  
 Os tokens emitidos de um serviço de token de segurança (STS) normalmente são tokens SAML. Este tópico explica como criar um tipo de token personalizado.  
  
 [Autorização personalizada](custom-authorization.md)  
 Explica como implementar a autorização personalizada.  
  
 [Substituindo a identidade de um serviço de autenticação](overriding-the-identity-of-a-service-for-authentication.md)  
 Descreve como substituir a identidade de um serviço para autenticação.  
  
 [Como: Criar um verificador de identidade de cliente personalizado](how-to-create-a-custom-client-identity-verifier.md)  
 Demonstra como validar uma identidade de ponto de extremidade personalizada.  
  
 [Como: Usar certificados X. 509 separados para assinatura e criptografia](how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 Normalmente, as mensagens são assinadas e criptografadas com um único certificado. Este tópico explica como dois certificados podem ser usados, quando necessário.  
  
 [Como: Alterar o provedor criptográfico para uma chave privada do certificado X. 509](change-cryptographic-provider-x509-certificate-private-key.md)  
 Explica como alterar o provedor criptográfico usado para fornecer uma chave privada do certificado X. 509 e como integrar o provedor à estrutura do Windows Communication Foundation (WCF).  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Segurança](../feature-details/security.md)  
  
 [Programação básica do WCF](../basic-wcf-programming.md)  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de segurança](../feature-details/security-overview.md)
