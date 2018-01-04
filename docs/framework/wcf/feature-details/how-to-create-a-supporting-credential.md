---
title: Como criar uma credencial de suporte
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4afad13300e2eb50a9625a5991bc8cb724c21dd6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-supporting-credential"></a>Como criar uma credencial de suporte
É possível ter um esquema de segurança personalizado que requer mais de uma credencial. Por exemplo, um serviço pode demandar do cliente não apenas um nome de usuário e senha, mas também uma credencial que comprove o cliente é com mais de 18. A credencial de segundo é um *suporte credencial*. Este tópico explica como implementar essas credenciais em um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] cliente.  
  
> [!NOTE]
>  A especificação para dar suporte a credenciais faz parte da especificação WS-SecurityPolicy. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Especificações de segurança de serviços web](http://go.microsoft.com/fwlink/?LinkId=88537).  
  
## <a name="supporting-tokens"></a>Tokens com suporte  
 Em suma, quando você usa segurança de mensagem, um *credencial primário* sempre é usado para proteger a mensagem (por exemplo, um certificado x. 509 ou um tíquete Kerberos).  
  
 Conforme definido pela especificação, usa uma associação de segurança *tokens* para proteger a troca de mensagens. Um *token* é uma representação de uma credencial de segurança.  
  
 A associação de segurança usa um token primário identificado na política de associação de segurança para criar uma assinatura. Esta assinatura é conhecida como o *assinatura da mensagem*.  
  
 Tokens adicionais podem ser especificados para aumentar as declarações fornecidas pelo símbolo associado com a assinatura da mensagem.  
  
## <a name="endorsing-signing-and-encrypting"></a>Endossando, assinatura e criptografia  
 Uma credencial de suporte resulta em uma *token de suporte* transmitidos dentro a mensagem. A especificação WS-SecurityPolicy define quatro maneiras para anexar um token de suporte para a mensagem, conforme descrito na tabela a seguir.  
  
|Finalidade|Descrição|  
|-------------|-----------------|  
|Assinado|O token de suporte está incluído no cabeçalho de segurança e é assinado pela assinatura de mensagem.|  
|Endossando|Um *um token* assina a assinatura da mensagem.|  
|Endosso e não assinados|Assinado, endossando tokens de entrada todo o `ds:Signature` elemento próprios produzido da assinatura da mensagem e são assinados por essa assinatura de mensagem; ou seja, ambos os tokens (o token usado para a assinatura da mensagem e o token de endosso assinado) entrar uns aos outros.|  
|Criptografia e não assinados|Tokens de suporte assinados e criptografados são assinados para dar suporte a tokens que também são criptografadas quando elas aparecerem no `wsse:SecurityHeader`.|  
  
## <a name="programming-supporting-credentials"></a>Credenciais de programação com suporte  
 Para criar um serviço que usa tokens de suporte, você deve criar um [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md). ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Como: criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)  
  
 A primeira etapa ao criar uma associação personalizada é criar um elemento de associação de segurança, que pode ser um dos três tipos:  
  
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
  
-   *Ponto de extremidade de dar suporte a tokens* oferece suporte a todas as operações de um ponto de extremidade. Ou seja, a credencial que representa o token de suporte pode ser usada sempre que qualquer operação de ponto de extremidade é invocadas.  
  
-   *Operação de dar suporte a tokens* dar suporte a apenas uma operação de ponto de extremidade específico.  
  
 Conforme indicado pelos nomes de propriedade, as credenciais de suporte pode ser obrigatório ou opcional. Ou seja, se a credencial de suporte será usada se estiver presente, embora ele não é necessário, mas a autenticação não falharão se não estiver presente.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a>Para criar uma associação personalizada que inclui as credenciais de suporte  
  
1.  Crie um elemento de associação de segurança. O exemplo a seguir cria um <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> com o `UserNameForCertificate` modo de autenticação. Use o método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A>.  
  
2.  Adicione o parâmetro de suporte para a coleção de tipos retornados pela propriedade apropriada (`Endorsing`, `Signed`, `SignedEncrypted`, ou `SignedEndorsed`). Os tipos no <xref:System.ServiceModel.Security.Tokens> namespace incluem tipos de uso geral, como o <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir cria uma instância do <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> e adiciona uma instância do <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> a propriedade Endorsing retornada da classe à coleção.  
  
### <a name="code"></a>Código  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Como criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
