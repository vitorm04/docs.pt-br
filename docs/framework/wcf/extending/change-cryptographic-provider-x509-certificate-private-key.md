---
title: 'Como: alterar o provedor criptográfico para um certificado x. 509&#39;chave privada s'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptographic provider [WCF], changing
- cryptographic provider [WCF]
ms.assetid: b4254406-272e-4774-bd61-27e39bbb6c12
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e7dea9834b654be0b86155e18524053efa4b778b
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-change-the-cryptographic-provider-for-an-x509-certificate39s-private-key"></a>Como: alterar o provedor criptográfico para um certificado x. 509&#39;chave privada s
Este tópico mostra como alterar o provedor de criptografia usado para fornecer a chave privada de um certificado x. 509 e como integrar o provedor para o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] estrutura de segurança. Para obter mais informações sobre como usar certificados, consulte [trabalhar com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] estrutura de segurança fornece uma maneira de introduzir novos tipos de token de segurança, conforme descrito em [como: criar um Token personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md). Também é possível usar um token personalizado para substituir tipos de token fornecido pelo sistema existentes.  
  
 Neste tópico, o token de segurança x. 509 fornecido pelo sistema é substituído por um símbolo x. 509 personalizado que fornece uma implementação diferente para a chave privada do certificado. Isso é útil em cenários onde a chave privada real é fornecida por um provedor criptográfico diferente o provedor criptográfico do Windows padrão. Um exemplo de um provedor criptográfico alternativo é um módulo de segurança de hardware que executa todas as privada chave relacionadas operações criptográficas e não armazena as chaves privadas na memória, o que melhora a segurança do sistema.  
  
 O exemplo a seguir é apenas para demonstração. Não substitui o provedor criptográfico do Windows padrão, mas ela mostra onde esse provedor pode ser integrado.  
  
## <a name="procedures"></a>Procedimentos  
 Cada token de segurança que tem uma chave de segurança associadas ou chaves deve implementar o <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> propriedade, que retorna uma coleção de chaves da instância de token de segurança. Se o token é um token de segurança x. 509, a coleção contém uma única instância de <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> classe que representa as chaves públicas e privadas associadas ao certificado. Para substituir o provedor de criptografia padrão usado para fornecer chaves do certificado, crie uma nova implementação desta classe.  
  
#### <a name="to-create-a-custom-x509-asymmetric-key"></a>Para criar uma chave assimétrica do x. 509 personalizada  
  
1.  Definir uma nova classe que deriva de <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> classe.  
  
2.  Substituir o <xref:System.IdentityModel.Tokens.SecurityKey.KeySize%2A> propriedade somente leitura. Essa propriedade retorna o tamanho real da chave pública/privada do certificado par de chaves.  
  
3.  Substituir o método <xref:System.IdentityModel.Tokens.SecurityKey.DecryptKey%2A>. Este método é chamado pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] estrutura de segurança para descriptografar uma chave simétrica com a chave privada do certificado. (A chave foi previamente criptografada com a chave pública do certificado.)  
  
4.  Substituir o método <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetAsymmetricAlgorithm%2A>. Este método é chamado pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] estrutura de segurança para obter uma instância do <xref:System.Security.Cryptography.AsymmetricAlgorithm> a classe que representa o provedor criptográfico para obter as chave do certificado público ou privado, dependendo dos parâmetros passados para o método.  
  
5.  Opcional. Substituir o método <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetHashAlgorithmForSignature%2A>. Substitua este método se uma implementação diferente do <xref:System.Security.Cryptography.HashAlgorithm> classe é necessária.  
  
6.  Substituir o método <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetSignatureFormatter%2A>. Esse método retorna uma instância do <xref:System.Security.Cryptography.AsymmetricSignatureFormatter> classe associada com a chave privada do certificado.  
  
7.  Substituir o método <xref:System.IdentityModel.Tokens.SecurityKey.IsSupportedAlgorithm%2A>. Esse método é usado para indicar se um determinado algoritmo criptográfico é suportado pela implementação de chave de segurança.  
  
     [!code-csharp[c_CustomX509Token#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#1)]
     [!code-vb[c_CustomX509Token#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#1)]  
  
 O procedimento a seguir mostra como integrar a x. 509 segurança assimétrica chave implementação personalizada criada no procedimento anterior com o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] estrutura de segurança para substituir o token de segurança x. 509 fornecido pelo sistema.  
  
#### <a name="to-replace-the-system-provided-x509-security-token-with-a-custom-x509-asymmetric-security-key-token"></a>Para substituir o token de segurança x. 509 fornecido pelo sistema com um token de chave de segurança assimétrica de x. 509  
  
1.  Crie um token de segurança x. 509 personalizado que retorna a chave de segurança assimétrica x. 509 personalizada em vez da chave de segurança fornecidos pelo sistema, conforme mostrado no exemplo a seguir. Para obter mais informações sobre tokens de segurança personalizada, consulte [como: criar um Token personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomX509Token#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#2)]
     [!code-vb[c_CustomX509Token#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#2)]  
  
2.  Crie um provedor de token de segurança personalizada que retorna um token de segurança x. 509 personalizado, como mostrado no exemplo. Para obter mais informações sobre provedores de token de segurança personalizada, consulte [como: criar um provedor de Token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
     [!code-csharp[c_CustomX509Token#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#3)]
     [!code-vb[c_CustomX509Token#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#3)]  
  
3.  Se a chave de segurança personalizada precisa ser usado no lado do iniciador, crie um cliente personalizado Gerenciador de token de segurança e classes de credenciais de cliente personalizado, como mostrado no exemplo a seguir. Para obter mais informações sobre as credenciais do cliente personalizado e gerenciadores de token de segurança do cliente, consulte [passo a passo: criação de cliente personalizadas e as credenciais de serviço](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomX509Token#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#4)]
     [!code-vb[c_CustomX509Token#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#4)]  
  
     [!code-csharp[c_CustomX509Token#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#6)]
     [!code-vb[c_CustomX509Token#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#6)]  
  
4.  Se a chave de segurança personalizada precisa ser usado no lado do destinatário, crie um Gerenciador de token de segurança de serviço personalizado e credenciais de serviço personalizado, como mostrado no exemplo a seguir. Para obter mais informações sobre as credenciais de serviço personalizado e gerenciadores de token de segurança do serviço, consulte [passo a passo: criação de cliente personalizadas e as credenciais de serviço](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomX509Token#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#5)]
     [!code-vb[c_CustomX509Token#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#5)]  
  
     [!code-csharp[c_CustomX509Token#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#7)]
     [!code-vb[c_CustomX509Token#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#7)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey>  
 <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey>  
 <xref:System.IdentityModel.Tokens.SecurityKey>  
 <xref:System.Security.Cryptography.AsymmetricAlgorithm>  
 <xref:System.Security.Cryptography.HashAlgorithm>  
 <xref:System.Security.Cryptography.AsymmetricSignatureFormatter>  
 [Passo a passo: criando credenciais de serviço e de cliente personalizados](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Como criar um autenticador de token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Como criar um provedor de token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Como criar um token personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)  
 [Arquitetura de segurança](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
