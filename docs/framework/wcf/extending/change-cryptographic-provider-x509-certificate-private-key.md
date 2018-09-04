---
title: 'Como: alterar o provedor criptográfico para um certificado X.509&#39;s de chave privada'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptographic provider [WCF], changing
- cryptographic provider [WCF]
ms.assetid: b4254406-272e-4774-bd61-27e39bbb6c12
ms.openlocfilehash: bb345b3106895a75c00a0d80b8665a0e9239598f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510473"
---
# <a name="how-to-change-the-cryptographic-provider-for-an-x509-certificate39s-private-key"></a>Como: alterar o provedor criptográfico para um certificado X.509&#39;s de chave privada
Este tópico mostra como alterar o provedor criptográfico usado para fornecer a chave privada de um certificado X.509 e como integrar o provedor a estrutura de segurança do Windows Communication Foundation (WCF). Para obter mais informações sobre como usar certificados, consulte [trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 A estrutura de segurança do WCF fornece uma maneira de introduzir novos tipos de token de segurança, conforme descrito em [como: criar um Token personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md). Também é possível usar um token personalizado para substituir tipos de token fornecido pelo sistema existentes.  
  
 Neste tópico, o token de segurança X.509 fornecido pelo sistema é substituído por um token X.509 personalizado que fornece uma implementação diferente da chave privada do certificado. Isso é útil em cenários onde a chave privada real é fornecida por um provedor criptográfico diferente que o provedor de criptografia do Windows padrão. Um exemplo de um provedor criptográfico alternativo é um módulo de segurança de hardware que executa todas as privada chave relacionadas operações criptográficas e não armazena as chaves privadas na memória, o que melhora a segurança do sistema.  
  
 O exemplo a seguir é para fins de demonstração. Ele não substitui o provedor criptográfico do Windows padrão, mas mostra onde esse provedor pode ser integrado.  
  
## <a name="procedures"></a>Procedimentos  
 Cada token de segurança que tem uma chave de segurança associada ou chaves deve implementar o <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> propriedade, que retorna uma coleção de chaves da instância de token de segurança. Se o token é um token de segurança X.509, a coleção contém uma única instância da <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> classe que representa as chaves públicas e privadas associadas ao certificado. Para substituir o provedor de criptografia padrão usado para fornecer chaves do certificado, crie uma nova implementação dessa classe.  
  
#### <a name="to-create-a-custom-x509-asymmetric-key"></a>Para criar uma chave assimétrica de x. 509 personalizada  
  
1.  Definir uma nova classe que deriva de <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> classe.  
  
2.  Substituir o <xref:System.IdentityModel.Tokens.SecurityKey.KeySize%2A> propriedade somente leitura. Essa propriedade retorna o tamanho real da chave pública/privada do certificado par de chaves.  
  
3.  Substituir o método <xref:System.IdentityModel.Tokens.SecurityKey.DecryptKey%2A>. Esse método é chamado pela estrutura de segurança do WCF para descriptografar uma chave simétrica com a chave privada do certificado. (A chave foi anteriormente criptografada com a chave pública do certificado.)  
  
4.  Substituir o método <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetAsymmetricAlgorithm%2A>. Esse método é chamado pela estrutura de segurança do WCF para obter uma instância da <xref:System.Security.Cryptography.AsymmetricAlgorithm> classe que representa o provedor criptográfico para as chaves do certificado público ou privado, dependendo dos parâmetros passados para o método.  
  
5.  Opcional. Substituir o método <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetHashAlgorithmForSignature%2A>. Substitua este método se uma implementação diferente de <xref:System.Security.Cryptography.HashAlgorithm> classe é necessária.  
  
6.  Substituir o método <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetSignatureFormatter%2A>. Esse método retorna uma instância do <xref:System.Security.Cryptography.AsymmetricSignatureFormatter> classe que está associado com a chave privada do certificado.  
  
7.  Substituir o método <xref:System.IdentityModel.Tokens.SecurityKey.IsSupportedAlgorithm%2A>. Esse método é usado para indicar se um determinado algoritmo criptográfico é compatível com a implementação de chave de segurança.  
  
     [!code-csharp[c_CustomX509Token#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#1)]
     [!code-vb[c_CustomX509Token#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#1)]  
  
 O procedimento a seguir mostra como integrar o a x. 509 assimétrica de segurança chave implementação personalizada criada no procedimento anterior com a estrutura de segurança do WCF para substituir a segurança X.509 fornecido pelo sistema token.  
  
#### <a name="to-replace-the-system-provided-x509-security-token-with-a-custom-x509-asymmetric-security-key-token"></a>Para substituir o token de segurança X.509 fornecido pelo sistema com um token de chave de segurança assimétricas de x. 509  
  
1.  Crie um token de segurança X.509 personalizado que retorna a chave assimétrica de segurança de x. 509 personalizada em vez da chave de segurança fornecida pelo sistema, conforme mostrado no exemplo a seguir. Para obter mais informações sobre tokens de segurança personalizada, consulte [como: criar um Token personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomX509Token#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#2)]
     [!code-vb[c_CustomX509Token#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#2)]  
  
2.  Crie um provedor de token de segurança personalizada que retorna um token de segurança X.509 personalizado, conforme mostrado no exemplo. Para obter mais informações sobre provedores de token de segurança personalizada, consulte [como: criar um provedor de Token de segurança personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
     [!code-csharp[c_CustomX509Token#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#3)]
     [!code-vb[c_CustomX509Token#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#3)]  
  
3.  Se a chave de segurança personalizada precisa ser usado no lado do iniciador, crie um cliente personalizado Gerenciador de token de segurança e as classes de credenciais de cliente personalizado, conforme mostrado no exemplo a seguir. Para obter mais informações sobre credenciais personalizadas do cliente e os gerentes de token de segurança de cliente, consulte [instruções passo a passo: Criando personalizadas do cliente e credenciais de serviço](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomX509Token#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#4)]
     [!code-vb[c_CustomX509Token#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#4)]  
  
     [!code-csharp[c_CustomX509Token#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#6)]
     [!code-vb[c_CustomX509Token#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#6)]  
  
4.  Se a chave de segurança personalizada precisa ser usado no lado do destinatário, crie um Gerenciador de token de segurança do serviço personalizado e credenciais de serviço personalizado, conforme mostrado no exemplo a seguir. Para obter mais informações sobre credenciais de serviço personalizado e gerentes de token de segurança do serviço, consulte [instruções passo a passo: Criando personalizadas do cliente e credenciais de serviço](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
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
 [Arquitetura de segurança](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
