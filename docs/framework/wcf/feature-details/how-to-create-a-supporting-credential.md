---
title: 'Como: criar uma credencial de suporte'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 7c6c4ea777f62541f8ca8fa79fdd024e5f5cf2ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326041"
---
# <a name="how-to-create-a-supporting-credential"></a>Como: criar uma credencial de suporte
É possível ter um esquema de segurança personalizado que requer mais de uma credencial. Por exemplo, pode exigir que um serviço do cliente não apenas um nome de usuário e senha, mas também uma credencial que comprova o cliente é com mais de 18 anos. A segunda credencial é um *que dão suporte a credencial*. Este tópico explica como implementar essas credenciais em um cliente do Windows Communication Foundation (WCF).  
  
> [!NOTE]
>  A especificação para dar suporte a credenciais é parte da especificação WS-SecurityPolicy. Para obter mais informações, consulte [especificações de segurança de serviços Web](https://go.microsoft.com/fwlink/?LinkId=88537).  
  
## <a name="supporting-tokens"></a>Tokens com suporte  
 Em resumo, quando você usa a segurança de mensagem, uma *credencial primário* sempre é usado para proteger a mensagem (por exemplo, um certificado X.509 ou um tíquete Kerberos).  
  
 Conforme definido pela especificação, uma associação de segurança usa *tokens* para proteger a troca de mensagens. Um *token* é uma representação de uma credencial de segurança.  
  
 A associação de segurança usa um token de primário identificado na política de associação de segurança para criar uma assinatura. Essa assinatura é conhecida como o *assinatura da mensagem*.  
  
 Tokens adicionais podem ser especificados para aumentar as declarações fornecidas pelo token associado com a assinatura da mensagem.  
  
## <a name="endorsing-signing-and-encrypting"></a>Endossando, assinatura e criptografia  
 Uma credencial de suporte resulta em uma *token de suporte* transmitidos dentro da mensagem. A especificação de WS-SecurityPolicy define quatro maneiras para anexar um token de suporte para a mensagem, conforme descrito na tabela a seguir.  
  
|Finalidade|Descrição|  
|-------------|-----------------|  
|Assinado|O token de suporte está incluído no cabeçalho de segurança e é assinado pela assinatura da mensagem.|  
|Endossando|Uma *token de endosso* assina a assinatura da mensagem.|  
|Assinado e de endosso|Assinado, endossando tokens de sinal de todo o `ds:Signature` elemento produzido a partir de assinatura da mensagem e são em si assinadas por essa assinatura de mensagem; ou seja, ambos os tokens (o token usado para a assinatura da mensagem e o token de endosso assinado) entrar uns aos outros.|  
|Criptografia e não assinados|Tokens de suporte assinados e criptografados são assinados que dão suporte a tokens que também são criptografados quando são exibidas no `wsse:SecurityHeader`.|  
  
## <a name="programming-supporting-credentials"></a>Programação que dão suporte a credenciais  
 Para criar um serviço que usa tokens de suporte, você deve criar uma [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md). (Para obter mais informações, consulte [como: Criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)  
  
 A primeira etapa ao criar uma ligação personalizada é criar um elemento de associação de segurança, que pode ser um dos três tipos:  
  
-   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Todas as classes herdam o <xref:System.ServiceModel.Channels.SecurityBindingElement>, que inclui quatro propriedades relevantes:  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a>Escopos  
 Existem dois escopos para dar suporte a credenciais:  
  
-   *Ponto de extremidade que dão suporte a tokens* dão suporte a todas as operações de um ponto de extremidade. Ou seja, a credencial que representa o token de suporte pode ser usada sempre que qualquer operação de ponto de extremidade é invocadas.  
  
-   *Operação de dar suporte a tokens* dar suporte a apenas uma operação de ponto de extremidade específico.  
  
 Conforme indicado pelos nomes de propriedade, que dão suporte a credenciais pode ser obrigatório ou opcional. Ou seja, se a credencial de suporte é usada se estiver presente, embora ele não é necessário, mas a autenticação não falhará se não estiver presente.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a>Para criar uma associação personalizada que inclui suporte a credenciais  
  
1. Crie um elemento de associação de segurança. O exemplo a seguir cria uma <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> com o `UserNameForCertificate` modo de autenticação. Use o método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A>.  
  
2. Adicione o parâmetro de suporte para a coleção de tipos retornados pela propriedade apropriada (`Endorsing`, `Signed`, `SignedEncrypted`, ou `SignedEndorsed`). Os tipos na <xref:System.ServiceModel.Security.Tokens> namespace incluem tipos comumente usados, como o <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir cria uma instância das <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> e adiciona uma instância da <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> a propriedade Endorsing retornada da classe à coleção.  
  
### <a name="code"></a>Código  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a>Consulte também

- [Como: Criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
