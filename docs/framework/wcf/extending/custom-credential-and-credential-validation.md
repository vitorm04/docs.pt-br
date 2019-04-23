---
title: Credencial personalizada e validação de credencial
ms.date: 03/30/2017
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
ms.openlocfilehash: 3b1ff700010f471a4d9be117f363083b6cbed493
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210627"
---
# <a name="custom-credential-and-credential-validation"></a>Credencial personalizada e validação de credencial
No Windows Communication Foundation (WCF) é baseada na troca de credenciais entre serviços e clientes. A maioria dos cenários de segurança podem ser atendidos usando tipos de credencial comuns, como Windows (Kerberos), nome de usuário e senhas e certificados. No entanto, se um novo tipo de credencial for necessário, os tópicos nesta seção explicam como manipular e validar os novos tipos.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Criar um serviço que utiliza um validador de certificado personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 Explica como personalizar a validação do WCF, herdando o <xref:System.IdentityModel.Selectors.X509CertificateValidator> classe.  
  
 [Passo a passo: Criação de credenciais de serviço e personalizadas do cliente](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 Demonstra como estender o <xref:System.ServiceModel.Description.ClientCredentials> e <xref:System.ServiceModel.Description.ServiceCredentials> classes para acomodar novos tipos de credenciais. Isso é o primeiro de uma série de tópicos que permitem a criação de tipos de credenciais personalizado.  
  
 [Como: Criar um provedor de Token de segurança personalizadas](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 Explica como criar um provedor de token de segurança para lidar com novos tipos de credenciais e retornar novos tokens de credencial. Este é o segundo tópico na série.  
  
 [Como: Criar um autenticador de Token de segurança personalizadas](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 Explica como criar um autenticador personalizado para autenticar um novo tipo de credencial. Este é o terceiro tópico na série.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Autenticação](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [Federação e tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [Autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>Consulte também

- [Segurança](../../../../docs/framework/wcf/feature-details/security.md)
