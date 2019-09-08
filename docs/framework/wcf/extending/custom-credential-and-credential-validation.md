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
ms.openlocfilehash: 1418d4155bc7f2fefc9f3e6caf4d3a264747a667
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795807"
---
# <a name="custom-credential-and-credential-validation"></a>Credencial personalizada e validação de credencial
A segurança no Windows Communication Foundation (WCF) é baseada na troca de credenciais entre serviços e clientes. A maioria dos cenários de segurança pode ser satisfeita usando tipos de credenciais comuns, como Windows (Kerberos), nome de usuário e senhas e certificados. No entanto, se um novo tipo de credencial for necessário, os tópicos nesta seção explicam como tratar e validar novos tipos.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Criar um serviço que empregue um validador de certificado personalizado](how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 Explica como personalizar a <xref:System.IdentityModel.Selectors.X509CertificateValidator> validação do WCF herdando da classe.  
  
 [Passo a passo: Criando credenciais de cliente e de serviço personalizadas](walkthrough-creating-custom-client-and-service-credentials.md)  
 Demonstra como estender as <xref:System.ServiceModel.Description.ClientCredentials> classes e <xref:System.ServiceModel.Description.ServiceCredentials> para acomodar novos tipos de credencial. Isso é primeiro em uma série de tópicos que permitem a criação de tipos de credenciais personalizados.  
  
 [Como: Criar um provedor de token de segurança personalizado](how-to-create-a-custom-security-token-provider.md)  
 Explica como criar um provedor de token de segurança para lidar com novos tipos de credenciais e retornar novos tokens para a credencial. Este é o segundo tópico da série.  
  
 [Como: Criar um autenticador de token de segurança personalizado](how-to-create-a-custom-security-token-authenticator.md)  
 Explica como criar um autenticador personalizado para autenticar um novo tipo de credencial. Este é o terceiro tópico da série.  
  
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
 [Autenticação](../feature-details/authentication-in-wcf.md)  
  
 [Federação e tokens emitidos](../feature-details/federation-and-issued-tokens.md)  
  
 [Autorização](../feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>Consulte também

- [Segurança](../feature-details/security.md)
