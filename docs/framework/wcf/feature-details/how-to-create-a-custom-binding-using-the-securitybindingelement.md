---
title: 'Como: Criar uma associação personalizada utilizando o SecurityBindingElement'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating custom bindings
ms.assetid: 203a9f9e-3a73-427c-87aa-721c56265b29
ms.openlocfilehash: 2c2aa5703e31b2529e0b98d909a763b8b4b23035
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576144"
---
# <a name="how-to-create-a-custom-binding-using-the-securitybindingelement"></a>Como: Criar uma associação personalizada utilizando o SecurityBindingElement
Windows Communication Foundation (WCF) inclui várias associações fornecidas pelo sistema que podem ser configuradas, mas não fornecem flexibilidade total durante a configuração de todas as opções de segurança que o WCF oferece suporte. Este tópico demonstra como criar uma ligação personalizada diretamente de elementos de ligação individuais e destaca algumas das configurações de segurança que podem ser especificadas ao criar essa associação. Para obter mais informações sobre como criar associações personalizadas, consulte [estendendo associações](../../../../docs/framework/wcf/extending/extending-bindings.md).  
  
> [!WARNING]
>  <xref:System.ServiceModel.Channels.SecurityBindingElement> não oferece suporte a <xref:System.ServiceModel.Channels.IDuplexSessionChannel> forma, o que é o uso de forma de canal padrão por TCP de canal de transporte quando <xref:System.ServiceModel.TransferMode> é definido como <xref:System.ServiceModel.TransferMode.Buffered>. Você deve definir <xref:System.ServiceModel.TransferMode> à <xref:System.ServiceModel.TransferMode.Streamed> para usar <xref:System.ServiceModel.Channels.SecurityBindingElement> nesse cenário.  
  
## <a name="creating-a-custom-binding"></a>Criando uma associação personalizada  
 No WCF todas as associações são compostas de *elementos de associação*. Cada elemento de associação deriva o <xref:System.ServiceModel.Channels.BindingElement> classe. Para associações fornecidas pelo sistema padrão, os elementos de associação criados e configurados para você, embora você pode personalizar algumas das configurações de propriedade.  
  
 Por outro lado, para criar uma ligação personalizada, elementos de associação são criados e configurados e um <xref:System.ServiceModel.Channels.CustomBinding> é criada a partir de elementos de associação.  
  
 Para fazer isso, você deve adicionar os elementos de associação individuais em uma coleção representada por uma instância das <xref:System.ServiceModel.Channels.BindingElementCollection> de classe e, em seguida, defina o `Elements` propriedade do `CustomBinding` igual a esse objeto. Você deve adicionar os elementos de associação na seguinte ordem: Fluxo de transações, sessão confiável, segurança, dúplex de composição, unidirecional, segurança de Stream, codificação de mensagem e transporte. Observe que nem todos os elementos de associação listados são necessárias em todas as associações.  
  
## <a name="securitybindingelement"></a>SecurityBindingElement  
 Três elementos de ligação se relacionam com segurança em nível de mensagem, que derivam de <xref:System.ServiceModel.Channels.SecurityBindingElement> classe. Os três são <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, e <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. O <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> é usado para fornecer segurança de modo misto. Os dois elementos são usados quando a camada de mensagem fornece segurança.  
  
 Classes adicionais são usadas quando a segurança em nível de transporte é fornecida:  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
## <a name="required-binding-elements"></a>Necessário de elementos de associação  
 Há um grande número de elementos de associação possíveis que podem ser combinadas em uma associação. Nem todas essas combinações são válidas. Esta seção descreve os elementos necessários que devem estar presentes em uma associação de segurança.  
  
 Associações de segurança válido dependem de muitos fatores, incluindo o seguinte:  
  
-   Modo de segurança.  
  
-   Protocolo de transporte.  
  
-   O padrão de troca mensagens (MEP) especificado no contrato.  
  
 A tabela a seguir mostra as configurações de pilha do elemento de associação válida para cada combinação de fatores anteriores. Observe que esses são os requisitos mínimos. Você pode adicionar elementos de ligação adicionais para associação, como elementos de associação, elementos de associação da transação e outros elementos de associação de codificação de mensagem.  
  
|Modo de segurança|Transporte|Contrato padrão de troca de mensagem|Contrato padrão de troca de mensagem|Contrato padrão de troca de mensagem|  
|-------------------|---------------|---------------------------------------|---------------------------------------|---------------------------------------|  
|||`Datagram`|`Request Reply`|`Duplex`|  
|Transporte|Https||||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP||||  
|||OneWayBindingElement|||  
|||SSL ou StreamSecurityBindingElement do Windows|SSL ou StreamSecurityBindingElement do Windows|SSL ou StreamSecurityBindingElement do Windows|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|Mensagem|Http|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement (modo de autenticação = SecureConversation)|  
|||||CompositeDuplexBindingElement|  
|||OneWayBindingElement||OneWayBindingElement|  
|||HttpTransportBindingElement|HttpTransportBindingElement|HttpTransportBindingElement|  
||Tcp|SecurityBindingElement|SecurityBindingElement|SymmetricSecurityBindingElement (modo de autenticação = SecureConversation)|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|Misto (transporte com as credenciais de mensagem)|Https|TransportSecurityBindingElement|TransportSecurityBindingElement||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP|TransportSecurityBindingElement|SymmetricSecurityBindingElement (modo de autenticação = SecureConversation)|SymmetricSecurityBindingElement (modo de autenticação = SecureConversation)|  
|||OneWayBindingElement|||  
|||SSL ou StreamSecurityBindingElement do Windows|SSL ou StreamSecurityBindingElement do Windows|SSL ou StreamSecurityBindingElement do Windows|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
  
 Observe que há muitas definições configuráveis no SecurityBindingElements. Para obter mais informações, consulte [modos de autenticação de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 Para obter mais informações, consulte [conversas segura e proteger sessões](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md).  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-create-a-custom-binding-that-uses-a-symmetricsecuritybindingelement"></a>Para criar uma associação personalizada que usa um SymmetricSecurityBindingElement  
  
1.  Criar uma instância das <xref:System.ServiceModel.Channels.BindingElementCollection> classe com o nome `outputBec`.  
  
2.  Chame o método estático `M:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement(true)`, que retorna uma instância da <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> classe.  
  
3.  Adicione a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> à coleção (`outputBec`) chamando o `Add` método da <xref:System.Collections.ObjectModel.Collection%601> de <xref:System.ServiceModel.Channels.BindingElement> classe.  
  
4.  Criar uma instância das <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> de classe e adicione-o à coleção (`outputBec`). Especifica a codificação usada pela associação.  
  
5.  Criar uma <xref:System.ServiceModel.Channels.HttpTransportBindingElement> e adicione-o à coleção (`outputBec`). Isso especifica que a associação usa o transporte HTTP.  
  
6.  Criar uma nova associação personalizada, criando uma instância das <xref:System.ServiceModel.Channels.CustomBinding> classe e passando a coleção `outputBec` para o construtor.  
  
7.  A associação personalizada resultante compartilha muitas das mesmas características como o padrão <xref:System.ServiceModel.WSHttpBinding>. Especifica as credenciais do Windows e a segurança em nível de mensagem, mas desabilita sessões seguras, requer que a credencial de serviço seja especificada fora de banda e não criptografa assinaturas. O último pode ser controlado apenas definindo a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A> propriedade conforme mostrado na etapa 4. Os outros dois podem ser controlados usando as configurações em associação padrão.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir fornece uma função completa para criar uma associação personalizada que usa um <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
### <a name="code"></a>Código  
 [!code-csharp[c_CustomBinding#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#20)]
 [!code-vb[c_CustomBinding#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombinding/vb/source.vb#20)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Estendendo associações](../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Associações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md)
