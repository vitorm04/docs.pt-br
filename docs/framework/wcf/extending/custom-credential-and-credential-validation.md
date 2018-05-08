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
ms.openlocfilehash: 00a49f9746c7073e3abdb353b38a76f6eea099f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="custom-credential-and-credential-validation"></a>Credencial personalizada e validação de credencial
Segurança no Windows Communication Foundation (WCF) baseia-se a troca de credenciais entre clientes e serviços. A maioria dos cenários de segurança podem ser satisfeitos usando tipos comuns de credenciais, como Windows (Kerberos), nome de usuário e senhas e certificados. No entanto, se um novo tipo de credencial for necessário, os tópicos nesta seção explicam como manipular e validar os novos tipos.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como criar um serviço que utiliza um validador de certificado personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 Explica como personalizar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] validação herdando do <xref:System.IdentityModel.Selectors.X509CertificateValidator> classe.  
  
 [Passo a passo: criando credenciais de serviço e de cliente personalizados](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 Demonstra como estender o <xref:System.ServiceModel.Description.ClientCredentials> e <xref:System.ServiceModel.Description.ServiceCredentials> classes para acomodar novos tipos de credenciais. Este é o primeiro em uma série de tópicos que permitem a criação de tipos de credencial personalizada.  
  
 [Como criar um provedor de token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 Explica como criar um provedor de token de segurança para lidar com novos tipos de credenciais e retornar novos tokens para a credencial. Este é o segundo tópico na série.  
  
 [Como criar um autenticador de token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
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
 [Segurança](../../../../docs/framework/wcf/feature-details/security.md)
