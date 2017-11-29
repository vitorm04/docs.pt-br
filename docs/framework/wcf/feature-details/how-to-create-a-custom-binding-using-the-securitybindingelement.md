---
title: "Como criar uma associação personalizada utilizando o SecurityBindingElement"
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
helpviewer_keywords: security [WCF], creating custom bindings
ms.assetid: 203a9f9e-3a73-427c-87aa-721c56265b29
caps.latest.revision: "19"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 0042ae642d8e3a5936c316921b2f9377a0eac17a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-binding-using-the-securitybindingelement"></a>Como criar uma associação personalizada utilizando o SecurityBindingElement
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]inclui várias associações fornecidas pelo sistema que podem ser configuradas, mas não fornecem total flexibilidade ao configurar a segurança todas as opções que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oferece suporte. Este tópico demonstra como criar uma associação personalizada diretamente de elementos de associação individuais e destaca algumas das configurações de segurança que podem ser especificadas ao criar essa associação. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Criando associações personalizadas, consulte [estendendo associações](../../../../docs/framework/wcf/extending/extending-bindings.md).  
  
> [!WARNING]
>  <xref:System.ServiceModel.Channels.SecurityBindingElement>não oferece suporte a <xref:System.ServiceModel.Channels.IDuplexSessionChannel> forma, o que é o uso de forma de canal padrão por TCP de canal de transporte quando <xref:System.ServiceModel.TransferMode> é definido como <xref:System.ServiceModel.TransferMode.Buffered>. Você deve definir <xref:System.ServiceModel.TransferMode> para <xref:System.ServiceModel.TransferMode.Streamed> para usar <xref:System.ServiceModel.Channels.SecurityBindingElement> neste cenário.  
  
## <a name="creating-a-custom-binding"></a>Criando uma associação personalizada  
 Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] todas as associações são compostas de *elementos de associação*. Cada elemento de associação derivado de <xref:System.ServiceModel.Channels.BindingElement> classe. Para as associações padrão fornecido pelo sistema, os elementos de associação criados e configurados para você, embora você pode personalizar algumas das configurações de propriedade.  
  
 Por outro lado, para criar uma associação personalizada, elementos de associação são criados e configurados e um <xref:System.ServiceModel.Channels.CustomBinding> é criado a partir de elementos de associação.  
  
 Para fazer isso, você deve adicionar os elementos de associação individuais em uma coleção representada por uma instância do <xref:System.ServiceModel.Channels.BindingElementCollection> classe e, em seguida, defina o `Elements` propriedade o `CustomBinding` igual a esse objeto. Você deve adicionar os elementos de associação na seguinte ordem: fluxo de transações, sessão confiável, segurança, Duplex compostos, unidirecional, segurança de fluxo, codificação de mensagem e transporte. Observe que nem todos os elementos de associação listados são necessários em cada associação.  
  
## <a name="securitybindingelement"></a>SecurityBindingElement  
 Três elementos de associação se relacionam com segurança em nível de mensagem, que derivam de <xref:System.ServiceModel.Channels.SecurityBindingElement> classe. Os três são <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, e <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. O <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> é usado para fornecer a segurança de modo misto. Os dois elementos são usados quando a camada de mensagem fornece segurança.  
  
 Classes adicionais são usadas quando a segurança em nível de transporte é fornecida:  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
## <a name="required-binding-elements"></a>Necessário de elementos de associação  
 Há um grande número de elementos de associação possíveis que podem ser combinadas em uma associação. Nem todas essas combinações são válidas. Esta seção descreve os elementos necessários que devem estar presentes em uma associação de segurança.  
  
 Associações de segurança válido dependem de muitos fatores, incluindo o seguinte:  
  
-   Modo de segurança.  
  
-   Protocolo de transporte.  
  
-   O padrão de troca mensagens (MEPS) especificado no contrato.  
  
 A tabela a seguir mostra as configurações de pilha do elemento de associação válida para cada combinação de fatores anteriores. Observe que esses são os requisitos mínimos. Você pode adicionar elementos de associação adicionais para a associação, como elementos de associações, elementos de associação de transação e outros elementos de associação de codificação de mensagem.  
  
|Modo de segurança|Transporte|Contrato padrão de troca de mensagem|Contrato padrão de troca de mensagem|Contrato padrão de troca de mensagem|  
|-------------------|---------------|---------------------------------------|---------------------------------------|---------------------------------------|  
|||`Datagram`|`Request Reply`|`Duplex`|  
|Transporte|HTTPS||||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP||||  
|||OneWayBindingElement|||  
|||SSL ou StreamSecurityBindingElement do Windows|SSL ou StreamSecurityBindingElement do Windows|SSL ou StreamSecurityBindingElement do Windows|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|Mensagem|http|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement (modo de autenticação = SecureConversation)|  
|||||CompositeDuplexBindingElement|  
|||OneWayBindingElement||OneWayBindingElement|  
|||HttpTransportBindingElement|HttpTransportBindingElement|HttpTransportBindingElement|  
||TCP|SecurityBindingElement|SecurityBindingElement|SymmetricSecurityBindingElement (modo de autenticação = SecureConversation)|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|Misto (transporte com credenciais de mensagem)|HTTPS|TransportSecurityBindingElement|TransportSecurityBindingElement||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP|TransportSecurityBindingElement|SymmetricSecurityBindingElement (modo de autenticação = SecureConversation)|SymmetricSecurityBindingElement (modo de autenticação = SecureConversation)|  
|||OneWayBindingElement|||  
|||SSL ou StreamSecurityBindingElement do Windows|SSL ou StreamSecurityBindingElement do Windows|SSL ou StreamSecurityBindingElement do Windows|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
  
 Observe que há muitas definições configuráveis no SecurityBindingElements. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Modos de autenticação SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Sessões seguras e conversas seguras](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md).  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-create-a-custom-binding-that-uses-a-symmetricsecuritybindingelement"></a>Para criar uma associação personalizada que usa um SymmetricSecurityBindingElement  
  
1.  Criar uma instância do <xref:System.ServiceModel.Channels.BindingElementCollection> classe com o nome `outputBec`.  
  
2.  Chame o método estático `M:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement(true)`, que retorna uma instância do <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> classe.  
  
3.  Adicionar o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> à coleção (`outputBec`) chamando o `Add` método o <xref:System.Collections.ObjectModel.Collection%601> de <xref:System.ServiceModel.Channels.BindingElement> classe.  
  
4.  Criar uma instância do <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> classe e adicione-o à coleção (`outputBec`). Especifica a codificação usada pela associação.  
  
5.  Criar um <xref:System.ServiceModel.Channels.HttpTransportBindingElement> e adicioná-lo à coleção (`outputBec`). Especifica que a associação usa o transporte HTTP.  
  
6.  Criar uma nova associação personalizada, criando uma instância do <xref:System.ServiceModel.Channels.CustomBinding> classe e passando a coleção `outputBec` para o construtor.  
  
7.  A associação personalizada resultante compartilha muitas das mesmas características como o padrão <xref:System.ServiceModel.WSHttpBinding>. Especifica as credenciais do Windows e a segurança em nível de mensagem, mas desabilita sessões seguras, requer que a credencial de serviço seja especificada fora de banda e não criptografa assinaturas. O último pode ser controlado apenas definindo o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A> propriedade, como mostrado na etapa 4. Os outros dois podem ser controlados usando configurações de associação padrão.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir fornece uma função completa para criar uma associação personalizada que usa um <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
### <a name="code"></a>Código  
 [!code-csharp[c_CustomBinding#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#20)]
 [!code-vb[c_CustomBinding#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombinding/vb/source.vb#20)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
 <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Estendendo associações](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md) (Associações fornecidas pelo sistema)
