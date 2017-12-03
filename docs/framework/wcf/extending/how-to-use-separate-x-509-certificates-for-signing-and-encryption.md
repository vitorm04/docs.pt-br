---
title: Como utilizar certificados X.509 separados para assinatura e criptografia
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, extensibility
- ClientCredentials class
- ClientCredentialsSecurityTokenManager class
ms.assetid: 0b06ce4e-7835-4d82-8baf-d525c71a0e49
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 312a4b854cb527e63d6866247d4147720ce0710c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-separate-x509-certificates-for-signing-and-encryption"></a>Como utilizar certificados X.509 separados para assinatura e criptografia
Este tópico mostra como configurar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] para usar certificados diferentes para assinatura e criptografia no cliente e no serviço.  
  
 Para habilitar certificados separados a ser usado para assinatura e criptografia, um cliente personalizado ou serviço credenciais (ou ambos) devem ser criados porque [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não fornece uma API para definir vários certificados de cliente ou serviço. Além disso, um segurança do Gerenciador de token deve ser fornecido para utilizar as informações de vários certificados e criar um provedor de token de segurança apropriado para especificado direção de mensagem e de uso de chave.  
  
 O diagrama a seguir mostra as classes principais usadas, as classes herdam (mostrada por uma seta apontando para cima) e os tipos de retorno de certos métodos e propriedades.  
  
-   `MyClientCredentials`é uma implementação personalizada de <xref:System.ServiceModel.Description.ClientCredentials>.  
  
    -   Suas propriedades mostradas no diagrama de retorno de todas as instâncias do <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>.  
  
    -   O método <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> retorna uma instância de `MyClientCredentialsSecurityTokenManager`.  
  
-   `MyClientCredentialsSecurityTokenManager`é uma implementação personalizada de <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.  
  
    -   O método <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> retorna uma instância de <xref:System.IdentityModel.Selectors.X509SecurityTokenProvider>.  
  
 ![Gráfico mostrando como as credenciais do cliente são usadas](../../../../docs/framework/wcf/extending/media/e4971edd-a59f-4571-b36f-7e6b2f0d610f.gif "e4971edd-a59f-4571-b36f-7e6b2f0d610f")  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]credenciais personalizadas, consulte [passo a passo: criação de cliente personalizadas e as credenciais de serviço](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Além disso, você deve criar um verificador de identidade personalizada e vinculá-lo a um elemento de associação de segurança em uma associação personalizada. Você também deve usar as credenciais personalizadas em vez de credenciais padrão.  
  
 O diagrama a seguir mostra as classes envolvidas na associação personalizada, e como o verificador de identidade personalizado é vinculado. Há vários elementos de associação envolvidos, que herda de <xref:System.ServiceModel.Channels.BindingElement>. O <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> tem o <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> propriedade, que retorna uma instância de <xref:System.ServiceModel.Security.IdentityVerifier>, do qual `MyIdentityVerifier` personalizada.  
  
 ![Gráfico mostrando um elemento de associação personalizada](../../../../docs/framework/wcf/extending/media/dddea4a2-0bb4-4921-9bf4-20d4d82c3da5.gif "dddea4a2-0bb4-4921-9bf4-20d4d82c3da5")  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Criando um verificador de identidade personalizada, consulte como: [como: criar um verificador de identidade do cliente personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md).  
  
### <a name="to-use-separate-certificates-for-signing-and-encryption"></a>Para usar certificados separados para assinatura e criptografia  
  
1.  Definir uma nova classe de credenciais de cliente que herde o <xref:System.ServiceModel.Description.ClientCredentials> classe. Implementar quatro novas propriedades para permitir a especificação de vários certificados: `ClientSigningCertificate`, `ClientEncryptingCertificate`, `ServiceSigningCertificate`, e `ServiceEncryptingCertificate`. Também substituir o <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> método para retornar uma instância do personalizado <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> classe definida na próxima etapa.  
  
     [!code-csharp[c_FourCerts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#1)]
     [!code-vb[c_FourCerts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#1)]  
  
2.  Definir um novo cliente segurança Gerenciador de token que herda de <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> classe. Substituir o <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> método para criar um provedor de token de segurança apropriado. O `requirement` parâmetro (um <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>) fornece o uso de chave e de direção de mensagem.  
  
     [!code-csharp[c_FourCerts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#2)]
     [!code-vb[c_FourCerts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#2)]  
  
3.  Definir uma nova classe de credenciais de serviço que herda de <xref:System.ServiceModel.Description.ServiceCredentials> classe. Implementar quatro novas propriedades para permitir a especificação de vários certificados: `ClientSigningCertificate`, `ClientEncryptingCertificate`, `ServiceSigningCertificate`, e `ServiceEncryptingCertificate`. Também substituir o <xref:System.ServiceModel.Description.ServiceCredentials.CreateSecurityTokenManager%2A> método para retornar uma instância do personalizado <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> classe definida na próxima etapa.  
  
     [!code-csharp[c_FourCerts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#3)]
     [!code-vb[c_FourCerts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#3)]  
  
4.  Definir um novo serviço segurança Gerenciador de token que herda de <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> classe. Substituir o <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> método para criar um provedor de token de segurança apropriadas dado o uso de chave e de direção de mensagem passada.  
  
     [!code-csharp[c_FourCerts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#4)]
     [!code-vb[c_FourCerts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#4)]  
  
### <a name="to-use-multiple-certificates-on-the-client"></a>Para usar vários certificados no cliente  
  
1.  Crie uma associação personalizada. O elemento de associação de segurança deve funcionar no modo duplex para permitir a segurança de diferente provedores de token estar presente para solicitações e respostas. Uma forma de fazer isso é usar um transporte duplex capaz ou usar o <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> conforme mostrado no código a seguir. Vincular a personalizada <xref:System.ServiceModel.Security.IdentityVerifier> que é definida na próxima etapa para o elemento de associação de segurança. Substitua as credenciais do cliente padrão com as credenciais do cliente personalizado criadas anteriormente.  
  
     [!code-csharp[c_FourCerts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#5)]
     [!code-vb[c_FourCerts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#5)]  
  
2.  Definir um personalizado <xref:System.ServiceModel.Security.IdentityVerifier>. O serviço tem várias identidades, como certificados diferentes são usados para criptografar a solicitação e para assinar a resposta.  
  
    > [!NOTE]
    >  No exemplo a seguir, o verificador de identidade personalizado fornecido não executa nenhuma identidade de ponto de extremidade verificando para fins de demonstração. Isso não é recomendável prática para código de produção.  
  
     [!code-csharp[c_FourCerts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#6)]
     [!code-vb[c_FourCerts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#6)]  
  
### <a name="to-use-multiple-certificates-on-the-service"></a>Para usar vários certificados no serviço  
  
1.  Crie uma associação personalizada. O elemento de associação de segurança deve operar em modo duplex para permitir a segurança de diferente provedores de token estar presente para solicitações e respostas. Como com o cliente, use um transporte duplex capaz ou <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> conforme mostrado no código a seguir. Substitua as credenciais de serviço padrão com as credenciais de serviço personalizado criadas anteriormente.  
  
     [!code-csharp[c_FourCerts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#7)]
     [!code-vb[c_FourCerts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#7)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>  
 <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager>  
 <xref:System.ServiceModel.Security.IdentityVerifier>  
 [Passo a passo: Criando credenciais de serviço e cliente personalizados](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
