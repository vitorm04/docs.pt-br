---
title: 'Como: Usar certificados X.509 separados para assinatura e criptografia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, extensibility
- ClientCredentials class
- ClientCredentialsSecurityTokenManager class
ms.assetid: 0b06ce4e-7835-4d82-8baf-d525c71a0e49
ms.openlocfilehash: 6910b7abeb6a97cce1da9655fdab99b5295cc346
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500480"
---
# <a name="how-to-use-separate-x509-certificates-for-signing-and-encryption"></a>Como: Usar certificados X.509 separados para assinatura e criptografia
Este tópico mostra como configurar o Windows Communication Foundation (WCF) para usar certificados diferentes para assinatura e criptografia no cliente e serviço.  
  
 Para habilitar certificados separados a serem usados para assinatura e criptografia, personalizadas do cliente ou serviço credenciais (ou ambos) devem ser criados porque o WCF fornece uma API para definir vários certificados de cliente ou serviço. Além disso, uma segurança Gerenciador de token deve ser fornecido para aproveitar as informações de vários certificados e criar um provedor de token de segurança apropriadas para especificado chave direção de uso e a mensagem.  
  
 O diagrama a seguir mostra as principais classes usadas, as classes herdam de (mostrado por uma seta apontando para cima) e os tipos de retorno de certos métodos e propriedades.  
  
-   `MyClientCredentials` é uma implementação personalizada de <xref:System.ServiceModel.Description.ClientCredentials>.  
  
    -   Suas propriedades mostradas no diagrama de retorno de todas as instâncias de <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>.  
  
    -   Seu método <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> retorna uma instância de `MyClientCredentialsSecurityTokenManager`.  
  
-   `MyClientCredentialsSecurityTokenManager` é uma implementação personalizada de <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.  
  
    -   Seu método <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> retorna uma instância de <xref:System.IdentityModel.Selectors.X509SecurityTokenProvider>.  
  
 ![Gráfico mostrando como as credenciais do cliente são usadas](../../../../docs/framework/wcf/extending/media/e4971edd-a59f-4571-b36f-7e6b2f0d610f.gif "e4971edd-a59f-4571-b36f-7e6b2f0d610f")  
  
 Para obter mais informações sobre credenciais personalizadas, consulte [passo a passo: Criação de credenciais de serviço e personalizadas do cliente](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Além disso, você deve criar um verificador de identidade personalizado e vinculá-lo a um elemento de associação de segurança em uma associação personalizada. Você também deve usar as credenciais personalizadas em vez das credenciais padrão.  
  
 O diagrama a seguir mostra as classes envolvidas na associação personalizada, e como o verificador de identidade personalizado está vinculado. Há vários elementos de associação envolvidos, que herdam de <xref:System.ServiceModel.Channels.BindingElement>. O <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> tem o <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> propriedade, que retorna uma instância do <xref:System.ServiceModel.Security.IdentityVerifier>, do qual `MyIdentityVerifier` é personalizada.  
  
 ![Gráfico mostrando um elemento de associação personalizado](../../../../docs/framework/wcf/extending/media/dddea4a2-0bb4-4921-9bf4-20d4d82c3da5.gif "dddea4a2-0bb4-4921-9bf4-20d4d82c3da5")  
  
 Para obter mais informações sobre como criar um verificador de identidade personalizada, consulte como: [Como: Criar um verificador de identidade do cliente personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md).  
  
### <a name="to-use-separate-certificates-for-signing-and-encryption"></a>Para usar certificados separados para assinatura e criptografia  
  
1.  Definir uma nova classe de credenciais de cliente que herda o <xref:System.ServiceModel.Description.ClientCredentials> classe. Implementar quatro novas propriedades para permitir a especificação de vários certificados: `ClientSigningCertificate`, `ClientEncryptingCertificate`, `ServiceSigningCertificate`, e `ServiceEncryptingCertificate`. Também substituir as <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> método para retornar uma instância de personalizada <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> classe que é definido na próxima etapa.  
  
     [!code-csharp[c_FourCerts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#1)]
     [!code-vb[c_FourCerts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#1)]  
  
2.  Definir um novo cliente segurança Gerenciador de token que herda o <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> classe. Substituir o <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> método para criar um provedor de token de segurança apropriado. O `requirement` parâmetro (uma <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>) fornece o uso de direção e a chave da mensagem.  
  
     [!code-csharp[c_FourCerts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#2)]
     [!code-vb[c_FourCerts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#2)]  
  
3.  Definir uma nova classe de credenciais de serviço que herda o <xref:System.ServiceModel.Description.ServiceCredentials> classe. Implementar quatro novas propriedades para permitir a especificação de vários certificados: `ClientSigningCertificate`, `ClientEncryptingCertificate`, `ServiceSigningCertificate`, e `ServiceEncryptingCertificate`. Também substituir as <xref:System.ServiceModel.Description.ServiceCredentials.CreateSecurityTokenManager%2A> método para retornar uma instância de personalizada <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> classe que é definido na próxima etapa.  
  
     [!code-csharp[c_FourCerts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#3)]
     [!code-vb[c_FourCerts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#3)]  
  
4.  Definir um novo serviço segurança Gerenciador de token que herda o <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> classe. Substituir o <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> método para criar um provedor de token de segurança apropriadas dado o uso de direção e a chave da mensagem passada.  
  
     [!code-csharp[c_FourCerts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#4)]
     [!code-vb[c_FourCerts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#4)]  
  
### <a name="to-use-multiple-certificates-on-the-client"></a>Para usar vários certificados no cliente  
  
1.  Crie uma ligação personalizada. O elemento de associação de segurança deve operar em modo duplex para permitir a segurança de diferente provedores de token esteja presente para solicitações e respostas. Uma forma de fazer isso é usar um transporte compatível com duplex ou usar o <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> conforme mostrado no código a seguir. Vincular personalizada <xref:System.ServiceModel.Security.IdentityVerifier> que é definido na próxima etapa para o elemento de associação de segurança. Substitua as credenciais do cliente padrão com as credenciais de cliente personalizada criadas anteriormente.  
  
     [!code-csharp[c_FourCerts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#5)]
     [!code-vb[c_FourCerts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#5)]  
  
2.  Definir um personalizado <xref:System.ServiceModel.Security.IdentityVerifier>. O serviço tem várias identidades, como certificados diferentes são usados para criptografar a solicitação e para assinar a resposta.  
  
    > [!NOTE]
    >  No exemplo a seguir, o verificador de identidade personalizado fornecido não realiza qualquer identidade de ponto de extremidade, verificando para fins de demonstração. Isso não é recomendável prática para o código de produção.  
  
     [!code-csharp[c_FourCerts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#6)]
     [!code-vb[c_FourCerts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#6)]  
  
### <a name="to-use-multiple-certificates-on-the-service"></a>Para usar vários certificados no serviço  
  
1.  Crie uma ligação personalizada. O elemento de associação de segurança deve operar em um modo duplex para permitir a segurança de diferente provedores de token esteja presente para solicitações e respostas. Como com o cliente, use um transporte compatível com duplex ou use <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> conforme mostrado no código a seguir. Substitua as credenciais de serviço padrão com as credenciais de serviço personalizado criadas anteriormente.  
  
     [!code-csharp[c_FourCerts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#7)]
     [!code-vb[c_FourCerts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#7)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>
- <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [Passo a passo: Criação de credenciais de serviço e personalizadas do cliente](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
